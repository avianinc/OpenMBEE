# Base image 
FROM ubuntu:20.04

# Define arguments
ARG VE_VERSION=4.0.2 
# # works with 2022 and mdk6+
#ARG VE_VERSION=5.0.0-beta 

# Install Nginx and required tools
RUN apt-get update && \
    apt-get install -y nginx wget unzip nano && \
    rm -rf /var/lib/apt/lists/* 

# Remove the default Nginx configuration file
RUN rm /etc/nginx/sites-enabled/default

# Copy the custom Nginx config
COPY nginx.conf /etc/nginx/sites-available/

# Link the config file to sites-enabled
RUN ln -s /etc/nginx/sites-available/nginx.conf /etc/nginx/sites-enabled/

# Download and unzip the file to /var/www/html
RUN wget https://github.com/Open-MBEE/ve/releases/download/${VE_VERSION}/${VE_VERSION}.zip && \
    unzip ${VE_VERSION}.zip -d /var/www/html && \
    rm ${VE_VERSION}.zip

RUN sed -i 's|apiUrl: '\''http://localhost:8080'\''|apiUrl: '\''http://54.208.197.217:8080'\''|g' /var/www/html/dist/js/ve-mms.min.b4876f296d0d3d3e.js

# Change the ownership and permissions of the Nginx web directory
RUN chown -R www-data:www-data /var/www/html && \
    chmod -R 755 /var/www/html

# Define default command
CMD ["nginx", "-g", "daemon off;"]

# Expose ports
EXPOSE 80