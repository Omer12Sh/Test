# Basic Nginx App

This repository contains a minimal Nginx setup that serves a static `index.html` page. The page is a simple newsletter for **Zutadeli Dairy**.

## Usage

Build the Docker image and run it with the following commands:

```bash
# Build the Docker image
docker build -t basic-nginx .

# Run the container
docker run -p 8080:80 basic-nginx
```

Access the application by navigating to `http://localhost:8080` in your web browser.

## Dynamic IP and DNS

If your server obtains its IP address dynamically, you can route a domain like `zutadeli.com` using a dynamic DNS provider. Configure a service such as DuckDNS or DynDNS to update the DNS record whenever the IP changes.

Example cron job using DuckDNS:

```bash
*/5 * * * * curl -fsS "https://www.duckdns.org/update?domains=zutadeli&token=<token>&ip="
```

## Deployment Best Practices

- Keep the Docker image small by using `nginx:alpine`.
- Store your newsletter content separately from the container image so you can update it without rebuilding.
- Use a reverse proxy or load balancer in front of Nginx if you expect high traffic.
- Terminate TLS with a certificate management tool (e.g. Let's Encrypt) to serve the newsletter over HTTPS.
