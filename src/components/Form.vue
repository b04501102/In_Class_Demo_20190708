<template lang="pug">
  form
    label(for='name') Name
    input(id='name' v-model='fields.name')
</template>

<script>
export default {
  props: {
    fields: Object
  }
}
</script>

