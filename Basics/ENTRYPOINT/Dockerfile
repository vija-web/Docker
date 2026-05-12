FROM almalinux:9 

# Here almalinux is the base os image
# CMD ["ping" , "faceboook.com"]

ENTRYPOINT ["ping" , "google.com"]
# We can make container alive with CMD and ENTRYPOINT Instruction , Otherwise container will get stop


# CMD and ENTRYPOINT both functionality same but CMD can override
# But ENTRYPOINT can't be override
# IF we use both CMD and ENTRYPOINT in the dockerfile then CMD value will get append to the ENTRYPOINT and gets error.
# IF need we can use both 
# example
#    FROM almalinux:9
#    CMD ["faceboook.com"]
#    ENTRYPOINT ["ping"]
# we can override the CMD value here 
# docker run -d cmdentry:v1 google.com Then it pings the google.com
