# Netcrave Communications SlackIRC bridge 

This bot uses ZNC as a front-end client to connect to freenode which removes the responsibility 
of TLS connection setup and nickserv authentication from the bot. See `config.json.example` for
more details.

## Building 

`docker build -t netcrave/slack-irc -t netcrave/slack-irc:latest .`

## Obtaining a legacy slack token 
[https://api.slack.com/custom-integrations/legacy-tokens]

## Running 

### ZNC 
Check out the znc.conf.example included in this repository. 

#### Freenode / nickserv configuration 

- Register a nickname for your bot using the `GROUP` command. First login with your normal Freenode nick:

```
/msg nickserv identify <pass>
/nick nick_for_bot 
/msg nickserv GROUP
/nick your_normal_nick
```
with that your nick can be authenticated using the same password. To configure ZNC to automatically identify on connect you need to connect to the bouncer as your bot's user with an IRC client and follow the instructions: 

- [https://wiki.znc.in/Nickserv]

To use the bouncer with Freenode you will most likely want to setup sasl authentication: 
- [https://wiki.znc.in/Sasl#example]
- [https://freenode.net/kb/answer/sasl]

### Starting the container
`docker run --restart=always -it -v /home/erratic/slack_irc:/config netcrave/slack-irc`

### Troubleshooting 
- Not connecting to ZNC? make sure your firewall is allowing it. Try disabling iptables and restarting docker so that only docker iptables rules are applied. ZNC can be tested with a normal IRC client like irssi, just point it to 172.17.0.1 and `/quote PASS nick/network password` but you may want to test this from irssi running in a container, also. 

