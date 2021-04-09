<template>
  <div className="avatar">
    <img :src="data">
  </div>
</template>

<script>
export default {
  name: "Avatar",
  props: ['data']
}
</script>

<style scoped>

</style>