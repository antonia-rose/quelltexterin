# Deployment
## Build hugo image (only if new hugo version is published)

1. run `docker build -t hugo -f Dockerfile.hugo`
2. run `docker run hugo`
3. run `docker login` and login to hub.docker.io
4. run `docker tag hugo quelltexterin/hugo:v<$version>`
5. run `docker push quelltexterin/hugo:v<?version>`

Deployment is automated with Travis. Just create a release (see [Gitflow](https://danielkummer.github.io/git-flow-cheatsheet/) for more information), publish and finish it. Travis will build a new docker image, version is same like release version and notify sloppy about the change.


# Development
If necessary update version of quelltexterin/hugo image.

1. run `docker-compose up`
