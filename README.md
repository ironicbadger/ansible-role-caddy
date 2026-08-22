# ansible-role-caddy

Install and configure Caddy reverse proxy programatically. Tested on Ubuntu 24.04.

## Variables
TLS providers
```yaml
caddy_tls_providers:
  - provider: cloudflare
    challenge_type: dns
    provider_api_token: "1234567890abcdefg"
    resolver_ip: 1.1.1.1
```

Endpoints
```yaml
caddy_endpoints:
  - friendly_name: app1
    fqdn: app1.exaple.com
    upstream: "localhost:8081"
    tls_insecure: false
    tls_provider: cloudflare
  - friendly_name: Wildcard *.local.example.com
    fqdn: '*.local.exaple.com'
    tls_provider: cloudflare
    wildcard_endpoints:
      - friendly_name: app2
        fqdn: app2.local.example.com
        upstream: "localhost:8082"
        tls_insecure: false
```

Geo-blocking
```yaml
caddy_geoblock:
  db_path:
    - /var/lib/caddy/GeoLite2-Country.mmdb
  allow_countries:
    - US
    - CA
  deny_asn:
    - 13335
  blocked_status: 403
  blocked_message: "Access denied"
```

The geoblock configuration is applied to every endpoint. Options that accept
multiple values, such as `db_path`, are YAML lists and produce one directive
per value.

