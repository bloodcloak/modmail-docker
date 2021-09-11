FROM python:3.7-alpine
ENV USING_DOCKER yes

RUN adduser -D mailbot
WORKDIR /home/mailbot
COPY . /home/mailbot

RUN  export PIP_NO_CACHE_DIR=false \
    && apk update \
    && apk add --update --no-cache --virtual .build-deps alpine-sdk \
    && pip install pipenv 
    
COPY --chown=mailbot:mailbot . .
USER mailbot

RUN pipenv install --deploy --ignore-pipfile

CMD ["pipenv", "run", "bot"]