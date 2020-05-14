<template>
  <div class="chat-title">
    <h1>{{fio}}</h1>
    <h2>{{post}}</h2>
    <figure class="avatar">
      <img src="https://res.cloudinary.com/mhmd/image/upload/v1564960395/avatar_usae7z.svg"
           alt="avatar"/>
    </figure>
  </div>
</template>

<script>
export default {
  name: 'ChatTitle',
  props: ['fio', 'post'],
};
</script>
