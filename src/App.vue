<template>
<div id="container">
  <h3 class="state">{{state}}</h3>
  <div class="btn-setup" id="btn-setup">
<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 512 512"><!--!Font Awesome Free 6.5.2 by @fontawesome - https://fontawesome.com License - https://fontawesome.com/license/free Copyright 2024 Fonticons, Inc.--><path d="M495.9 166.6c3.2 8.7 .5 18.4-6.4 24.6l-43.3 39.4c1.1 8.3 1.7 16.8 1.7 25.4s-.6 17.1-1.7 25.4l43.3 39.4c6.9 6.2 9.6 15.9 6.4 24.6c-4.4 11.9-9.7 23.3-15.8 34.3l-4.7 8.1c-6.6 11-14 21.4-22.1 31.2c-5.9 7.2-15.7 9.6-24.5 6.8l-55.7-17.7c-13.4 10.3-28.2 18.9-44 25.4l-12.5 57.1c-2 9.1-9 16.3-18.2 17.8c-13.8 2.3-28 3.5-42.5 3.5s-28.7-1.2-42.5-3.5c-9.2-1.5-16.2-8.7-18.2-17.8l-12.5-57.1c-15.8-6.5-30.6-15.1-44-25.4L83.1 425.9c-8.8 2.8-18.6 .3-24.5-6.8c-8.1-9.8-15.5-20.2-22.1-31.2l-4.7-8.1c-6.1-11-11.4-22.4-15.8-34.3c-3.2-8.7-.5-18.4 6.4-24.6l43.3-39.4C64.6 273.1 64 264.6 64 256s.6-17.1 1.7-25.4L22.4 191.2c-6.9-6.2-9.6-15.9-6.4-24.6c4.4-11.9 9.7-23.3 15.8-34.3l4.7-8.1c6.6-11 14-21.4 22.1-31.2c5.9-7.2 15.7-9.6 24.5-6.8l55.7 17.7c13.4-10.3 28.2-18.9 44-25.4l12.5-57.1c2-9.1 9-16.3 18.2-17.8C227.3 1.2 241.5 0 256 0s28.7 1.2 42.5 3.5c9.2 1.5 16.2 8.7 18.2 17.8l12.5 57.1c15.8 6.5 30.6 15.1 44 25.4l55.7-17.7c8.8-2.8 18.6-.3 24.5 6.8c8.1 9.8 15.5 20.2 22.1 31.2l4.7 8.1c6.1 11 11.4 22.4 15.8 34.3zM256 336a80 80 0 1 0 0-160 80 80 0 1 0 0 160z"/></svg>
  </div>
  <div class="btn-fs" id="btn-fs">
    <svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 448 512"><!--!Font Awesome Free 6.5.2 by @fontawesome - https://fontawesome.com License - https://fontawesome.com/license/free Copyright 2024 Fonticons, Inc.--><path d="M32 32C14.3 32 0 46.3 0 64v96c0 17.7 14.3 32 32 32s32-14.3 32-32V96h64c17.7 0 32-14.3 32-32s-14.3-32-32-32H32zM64 352c0-17.7-14.3-32-32-32s-32 14.3-32 32v96c0 17.7 14.3 32 32 32h96c17.7 0 32-14.3 32-32s-14.3-32-32-32H64V352zM320 32c-17.7 0-32 14.3-32 32s14.3 32 32 32h64v64c0 17.7 14.3 32 32 32s32-14.3 32-32V64c0-17.7-14.3-32-32-32H320zM448 352c0-17.7-14.3-32-32-32s-32 14.3-32 32v64H320c-17.7 0-32 14.3-32 32s14.3 32 32 32h96c17.7 0 32-14.3 32-32V352z"/></svg>
  </div>
  <div class="btn-mute" id="btn-mute">
    <svg id="volume-high" style="display: none" xmlns="http://www.w3.org/2000/svg" viewBox="0 0 640 512"><!--!Font Awesome Free 6.5.2 by @fontawesome - https://fontawesome.com License - https://fontawesome.com/license/free Copyright 2024 Fonticons, Inc.--><path d="M533.6 32.5C598.5 85.2 640 165.8 640 256s-41.5 170.7-106.4 223.5c-10.3 8.4-25.4 6.8-33.8-3.5s-6.8-25.4 3.5-33.8C557.5 398.2 592 331.2 592 256s-34.5-142.2-88.7-186.3c-10.3-8.4-11.8-23.5-3.5-33.8s23.5-11.8 33.8-3.5zM473.1 107c43.2 35.2 70.9 88.9 70.9 149s-27.7 113.8-70.9 149c-10.3 8.4-25.4 6.8-33.8-3.5s-6.8-25.4 3.5-33.8C475.3 341.3 496 301.1 496 256s-20.7-85.3-53.2-111.8c-10.3-8.4-11.8-23.5-3.5-33.8s23.5-11.8 33.8-3.5zm-60.5 74.5C434.1 199.1 448 225.9 448 256s-13.9 56.9-35.4 74.5c-10.3 8.4-25.4 6.8-33.8-3.5s-6.8-25.4 3.5-33.8C393.1 284.4 400 271 400 256s-6.9-28.4-17.7-37.3c-10.3-8.4-11.8-23.5-3.5-33.8s23.5-11.8 33.8-3.5zM301.1 34.8C312.6 40 320 51.4 320 64V448c0 12.6-7.4 24-18.9 29.2s-25 3.1-34.4-5.3L131.8 352H64c-35.3 0-64-28.7-64-64V224c0-35.3 28.7-64 64-64h67.8L266.7 40.1c9.4-8.4 22.9-10.4 34.4-5.3z"/></svg>
    <svg id="volume-xmark" xmlns="http://www.w3.org/2000/svg" viewBox="0 0 576 512"><!--!Font Awesome Free 6.5.2 by @fontawesome - https://fontawesome.com License - https://fontawesome.com/license/free Copyright 2024 Fonticons, Inc.--><path d="M301.1 34.8C312.6 40 320 51.4 320 64V448c0 12.6-7.4 24-18.9 29.2s-25 3.1-34.4-5.3L131.8 352H64c-35.3 0-64-28.7-64-64V224c0-35.3 28.7-64 64-64h67.8L266.7 40.1c9.4-8.4 22.9-10.4 34.4-5.3zM425 167l55 55 55-55c9.4-9.4 24.6-9.4 33.9 0s9.4 24.6 0 33.9l-55 55 55 55c9.4 9.4 9.4 24.6 0 33.9s-24.6 9.4-33.9 0l-55-55-55 55c-9.4 9.4-24.6 9.4-33.9 0s-9.4-24.6 0-33.9l55-55-55-55c-9.4-9.4-9.4-24.6 0-33.9s24.6-9.4 33.9 0z"/></svg>
  </div>
  <div class='joystick' id="joystick">
  </div>
  <video ref="video" class="video" playsinline>
    <source src=http://commondatastorage.googleapis.com/gtv-videos-bucket/sample/BigBuckBunny.mp4 type=video/mp4>
  </video>
  <dialog id="setup-dialog">
    <textarea id="config" cols=40 rows=10></textarea>
    <br>
    <div id="btn-setup-save" class="btn">
    <svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 448 512"><!--!Font Awesome Free 6.5.2 by @fontawesome - https://fontawesome.com License - https://fontawesome.com/license/free Copyright 2024 Fonticons, Inc.--><path d="M64 32C28.7 32 0 60.7 0 96V416c0 35.3 28.7 64 64 64H384c35.3 0 64-28.7 64-64V173.3c0-17-6.7-33.3-18.7-45.3L352 50.7C340 38.7 323.7 32 306.7 32H64zm0 96c0-17.7 14.3-32 32-32H288c17.7 0 32 14.3 32 32v64c0 17.7-14.3 32-32 32H96c-17.7 0-32-14.3-32-32V128zM224 288a64 64 0 1 1 0 128 64 64 0 1 1 0-128z"/></svg>
    </div>
    <div id="btn-setup-edit" class="btn">
      <svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 512 512"><!--!Font Awesome Free 6.5.2 by @fontawesome - https://fontawesome.com License - https://fontawesome.com/license/free Copyright 2024 Fonticons, Inc.--><path d="M471.6 21.7c-21.9-21.9-57.3-21.9-79.2 0L362.3 51.7l97.9 97.9 30.1-30.1c21.9-21.9 21.9-57.3 0-79.2L471.6 21.7zm-299.2 220c-6.1 6.1-10.8 13.6-13.5 21.9l-29.6 88.8c-2.9 8.6-.6 18.1 5.8 24.6s15.9 8.7 24.6 5.8l88.8-29.6c8.2-2.7 15.7-7.4 21.9-13.5L437.7 172.3 339.7 74.3 172.4 241.7zM96 64C43 64 0 107 0 160V416c0 53 43 96 96 96H352c53 0 96-43 96-96V320c0-17.7-14.3-32-32-32s-32 14.3-32 32v96c0 17.7-14.3 32-32 32H96c-17.7 0-32-14.3-32-32V160c0-17.7 14.3-32 32-32h96c17.7 0 32-14.3 32-32s-14.3-32-32-32H96z"/></svg>
    </div>
    <div id="btn-setup-close" class="btn">
      <svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 512 512"><!--!Font Awesome Free 6.5.2 by @fontawesome - https://fontawesome.com License - https://fontawesome.com/license/free Copyright 2024 Fonticons, Inc.--><path d="M256 512A256 256 0 1 0 256 0a256 256 0 1 0 0 512zM175 175c9.4-9.4 24.6-9.4 33.9 0l47 47 47-47c9.4-9.4 24.6-9.4 33.9 0s9.4 24.6 0 33.9l-47 47 47 47c9.4 9.4 9.4 24.6 0 33.9s-24.6 9.4-33.9 0l-47-47-47 47c-9.4 9.4-24.6 9.4-33.9 0s-9.4-24.6 0-33.9l47-47-47-47c-9.4-9.4-9.4-24.6 0-33.9z"/></svg>
    </div>
  </dialog>

