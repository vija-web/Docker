FROM almalinux:9
RUN dnf install nginx -y 
RUN rm -rf /usr/share/nginx/html/index.html
ONBUILD COPY index.html /usr/share/nginx/html/

CMD ["nginx" , "-g" , "daemon off;"]

# ONBUILD means who ever using this image they should have the index.html file in the folder 
# We can make users to mandatory to give this option.