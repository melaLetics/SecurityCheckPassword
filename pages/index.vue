<template>
  <section class="input-container">
    <dynamic-check />
  </section>
</template>

<script>
import DynamicCheck from '../components/DynamicCheck'
export default {
  name: 'Startpage',
  components: { DynamicCheck }
}
</script>
<style scoped>
.input-container {
  padding: 35px;
}
</style>
