<template>
  <div>
    <!-- <img :src="author.image" /> -->
    <div>
      <p>Written by: {{ author.name }}</p>
      <p>Author bio: {{ author.bio }}</p>
    </div>
  </div>
</template>

<script>
  export default {
    props: {
      author: {
        type: Object,
        required: true
      }
    }
  }
</script>
