# BUN-IPC
A method to get interprocess communication working using websockets in bun for mainly for windows, as bun currently lacks it :/

#Usage

Client - main file:

```js
import IPC from './IPC.js'
let client = await IPC.client({use: IPC.typeEnums.DFT, port: 3434})
client.set_IPC_Type(1) // change dft tag to the number you want the client/server to respond on
client.Console.read(async(msg) => {
    console.log(msg.data)
})
```

Server - extern.js file:

```js
import IPC from './IPC.js'
const s = IPC.newServer(IPC.typeEnums.DFT, { port: 3434 })
s.set_IPC_Type(1)
console = s.Console // change console to use s.Console which allows you to send messages to the client

s.close() // instruct to close the server and process
```
