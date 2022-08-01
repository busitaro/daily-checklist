# package
FROM node:16-alpine3.15 as package

ARG SRC_DIR ./back

WORKDIR /app

COPY ${SRC_DIR} .

RUN yarn install --non-interactive --frozen-lockfile

# run
FROM node:16-alpine3.15 as run

WORKDIR /app

ENV TINI_VERSION v0.19.0
ADD https://github.com/krallin/tini/releases/download/${TINI_VERSION}/tini-static /tini
RUN chmod +x /tini

RUN adduser -D app

COPY --chown=app:app --from=package /app/node_modules /app/node_modules
RUN chown -R app:app /app

USER app
EXPOSE 3000
ENTRYPOINT ["/tini", "--"]
