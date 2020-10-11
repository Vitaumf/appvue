<template>
  <div>
    <h3>{{message}}</h3>
  </div>
</template>
<script>

export default {
  props:{
    message:{
      type:String
    }
  }
};

</script>

<style scoped>

h3 {
  color: white;
}

</style>
