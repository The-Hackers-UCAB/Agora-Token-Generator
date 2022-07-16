# Agora Node Token Server

This is an example of a simple Node/Express server that generates tokens for Agora applications.

### Run the server

- Install the dependencies

```bash
#npm dependencies
$ npm install
```

- Create a copy of the `.env.example` file and save it as `.env`
- Add your Agora App ID and App Certificate:

```bash
#.env.example configuration
$ cp .env.example .env

#Data
APP_ID=ca123xxxxxx
APP_CERTIFICATE=12za123xxxxxx
```

You can obtain these values by selecting your project in the [Agora console projects section](https://console.agora.io/projects). Optionally, you can also define a port.

- Start the service

```node
npm start
```

## Endpoints

### Ping

**endpoint structure**

```
/ping
```

response:

```
{"message":"pong"}
```

### RTC Token

The `rtc` token endpoint requires a `tokentype` (uid || userAccount), `channelName`, and the user's `uid` (type varies based on `tokentype`).
`(optional)` Pass an integer to represent the token lifetime in seconds.

**endpoint structure**

```
/rtc/:channelName/:role/:tokentype/:uid/?expiry=
```

response:

```
{"rtcToken":" "}
```

## RTM Token

The `rtm` token endpoint requires the user's `uid`.
`(optional)` Pass an integer to represent the privelege lifetime in seconds.

**endpoint structure**

```
/rtm/:uid/?expiry=
```

response:

```
{"rtmToken":" "}
```

### Both Tokens

The `rte` token endpoint generates both the `rtc` and `rtm` tokens with a single request. This endpoint requires a `tokentype` (uid || userAccount), `channelName`, and the user's `uid` (type varies `String/Int` based on `tokentype`).
`(optional)` Pass an integer to represent the token lifetime in seconds.

**endpoint structure**

```
/rte/:channelName/:role/:tokentype/:uid/?expiry=
```

response:

```
{
  "rtcToken":" ",
  "rtmToken":" "
}
```
