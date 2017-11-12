<template>
  <div id="translateOutput">
    {{translatedText}}
  </div>
</template>

<script>


export default {
  name: 'translateOutput',
  props:[
    "translatedText"

  ]
 
}
</script>

<style scoped>
  #translateOutput{
    font-size: 28px;
  }
</style>
