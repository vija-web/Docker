FROM almalinux:9
RUN dnf install nginx -y
RUN rm -rf /usr/share/nginx/html/index.html
CMD ["nginx" , "-g" , "daemon off;"]
COPY index.html /usr/share/nginx/html/

LABEL created=Vijay \
      Author=vijay
EXPOSE 80