</div>

</template>

<script setup>
import { ref, onMounted } from 'vue'
import mqtt from 'mqtt'
import nipplejs from 'nipplejs'

const video = ref(null)
const state = ref(null)

var playerConfig = JSON.parse(localStorage.getItem('pp'))
if (playerConfig == null) {
  playerConfig = {}
  playerConfig.mqttUrl = "wss://broker.emqx.io:8084/mqtt"
  playerConfig.deviceId = "test"
  playerConfig.username = ""
  playerConfig.password = ""
  playerConfig.rotate = false
}

const deviceId = playerConfig.deviceId
const client = mqtt.connect(playerConfig.mqttUrl, {
  clientId: playerConfig.clientId,
  username: playerConfig.username,
  password: playerConfig.password,
})

var offerId = Math.floor((Math.random() * 1000) + 1);
var answerId = Math.floor((Math.random() * 1000) + 1);
var isMuted = true
var dcOpened = false

client.on('connect', () => {
  console.log("connected")
  state.value = 'Connecting.'
  client.subscribe('webrtc/' + deviceId + '/jsonrpc-reply', function (err) {
    if (!err) {
      console.log('subscribe ok')
    }
  })

  client.publish('webrtc/' + deviceId + '/jsonrpc', JSON.stringify({
   jsonrpc: '2.0',
   method: 'offer',
   id: offerId,
  }), {qos: 2})
})

