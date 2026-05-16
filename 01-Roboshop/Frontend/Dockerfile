# Note this is not docker best practise
FROM nginx
RUN rm -rf /usr/share/nginx/html/*
RUN rm -rf /etc/nginx/nginx.conf 
RUN rm -rf /etc/nginx/conf.d/default.conf 
COPY frontend/ /usr/share/nginx/html/
COPY nginx.conf /etc/nginx/nginx.conf

