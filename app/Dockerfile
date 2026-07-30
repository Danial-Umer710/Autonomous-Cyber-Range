# Using an older Nginx image so Trivy can find real vulnerabilities
FROM nginx:1.14-alpine

WORKDIR /usr/share/nginx/html
COPY . .

EXPOSE 80
CMD ["nginx", "-g", "daemon off;"]
