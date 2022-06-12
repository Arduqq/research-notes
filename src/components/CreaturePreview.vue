<template>
  <div class="creaturePreview">
    <img :src="url"/>
  </div>
</template>

<script>
export default {
  name: 'creaturePreview',
  data() {
    return {
        
    };
  },
  props: {
    url: String
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
</style>
