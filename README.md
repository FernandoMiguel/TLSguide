# TLSguide
SSL/TLS Workshop/Reference Guide






## Reference URLs
### mozilla vhost generator
- https://mozilla.github.io/server-side-tls/ssl-config-generator/?server=nginx-1.10.1&openssl=1.0.1e&hsts=yes&profile=modern

### Let's Encrypt
- https://letsencrypt.org/
- https://letsencrypt.org/docs/
- https://letsencrypt.org/docs/client-options/
- https://letsencrypt.org/docs/rate-limits/
#### LE Production API
- The main limit is Certificates per Registered Domain (20 per week). 
- limit of 100 Names per Certificate (SAN)
- a maximum of 500 Accounts per IP Address per 3 hours
#### LE Staging API
- The Certificates per Registered Domain limit is 30,000 per week.
- The Duplicate Certificate limit is 30,000 per week.
- The Failed Validations limit will be 60 per hour.

### CLoudflare
- https://www.cloudflare.com

### AWS
- https://aws.amazon.com/certificate-manager/faqs/
- https://aws.amazon.com/cloudfront/
- https://aws.amazon.com/elasticloadbalancing/applicationloadbalancer/

### acme.sh
- https://acme.sh
- https://github.com/Neilpang/acme.sh
- https://github.com/Neilpang/acme.sh/wiki
- https://github.com/Neilpang/acme.sh/blob/master/dnsapi/README.md


### monitors
- https://crt.sh/
- https://developers.facebook.com/tools/ct/
- https://letsmonitor.org/
- https://www.ssllabs.com/ssltest/

### Scott Helme
https://scotthelme.co.uk/
https://report-uri.io/
https://securityheaders.io/

#### brew
https://github.com/nabla-c0d3/sslyze
https://testssl.sh/





