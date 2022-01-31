FROM nginx

RUN mkdir /app
COPY index.html /app/index.html

RUN sed -i 's/80/8000/' /etc/nginx/conf.d/default.conf \
   && sed -i 's|/usr/share/nginx/html|/app|' /etc/nginx/conf.d/default.conf

RUN touch /var/run/nginx.pid

RUN usermod -u 1001 nginx \
    && groupmod -g 1001 nginx 

RUN chown -R nginx:nginx /app \
   && chmod -R 755 /app \
   && chown -R nginx:nginx /etc/nginx \
   && chown -R nginx:nginx /var/cache/nginx \
   && chown -R nginx:nginx /var/log/nginx \
   && chown -R nginx:nginx /var/run/nginx.pid

USER nginx