FROM linuxserver/code-server:latest

USER root

RUN \
  apt-get update -y && \
  apt-get upgrade -y

RUN \
  RELEASE_INFO=$(curl -s https://nodejs.org/dist/index.json) && \
  NODEJS=$(echo "$RELEASE_INFO" | jq -r '.[] | select(.lts != null) | .version' | head -n 1 | sed 's/^v//' | awk -F. '{print $1}') && \
  curl -sL https://deb.nodesource.com/setup_${NODEJS}.x | bash - && \
  apt-get install -y nodejs

EXPOSE 5173
