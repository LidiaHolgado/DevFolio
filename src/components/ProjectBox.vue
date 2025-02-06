<template>
  <div class="box-container" ref="boxContainer"> 
    <a :href="link" target="_blank">
      <div class="box-image" :style="backgroundStyle"></div>
      <div class="box-content">
        <h1>{{ title }}</h1>
        <p class="card-text">{{ text }}</p>
      </div>
    </a>
  </div>

</template>
  
<script>

import 'animate.css'

export default {
  name: 'TecnologiesBox',
  props: {
    title: String,
    text: String,
    bgImage: String,
    link: String
  },
  computed:{
    backgroundStyle(){
      return {
        backgroundImage: `url(${this.bgImage})`,
        backgroundSize: 'cover',
        backgroundPosition: 'center',
        backgroundRepeat: 'no-repeat',
      }
    }
  }, 
  /*mounted() {
            const options = {
                threshold: 0.5
            };

            const observer = new IntersectionObserver((entries) => {
                entries.forEach(entry => {
                    if (entry.isIntersecting && entry.boundingClientRect.top > 0) {
                        if (entry.target.classList.contains('box-container')) {
                            entry.target.style.opacity = 1;
                            entry.target.classList.add('animate__animated', 'animate__zoomIn');
                        }
                    }else{
                        if (entry.target.classList.contains('box-container') && entry.boundingClientRect.top > 0) {
                            entry.target.style.opacity = 0;
                            entry.target.classList.remove('animate__animated', 'animate__zoomIn');
                        }
                    }
                });
            }, options);

            observer.observe(this.$refs.boxContainer);

        }*/

}
</script>

<style scoped>     
.box-container{
  width: 25vw;
  height: 23vw;
  border-radius: 0.8em;
  transition: transform 0.6s;
  z-index: 1;
  border: 0.15vw solid #0e0e0e;
  background-color: #fdf9f8;

  cursor: pointer;
  text-decoration: none;
  color: #0e0e0e;

  overflow: hidden;
}

.box-container:hover{
  transform: scale(1.05);
  box-shadow: 0.3vw 0.3vw 0vw 0.1vw #494949;
  transition: 0.3s;
}

.box-container a{
  text-decoration: none;
  color: #0e0e0e;
}

.box-image{
  width: 100%;
  height: 60%;
  border-radius: 0.5em 0.5em 0em 0em;
}

h1{
  font-size: 1.4vw;
  margin: 0.5vw;
}
p{
  font-size: 1vw;
  margin: 0.5vw;
}

.card-text{
  margin: 0.5vw;
}



@media(max-width: 1024px){

  .box-container{
    width: 70vw;
    height: auto;
    margin-top: 2em;
  }
  .box-image{
    height: 40vw;
  }

  h1{
    font-size: 4vw;
    margin: 2vw;
  }
  p{
    font-size: 3vw;
    padding: 2vw;
  }

  .box-content{
    display: flex;
    flex-direction: column;
    justify-content: start;
    align-items: start; 
    overflow: scroll;

  }
}

</style>