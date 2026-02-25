# =============================================================================
# Dockerfile — Static HTML App served by NGINX
# Base: nginx:alpine  (tiny ~23 MB image)
# =============================================================================

FROM nginx:alpine

# Remove the default NGINX welcome page
RUN rm -rf /usr/share/nginx/html/*

# Copy our HTML app into the NGINX web root
COPY index.html /usr/share/nginx/html/index.html

# Copy custom NGINX config (optional, falls back to default if not present)
COPY nginx.conf /etc/nginx/conf.d/default.conf

# Expose port 80
EXPOSE 80

# Health check — ensure NGINX is serving the app
HEALTHCHECK --interval=30s --timeout=5s --start-period=5s --retries=3 \
  CMD wget -qO- http://localhost/ || exit 1

# Default NGINX command (already set in base image, explicit for clarity)
CMD ["nginx", "-g", "daemon off;"]
