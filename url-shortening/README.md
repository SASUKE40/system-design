# URL Shortening service

## Capacity Estimation and Constrains

- Read-write ratio​
  - 100:1
- Write
  - 100m URLs/month
  - QPS
    - 100m / (30 * 24 * 3600) = ~40 URLs/s
- Read
  - QPS
    - 40 * 100 = 4k URLs/s
- Storage
  - 100m * 5 * 12 = 6b
  - 6b * 500bytes = 3TB
- Bandwidth
  - 40 * 500 bytes = 20k/s
  - 4k * 500 bytes = 2M/s
- Memory
  - 20-80 rule
  - 4k * 3600 * 24 = ~0.4billion
  - 0.2 * 0.4b * 500 bytes = ~40G

| type                | estimation |
| ------------------- | ---------- |
| New URLs            | 40/s       |
| URL redirections    | 4k/s       |
| Incoming data       | 20k/s      |
| Outgoing data       | 2m/s       |
| Storage for 5 years | 3T         |
| Memory for cache    | 40G        |

## System APIs

createURL(api_dev_key, original_url, custom_alias=null, user_name=null,expire_data=null): url_key

deleteURL(api_dev_key, url_key): boolean

## Basic Design

### Encoding

SHA256 + Base62

