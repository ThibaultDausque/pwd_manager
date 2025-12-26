FROM debian:bookworm-slim AS build

RUN apt update -y && apt install -y
WORKDIR /app
COPY . .
RUN apt install nodejs npm -y
RUN wget -qO- https://get.pnpm.io/install.sh | ENV="$HOME/.shrc" SHELL="$(which sh)" sh -
FROM debian:bookworm-slim

COPY --from=build /app/* .

EXPOSE 3000

CMD ["pnpm", "dev"]
