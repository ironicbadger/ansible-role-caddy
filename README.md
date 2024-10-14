# ansible-role-caddy

Install and configure Caddy reverse proxy programatically. Tested on Ubuntu 24.04.

## Variables
TLS providers
'''
caddy_tls_providers:
  - provider: cloudflare
    challenge_type: dns
    provider_api_token: "1234567890abcdefg"
    resolver_ip: 1.1.1.1
'''

Endpoints
'''
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
      - friendly_name: Proxmox
        fqdn: proxmox.local.maccan.tech
        upstream: ""
        tls_insecure: false
'''

