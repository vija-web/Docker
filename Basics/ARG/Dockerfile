ARG VERSION
FROM almalinux:${VERSION:-9}
ARG NAME="vijay" \
    COURSE="docker"
RUN echo "Name : ${NAME} , Course : ${COURSE} , Version : ${VERSION}"
# Here the will come but the variable VERSION value will not print
# The version scope is upto the 2nd line only 
# docker build -t arg:v1 --build-arg VERSION=8 .
