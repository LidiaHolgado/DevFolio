<template>
    <div class="box-container" :style="{ backgroundColor: bgColor }">
        <img :src="img" alt="logo" width="100" height="100">
        <h1>{{ title }}</h1>
    </div>

</template>
  
<script>
  

  export default {
    name: 'TecnologiesBox',
    props: {
      title: String,
      img: String,
      bgColor: {
        type: String,
        default: '#fdf9f8',
      }
    }
  }

</script>

  <!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>     
.box-container{
  width: 12dvw;
  height: 13dvw;
  border-radius: 0.4dvw;
  transition: transform 0.6s;
  z-index: 1;
  border: 0.1dvw solid #000;
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  
}

.box-container:hover{
  transform: scale(1.05);
  box-shadow: 0.2em 0.2em 0em 0.1em #494949;
  transition: 0.3s;
}

img{
  width: 6dvw;
  height: 6dvw;
  margin-bottom: 1em;
}

h1{
  font-size: 1.2dvw;
}

@media(max-width: 1024px){
  .box-container{
    width: 23dvw;
    height: 24dvw;
  }
  img{
    width: 13dvw;
    height: 13dvw;
    margin-bottom: 0.6em;
  }
  h1{
    font-size: 3dvw;
    margin-top:0;
  }
}

</style>