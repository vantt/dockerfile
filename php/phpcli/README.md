# docker-phpcli
docker build -f Dockerfile-7.4 -t devops/phpcli:7.4 .

add this line to your bash_profile file

```
php () {
    tty=
    tty -s && tty=--tty
    docker run \
        $tty \
        --interactive \
        --rm \
        --volume $(pwd):/app \
        --volume $(dirname $SSH_AUTH_SOCK):$(dirname $SSH_AUTH_SOCK) \
        --volume /etc/passwd:/etc/passwd:ro \
        --volume /etc/group:/etc/group:ro \
        --user $(id -u):$(id -g) \
        --env SSH_AUTH_SOCK=$SSH_AUTH_SOCK \
        990863991647.dkr.ecr.us-west-2.amazonaws.com/devops/phpcli:latest "$@"
}
```
