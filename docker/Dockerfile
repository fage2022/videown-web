FROM node:16-alpine3.15 as builder

WORKDIR /apps
COPY . .

RUN yarn install && yarn run build

# ===========================================================
FROM nginx:stable-alpine

WORKDIR /usr/share/nginx/html

RUN apk add --no-cache bash

COPY --from=builder /apps/build /usr/share/nginx/html

EXPOSE 80

CMD ["/bin/bash", "-c", "nginx -g \"daemon off;\""]
