from golang:1.15.6 as builder

ADD . /go/src/github.com/{{ cookiecutter.github_username }}/{{ cookiecutter.app_name }}
WORKDIR . /go/src/github.com/{{ cookiecutter.github_username }}/{{ cookiecutter.app_name }}

RUN make build-alpine

FROM alpine:latest

ARG GIT_COMMIT
ARG VERSION
LABEL GIT_COMMIT=$GIT_COMMIT
LABEL VERSION=$VERSION

RUN apk --no-cache add ca-certificates
WORKDIR /root/
COPY --from=builder /go/src/github.com/{{ cookiecutter.github_username }}/{{ cookiecutter.app_name }}/bin/{{ cookiecutter.app_name }} .
CMD ["./{{ cookiecutter.app_name }}"]