client.on('message', function (topic, message) {

  let msg = JSON.parse(message.toString())
  console.log(msg)

  if (msg.error != undefined) {
    console.log(msg.error)
    state.value = msg.error.message
  } else if (msg.id == offerId) {

    state.value = 'Connecting..'
    let sdp = msg.result;
    let offer = {type: 'offer', sdp: sdp};
    console.log(offer)
    pc.setRemoteDescription(offer);
    pc.createAnswer().then(d => pc.setLocalDescription(d)).catch(() => console.log('error'));

    setTimeout(() => {
      let json = {
        jsonrpc: '2.0',
        method: 'answer',
        params: pc.localDescription.sdp,
        id: answerId,
      }
      console.log(json)
      client.publish('webrtc/' + deviceId + '/jsonrpc', JSON.stringify(json))
    }, 1000)

  } else if (msg.id == answerId) {

    console.log('receive answer ok')
  }
})


var pc = new RTCPeerConnection({
  iceServers: [
    {
      urls: "stun:stun.l.google.com:19302",
    },
  ],
});

const datachannel = pc.createDataChannel('libpeer')
pc.ontrack = (event) => {
  console.log(event.track.kind)
  if (event.track.kind == 'video') {
    video.value.srcObject = event.streams[0];
    video.value.muted = true;
    video.value.autoplay = true;
    console.log(video.value);
  } else if (event.track.kind == 'audio') {
    console.log('audio')
  }
}

