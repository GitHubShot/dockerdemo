############################################################
# Dockerfile to build Nginx Installed Containers
# Based on Ubuntu
############################################################

# Set the base image to Ubuntu
FROM ubuntu

# File Author / Maintainer
MAINTAINER mark@mauerwerk.biz

# Add Metadata (as key/value pairs)
LABEL com.t-systems.provider="architecture" description="nginx conatiner acting as reverse proxy"


# Install Nginx
# RUN executes any commands in a new layer on top of the current image 
# and commit the results. 
# The resulting committed image will be used for the next step 

# Update the repository
RUN apt-get update

# Install necessary tools
RUN apt-get install -y nano wget dialog net-tools

# Download and Install Nginx
RUN apt-get install -y nginx  

# Remove the default Nginx configuration file
RUN rm -v /etc/nginx/nginx.conf

# Copy a configuration file from the current directory
ADD nginx.conf /etc/nginx/

# mount host volume for static web content
#VOLUME ["./html:/usr/share/nginx/html:ro"]

#Logging forward request and error logs to docker log collector
RUN ln -sf /dev/stdout /var/log/nginx/access.log
RUN ln -sf /dev/stderr /var/log/nginx/error.log

# Expose ports
# ontainer listens on the specified network ports at runtime
# but does not make ports accessible for the host 
# --> use -P flag to publish all the exposed ports
EXPOSE 80

# provide defaults for an executing container.
# there is  only one CMD per docker container
# only the 
CMD ["nginx", "-g", "daemon off;"]