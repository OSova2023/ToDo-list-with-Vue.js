<template>
  <button @click="this.$emit('remove')" class="delete">{{ title }}</button>
</template>

<script>
export default {
  name: 'ButtonDel',
  data() {
    return {
      title: 'Delete'
    }
  }
}
</script>
<style></style>
