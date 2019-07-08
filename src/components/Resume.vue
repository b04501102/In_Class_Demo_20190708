<template lang="pug">
  .resume
    .name {{ name }}
    ul.timeline
      li(v-for='event in experience') {{ event.title }}
</template>
<script>
export default {
  props: {
    name: String,
    experience: Array
  }
}
</script>