pc.oniceconnectionstatechange = e => {
  console.log(pc.iceConnectionState)
  if (pc.iceConnectionState == 'checking') {
    state.value = 'Connecting...'
  } else if (pc.iceConnectionState == 'connected') {
    state.value = ''
  } else if (pc.iceConnectionState == 'disconnected') {
    state.value = 'Disconnected'
  } else if (pc.iceConnectionState == 'failed') {
    state.value = 'Failed'
  }
  console.log(e)
}

pc.ondatachannel = () => {
  console.log('ondatachannel');
}

datachannel.onclose = () => console.log('datachannel has closed');
datachannel.onopen = () => {
  dcOpened = true;
}

datachannel.onmessage = e => {
  console.log(e.data)
}

pc.onicecandidate = event => {
  console.log(event.candidate)
}

pc.addTransceiver('video', {direction: 'recvonly'});

const roundTo = function( num, decimal ) { return Math.round( ( num + Number.EPSILON ) * Math.pow( 10, decimal ) ) / Math.pow( 10, decimal ); }

onMounted(() => {
  if (playerConfig.rotate) {
    video.value.style.transform = 'translateY(-50%) rotate(180deg)';
  }

  var joystick = nipplejs.create({
    zone: document.getElementById('joystick'),
    mode: 'static',
    color: 'white',
    size: 100,
    position: { left: '20%', top: '20%' },
  });
  joystick.on('start end', function(evt) {
    console.log(evt.type, 0, 0);
    if (dcOpened) {
      datachannel.send(JSON.stringify({x: 0, y: 0}))
    }
  })
  joystick.on('move', function(evt, data) {
    console.log(evt.type, roundTo(data.vector.x, 2), roundTo(data.vector.y, 2));
    if (dcOpened) {
      datachannel.send(JSON.stringify({x: roundTo(data.vector.x, 2), y: roundTo(data.vector.y, 2)}))
    }
  })

  const setup = document.getElementById('btn-setup')
  setup.addEventListener('click', () => {
    document.getElementById('setup-dialog').showModal();
  });

  const setupEdit = document.getElementById('btn-setup-edit');
  const setupClose = document.getElementById('btn-setup-close');
  const setupSave = document.getElementById('btn-setup-save');
  const configText = document.getElementById('config');
  configText.value = JSON.stringify(playerConfig, null, 2);
  configText.disabled = true
  setupSave.style.display = 'none'

  setupEdit.addEventListener('click', () => {
    configText.disabled = false
    setupEdit.style.display = 'none'
    setupSave.style.display = 'inline-block'
  });

  setupSave.addEventListener('click', () => {

    try {
      playerConfig = JSON.parse(document.getElementById('config').value)
      localStorage.setItem('pp', JSON.stringify(playerConfig));
      configText.value = JSON.stringify(playerConfig, null, 2);
      configText.disabled = true
      setupSave.style.display = 'none'
      setupEdit.style.display = 'inline-block'
    } catch {
      console.log('not json format')
    }

  });

  setupClose.addEventListener('click', () => {
    document.getElementById('setup-dialog').close();
  });

  var fs = document.getElementById('btn-fs');
  var mute = document.getElementById('btn-mute');
  fs.addEventListener('click', goFullScreen);
  mute.addEventListener('click', () => {
    isMuted = !isMuted
    video.value.muted = isMuted
    if (isMuted) {
      document.getElementById('volume-high').style.display = 'none'
      document.getElementById('volume-xmark').style.display = 'block'
    } else {
      document.getElementById('volume-high').style.display = 'block'
      document.getElementById('volume-xmark').style.display = 'none'
    }
  })
})

