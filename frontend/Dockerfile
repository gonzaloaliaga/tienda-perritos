# ========== ETAPA 1: Preparación ==========
FROM alpine AS builder
WORKDIR /app
COPY . .
RUN rm -f Dockerfile nginx.conf.template

# ========== ETAPA 2: Producción ==========
FROM nginxinc/nginx-unprivileged:alpine
COPY --from=builder /app /usr/share/nginx/html
# Copiamos el template de configuración del proxy
COPY nginx.conf.template /etc/nginx/templates/default.conf.template
EXPOSE 8080
CMD ["nginx", "-g", "daemon off;"]