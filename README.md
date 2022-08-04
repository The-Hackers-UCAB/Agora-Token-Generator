# Agora Node Token Server

This is an example of a simple Node/Express server that generates tokens for Agora applications.


## Installation

```bash
#npm dependencies
$ npm install

#.env.example configuration (Add your Agora App ID and App Certificate)
$ cp .env.example .env
```

## Running the app

```bash
$ npm start
```
## Endpoints



### Test (Ping)

Test connectivity by sending a `ping` request.

```bash
#endpoint structure
GET ${url}/ping

#response:
{"message":"pong"}
```


### RTC Token

The `rtc` token endpoint requires a `tokentype` (uid || userAccount), `channelName`, and the user's `uid` (type varies based on `tokentype`). `(optional)` Pass an integer to represent the token lifetime in seconds.

```bash
#endpoint structure
GET ${URL}/rtc/${channelName}/${role}/${tokentype}/${uid}/?expiry=

#response:
{"rtcToken":" "}
```


### RTM Token

The `rtm` token endpoint requires the user's `uid`. `(optional)` Pass an integer to represent the privelege lifetime in seconds.

```bash
#endpoint structure
GET ${url}/rtm/${uid}/?expiry=

#response:
{"rtmToken":" "}
```


### RTE Tokens

The `rte` token endpoint generates both the `rtc` and `rtm` tokens with a single request. This endpoint requires a `tokentype` (uid || userAccount), `channelName`, and the user's `uid` (type varies `String/Int` based on `tokentype`). `(optional)` Pass an integer to represent the token lifetime in seconds.

```bash
#endpoint structure
GET ${url}/rte/${channelName}/${role}/${tokentype}/${uid}/?expiry=

#response:
{
  "rtcToken":" ",
  "rtmToken":" "
}
```

## License

Agora-Token-Generator is [MIT licensed](LICENSE)


## Extras

### Guides

- [Example of a simple Node/Express server that generates tokens for Agora applications.](https://github.com/AgoraIO-Community/Agora-Node-TokenServer)

