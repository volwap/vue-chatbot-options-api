<template>
  <div class="message-box">
    <textarea
      class="message-input"
      placeholder="Введите сообщение..."
      v-model="comment"
      @keydown.enter.exact.prevent
      @keyup.enter.exact="sendMessage"
    ></textarea>
    <button
      type="submit"
      class="message-submit"
      @click="sendMessage"
    >Отправить</button>
  </div>
</template>

<script>
export default {
  name: 'MessageBox',
  data() {
    return {
      comment: '',
      chatbotMessages: [
        'Привет! Меня зовут Борис, а вас?',
        'Приятно с вами познакомиться!',
        'Как ваши дела?',
        'Не так уж и плохо, спасибо)',
        'Чем вы занимаетесь?',
        'Это потрясающе!',
        'Чат - хорошее место для общения',
        'Я думаю, что вы - хороший человек',
        'Почему вы так думаете?',
        'Можете объяснить?',
        'В любом случае я должен идти',
        'Было приятно поболтать с вами',
        'Пришло время написать больше кода',
        'Счастливо оставаться!',
        ':)',
      ],
      chatbotIndex: 0,
    };
  },
  mounted() {
    this.sendChatbotMessage();
  },
  methods: {
    sendMessage() {
      if (!this.comment) return;
      const message = {
        id: Date.now(),
        text: this.comment,
      };
      this.$emit('sendMessage', message);
      this.comment = '';
      setTimeout(this.sendChatbotMessage, 1000 + (Math.random() * 20) * 100);
    },
    sendChatbotMessage() {
      if (this.comment) return;
      const message = {
        id: Date.now(),
        text: this.chatbotMessages[this.chatbotIndex],
        date: new Date(),
        chatbot: true,
      };
      this.$emit('sendMessage', message);
      if (this.chatbotIndex < this.chatbotMessages.length) {
        this.chatbotIndex += 1;
      }
      if (this.chatbotIndex === 4) {
        setTimeout(this.sendChatbotMessage, 1000 + (Math.random() * 20) * 100);
      }
    },
  },
};
</script>
