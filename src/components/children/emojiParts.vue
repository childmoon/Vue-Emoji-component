<template>
  <div>
    <span class="partsC" @click="emitMes"></span>
  </div>
</template>

<script>
export default {
  name: '',
  components: {
    
  },
  props:{
      text:String
  },
  methods:{
      emitMes(){
          this.$emit('callf',this.text)
      }
  }
}
</script>

<style lang="scss">
.partsC{
    display:inline-block;
    width:44.45px;
    height:44.45px;
    cursor:pointer;
}
</style>