function goFullScreen() {
  var fullscreenElement = document.fullscreenElement || document.mozFullScreenElement || document.webkitFullscreenElement || document.msFullscreenElement;
  if (fullscreenElement) {
    exitFullscreen();
  } else {
    launchIntoFullscreen(document.getElementById('container'));
  }
}

function launchIntoFullscreen(element) {
  if (element.requestFullscreen) {
    element.requestFullscreen();
  } else if (element.mozRequestFullScreen) {
    element.mozRequestFullScreen();
  } else if (element.webkitRequestFullscreen) {
    element.webkitRequestFullscreen();
  } else if (element.msRequestFullscreen) {
    element.msRequestFullscreen();
  } else if (video.value.webkitEnterFullScreen) {
    video.value.webkitEnterFullScreen();
  }
}

function exitFullscreen() {
  if (document.exitFullscreen) {
    document.exitFullscreen();
  } else if (document.mozCancelFullScreen) {
    document.mozCancelFullScreen();
  } else if (document.webkitExitFullscreen) {
    document.webkitExitFullscreen();
  }
}

</script>

<style scoped>

#container {
  width: 100%;
  height: 100%;
}

.btn-mute {
  background: rgba(255, 255, 255, 0.3);
  position: absolute;
  width: 25px;
  height: 25px;
  padding: 10px;
  border-radius: 15px;
  z-index: 10;
  cursor: pointer;
  bottom: 40px;
  left: 60px;
}

.btn-setup {
  background: rgba(255, 255, 255, 0.3);
  position: absolute;
  width: 25px;
  height: 25px;
  padding: 10px;
  border-radius: 15px;
  z-index: 10;
  cursor: pointer;
  bottom: 40px;
  left: 110px;
}

.btn {
  background: rgba(255, 255, 255, 0.3);
  width: 17px;
  height: 17px;
  padding: 10px;
  color: white;
  border-radius: 15px;
  cursor: pointer;
  display: inline-block
}


.btn-fs {
  background: rgba(255, 255, 255, 0.3);
  position: absolute;
  width: 25px;
  height: 25px;
  padding: 10px;
  color: white;
  border-radius: 15px;
  z-index: 10;
  cursor: pointer;
  bottom: 40px;
  left: 10px;
}

.joystick {
  position: absolute;
  bottom: 70px;
  right: 70px;
  height: 1%;
  width: 1%;
}

:-webkit-full-screen video {
  width: 100%;
  height: 100%;
}

.video {
  position: fixed;
  width: 100%;
  top: 50%;
  transform: translateY(-50%);
}

:modal {
  background-color: beige;
  border: 2px solid burlywood;
  border-radius: 5px;
}

.state {
  position: absolute;
  color: white;
  z-index: 10;
  top: 50%;
  left: 50%;
  transform: translate(-50%,-50%);
}

dialog:modal {
  max-width: calc(100% - 6px - 2em);
}
</style>
