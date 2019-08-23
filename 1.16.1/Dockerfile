FROM nginx:1.16.1

RUN apt update &&\
    DEBIAN_FRONTEND=noninteractive apt install -y nginx-extras --no-install-recommends &&\
    apt autoremove -y && apt clean && rm -rf /var/lib/apt/lists* /tmp/* /var/tmp/*

RUN sed -i '/location \/ {/i\client_max_body_size 1G;' /etc/nginx/conf.d/default.conf &&\
    sed -i '/location \/ {/a\dav_methods PUT DELETE MKCOL COPY MOVE;' /etc/nginx/conf.d/default.conf

RUN chown -R www-data:www-data /usr/share/nginx/html