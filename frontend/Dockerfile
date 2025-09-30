# Use a lightweight Nginx image to serve static content
FROM nginx:alpine

# Remove the default Nginx welcome page
RUN rm /usr/share/nginx/html/index.html

# Copy the static files from the frontend directory into the Nginx web root
COPY . /usr/share/nginx/html

# Expose port 80 to the outside world
EXPOSE 80

# The default Nginx entrypoint will start the server automatically
# No CMD is needed.