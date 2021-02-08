# Matrix Message github action

This is a simple github action to send messages with subjects to matrix servers.

## Usage

Sending messages requires generating of an access token, which can be done with
`curl`, and is detailed [here](https://matrix.org/docs/guides/client-server-api/).

The Room ID does not refer to the room's name, but its unique ID. In Riot, this
can be found by navigating to 'Room Settings' -> 'Advanced'.

Markdown-formatted messages are supported.

```workflow
name: Send a hello world to matrix every 5 minutes
on:
  schedule:
    - cron: '*/5 * * * *'
jobs:
  ping_matrix:
   runs-on: ubuntu-latest
   steps:
     - name: send message
       uses: olabiniV2/matrix-msg-action@v0.0.1
       with:
         room_id: ${{ secrets.MATRIX_ROOM_ID }}
         access_token: ${{ secrets.MATRIX_ACCESS_TOKEN }}
         subject: "Something"
         message: "Hello, world"
         server: "matrix.org"
```


## Credits

This project was primarily created by Martin Pugh (pugh@s3kr.it). This version is a very slight change that might be
contributed back soon.
