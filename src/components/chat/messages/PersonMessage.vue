<template>
  <div class="message new message-personal">
    <span>{{message.text}}</span>
  </div>
</template>

<script>
export default {
  name: 'PersonMessage',
  props: {
    message: Object,
  },
};
</script>
