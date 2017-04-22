# TLS guide
SSL/TLS Workshop/Reference Guide


## Knowledge Base

###  acme protocol
- http://ietf-wg-acme.github.io/acme/


## Reference URLs


### mozilla vhost generator
- https://mozilla.github.io/server-side-tls/ssl-config-generator/?profile=modern


### Let's Encrypt
- https://letsencrypt.org/
- https://letsencrypt.org/docs/


### CLoudflare
- https://www.cloudflare.com
- https://github.com/cloudflare/sslconfig/blob/master/conf


### AWS
- https://aws.amazon.com/certificate-manager/faqs/
- https://aws.amazon.com/cloudfront/
- https://aws.amazon.com/elasticloadbalancing/applicationloadbalancer/


### monitors
- https://crt.sh/
- https://developers.facebook.com/tools/ct/
- https://letsmonitor.org/
- https://www.ssllabs.com/ssltest/


#### brew
- https://github.com/nabla-c0d3/sslyze
- https://testssl.sh/


### Scott Helme
- https://scotthelme.co.uk/
- https://report-uri.io/
- https://securityheaders.io/


## Let's Encrypt

## ACME protocol challenges options

- standalone
- webroot
- apache
- nginx
- manual (http-01, DNS-01)


### API rate limits
- https://letsencrypt.org/docs/rate-limits/
#### LE Production API
- The main limit is Certificates per Registered Domain (20 per week). 
- A limit of 100 Names per Certificate (SAN)
- A maximum of 500 Accounts per IP Address per 3 hours
#### LE Staging API
- The Certificates per Registered Domain limit is 30,000 per week.
- The Duplicate Certificate limit is 30,000 per week.
- The Failed Validations limit will be 60 per hour.


### LE clients
- https://letsencrypt.org/docs/client-options/

#### Certbot
- https://certbot.eff.org/about/

#### acme.sh
- https://acme.sh
- https://github.com/Neilpang/acme.sh
- https://github.com/Neilpang/acme.sh/wiki

### DNS-01
- 
- https://github.com/Neilpang/acme.sh/blob/master/dnsapi/README.md


## Auxiliar 
- https://cloud-images.ubuntu.com/locator/ec2/
- https://brew.sh/


## Contributing

1. Fork it!
2. Create your feature branch: `git checkout -b my-new-feature`
3. Commit your changes: `git commit -am 'Add some feature'`
4. Push to the branch: `git push origin my-new-feature`
5. Submit a pull request :D


## License

[The Unlicense](LICENSE)
