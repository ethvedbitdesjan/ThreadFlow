FROM node:20-alpine AS base

WORKDIR /app


COPY package.json package-lock.json* ./


FROM base AS development
RUN npm install

CMD ["npm", "run", "dev", "--", "--hostname", "0.0.0.0"]


FROM base AS production
RUN npm ci
COPY . .
RUN npm run build

RUN npm prune --production
CMD ["node", "server.js"]