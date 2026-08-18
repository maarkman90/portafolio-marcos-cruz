FROM nginx:alpine

# Elimina la configuración default de nginx
RUN rm -f /etc/nginx/conf.d/default.conf

# Copia nuestra configuración personalizada
COPY deploy/nginx.conf /etc/nginx/conf.d/default.conf

# Copia el portafolio como index.html
COPY portafolio_marcos_cruz.html /usr/share/nginx/html/index.html

# Copia el CV
COPY cv_marcos_profesional.html /usr/share/nginx/html/cv_marcos_profesional.html

# Copia robots.txt para SEO
COPY robots.txt /usr/share/nginx/html/robots.txt

# Copia los assets (imágenes, logo, etc.)
COPY assets/ /usr/share/nginx/html/assets/

# Copia las demos interactivas (ej. RAG legal)
COPY demos/ /usr/share/nginx/html/demos/

EXPOSE 80

HEALTHCHECK --interval=30s --timeout=3s --retries=3 \
  CMD wget -q --spider http://127.0.0.1/ || exit 1

CMD ["nginx", "-g", "daemon off;"]
