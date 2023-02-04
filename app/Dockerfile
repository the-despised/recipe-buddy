FROM node:16-alpine as builder

COPY . .

RUN yarn install --freeze-lockfile

RUN yarn run build

FROM nginx as Deploy

COPY nginx/default.conf /etc/nginx/conf.d/default.conf

COPY --from=builder /dist ./usr/share/nginx/html

EXPOSE 80
