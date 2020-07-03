<template>
  <div class="gif-box">
    <a :href="gif.url">
      <img class="gif-image" :src="gif.images.original.url" />
    </a>
    <a class="gif-user" v-if="gif.user" :href="gif.user.profile_url">
      <img :src="gif.user.avatar_url" height="35" width="35" />
      {{ gif.user.display_name }}
    </a>
  </div>
</template>

<script>
export default {
  name: "gif-box",
  props: {
    gif: Array
  }
};
</script>
