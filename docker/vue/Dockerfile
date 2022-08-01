# package
FROM node:16-alpine3.15 as package

WORKDIR /app

COPY front/yarn.lock /app/
COPY front/package.json /app/
RUN apk update && \
    yarn install --frozen-lockfile

# run
FROM node:16-alpine3.15 as run

WORKDIR /app

ENV TINI_VERSION v0.19.0
ADD https://github.com/krallin/tini/releases/download/${TINI_VERSION}/tini-static /tini
RUN chmod +x /tini

RUN adduser -D app

COPY --chown=app:app --from=package /app/node_modules /app/node_modules

USER app
EXPOSE 3000
ENTRYPOINT ["/tini", "--"]

# return chmod package.json etc.
# sudo ln -s ./package.json /package.json
# yarn --cwd / vue-cli-service serve
# npx run serve
