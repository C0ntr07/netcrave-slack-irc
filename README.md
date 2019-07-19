# Netcrave Communications SlackIRC bridge 

This bot uses ZNC as a front-end client to connect to freenode which removes the responsibility 
of TLS connection setup and nickserv authentication from the bot. See `config.json.example` for
more details.

## Building 

`docker build -t netcrave/slack-irc -t netcrave/slack-irc:latest .`

## Obtaining a legacy slack token 
[https://api.slack.com/custom-integrations/legacy-tokens]

## Running 

`docker run --restart=always -it -v /home/erratic/slack_irc:/config netcrave/slack-irc`

