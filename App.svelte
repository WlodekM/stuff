
<script>
import CloudlinkClient from 'cl.js';

// setup a new client
let cloudlink = new CloudlinkClient({
  url: "wss://server.meower.org/",
  log: true
})

// listen for packets
cloudlink.on("packet", (packet) => {
  console.log("Received packet:", packet)
})

// send a packet
async function sendtest() {
    await cloudlink.send({
      cmd: "direct",
      val: {
        "cmd": "gen_account",
        "val": {
            "username": "testing1212",
            "pswd": "pass"
        }
      },
      listener: "join"
    })
}
</script>
<button onclick="sendtest()">TEST!</button>