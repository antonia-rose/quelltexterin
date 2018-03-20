# Deployment
## Build hugo image

1. run `docker build -t hugo -f Dockerfile.hugo`
2. run `docker run hugo`
3. run `docker login` and login to hub.docker.io
4. run `docker tag hugo quelltexterin/hugo:v<$version>`
5. run `docker push quelltexterin/hugo:v<?version>`

Now the hugo image is ready for use.

## Build Deployment Image

1. Update version of hugo image
2. run `docker build -t blog -f Dockerfile.deployment`
3. run `docker run blog`
4. run `docker login` and login to hub.docker.io
5. run `docker tag blog quelltexterin/blog:v<$version>`
6. run `docker push quelltexterin/blog:v<$version>`
7. Update version in sloppy.yml
8. run `sloppy change sloppy.yml`

# Development
If necessary update version of quelltexterin/hugo image.

1. run `docker-compose up`
