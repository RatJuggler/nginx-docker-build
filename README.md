# my-production-docker-build

This is still a work in progress and is my attempt at a unified build process for the various projects I'm running on my Pi farm.

The goal to start with is to build all the images I want by cloning repos and running all the builds with a single command:

    ./build.sh

The script clones only the minimum source code required (no history) and then any building and copying is done in the multi-stage 
docker file. The source code cloned also includes my production Nginx configuration files from [Nginx HTTP server boilerplate configs](https://github.com/RatJuggler/server-configs-nginx/tree/production).

At the moment I'm running this on a single Raspberry PI 3 Model B+, so I'm conserving resources by using a single instance of Nginx 
to serve the static content for two sites and dynamic content from a Node instance.

Note, the site certificates and private keys are bundled with the image so this is not an ideal solution from a security 
perspective. Anyone with access to the generated Docker image can retrieve them. This also makes updating the certificates 
automatically harder as the Docker image must be re-created to include the updates and any running containers then restarted with 
the new image.
