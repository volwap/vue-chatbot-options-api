<template>
  <div class="chat">
    <ChatTitle v-bind:fio="'Boris Pavlov'" :post="'Full stack developer'"/>
    <MessagesList :messages="messages"/>
    <MessageBox @sendMessage="addMessage"/>
  </div>
</template>

<script>
import ChatTitle from './chat/ChatTitle.vue';
import MessagesList from './chat/MessagesList.vue';
import MessageBox from './chat/MessageBox.vue';

export default {
  name: 'Chat',
  components: { MessageBox, MessagesList, ChatTitle },
  data() {
    return {
      messages: [],
    };
  },
  methods: {
    addMessage(message) {
      this.messages.push(message);
    },
  },
};
</script>

<style lang="scss">
  @import "../styles/chat";
</style>
