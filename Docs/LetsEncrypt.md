## Let's Encrypt

### ACME protocol challenges options

- https://certbot.eff.org/docs/using.html#getting-certificates-and-choosing-plugins

- standalone


Use standalone mode to obtain a cert if you don’t want to use (or don’t currently have) existing server software.


The standalone plugin does not rely on any other server software running on the machine where you obtain the cert.

- webroot


If you’re running a local webserver for which you have the ability to modify the content being served, and you’d prefer not to stop the webserver during the certificate issuance process, you can use the webroot plugin to obtain a cert


The webroot plugin works by creating a temporary file for each of your requested domains in ${webroot-path}/.well-known/acme-challenge. Then the Let’s Encrypt validation server makes HTTP requests to validate that the DNS for each requested domain resolves to the server running certbot.


Note that to use the webroot plugin, your server must be configured to serve files from hidden directories. If /.well-known is treated specially by your webserver configuration, you might need to modify the configuration to ensure that files inside /.well-known/acme-challenge are served by the webserver.

- apache
- nginx
- manual (http-01, [DNS-01](#dns-01))


If you’d like to obtain a cert running certbot on a machine other than your target webserver or perform the steps for domain validation yourself, you can use the manual plugin.


The manual plugin can use either the http or the dns challenge.


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
When using the dns plugin, LE client will ask you to place a TXT DNS record with specific contents under the domain name consisting of the hostname for which you want a certificate issued, prepended by _acme-challenge.
- https://github.com/Neilpang/acme.sh/tree/master/dnsapi/README.md
