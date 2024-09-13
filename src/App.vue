<script setup>
import { onMounted } from 'vue';

// import { Client } from '@stomp/stompjs';
// import { onMounted, onUnmounted, ref } from 'vue';

// const messages = ref([]);
// const newMessage = ref("");
// const client = ref(null);


// const connection = () => {
//   client.value = new Client({
//     brokerURL: 'ws://localhost:8080/ws', // WebSocket URL
//     onConnect: () => {
//       console.log('STOMP 연결 성공');
//       client.value.subscribe('/sub/chatroom/1', (message) => {
//         messages.value.push(message.body);
//       });
//     },
//     onStompError: (frame) => {
//       console.error('STOMP 오류:', frame.headers['message']);
//     }
//   });

//   client.value.activate();
// }

// const sendMessage = () => {
//   if (newMessage.value) {
//     client.value.publish({
//       destination: '/pub/message', // 메시지를 보낼 엔드포인트
//       body: JSON.stringify({id:1, message: newMessage.value})
//     });
//     newMessage.value = "";
//   }else{
//     console.log("error")
//   }
// }


// onMounted(() => {
//   connection();
// });

// onUnmounted(() => {
//   if (client.value) {
//     client.value.deactivate();
//   }
// })

onMounted(()=>{
  fetch("http://222.112.124.237:8080/test").then(response => response.json())
  .then(data => {
    console.log("==============");
    console.log(data);
    console.log("==============");
  });
});
</script>

<template>

  <h1> example message</h1>
  <div v-for="msg in messages" :key="msg">{{ msg }}</div>
  <input v-model="newMessage" @keyup.enter="sendMessage" placeholder="메시지 입력" />
  
</template>

<style scoped></style>
