FROM debian:bookworm-slim AS build

RUN apt update -y && apt install -y
RUN apt-get install -y python3-full python3-dev python-is-python3 git
RUN apt-get install pip -y
RUN python3 -m venv /opt/venv
ENV PATH="/opt/venv/bin:$PATH"
RUN pip install django
WORKDIR /app
COPY . .

FROM debian:bookworm-slim

COPY --from=build /app/* .
WORKDIR /app

EXPOSE 8000

CMD ["python", "manage.py", "runserver"]
