<template>
<div id="container">
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
</div>

</template>

<script setup>
import { ref, onMounted } from 'vue'
import mqtt from 'mqtt'
import nipplejs from 'nipplejs'

const video = ref(null)

const client = mqtt.connect('wss://broker.emqx.io:8084/mqtt')

var offerId = Math.floor((Math.random() * 1000) + 1);
var answerId = Math.floor((Math.random() * 1000) + 1);
var deviceId = 'test'
var isMuted = true
var dcOpened = false

client.on('connect', function () {
  console.log("connected")
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
  if (msg.id == offerId) {

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
  bottom: 80px;
  right: 80px;
}

:-webkit-full-screen video {
  width: 100%;
  height: 100%;
}

.video {
  position: fixed;
  top: 50%;
  left: 50%;
  transform: translate(-50%,-50%);
}
</style>
