<template>
    <div class="group" id="Experience">
        <div class="group-title">
            <h1>Experiencia</h1>
        </div>
        <div class="group-description">
            <div class="group-left">      
                <div class="group-down">
                    <transition name="slide-left" mode="out-in">
                        <div class="group-down-boxes" id="Mcdonalds" ref="mcdonalds" @mouseenter="job = 'McDonalds'" @mouseleave="job = 'WebDeveloper'">
                            <h2>Camarera / Personal de Equipo</h2>
                            <p>Mcdonals | Septiembre 2024 - Febrero 2025</p>
                            <p>Atención al cliente, preparación de alimentos, limpieza, entre otras funciones. </p>
                        </div>
                    </transition>

                    <transition name="slide-left" mode="out-in">
                        <div class="group-down-boxes" id="WebDeveloper" ref="webDeveloper" @mouseenter="job = 'WebDeveloper'" @mouseleave="job = 'WebDeveloper'">
                            <h2>Junior Web Developer</h2>
                            <p>Knowmad mood | Marzo 2024 - Junio 2024</p>
                            <p>Desarrollo de aplicaciones web con tecnologías como HTML, CSS, Java, Spring Boot, MySQL, Jenkings, Jmeter SonarQube...</p>
                        </div>
                    </transition>

                    <transition name="slide-left" mode="out-in">
                        <div class="group-down-boxes" id="Telemarketing" ref="telemarketing" @mouseenter="job = 'Telemarketing'" @mouseleave="job = 'WebDeveloper'">
                            <h2>Operadora Telemarketing</h2>
                            <p>Konecta | Octubre 2021 - Marzo 2022</p>
                            <p>Atención al cliente, ventas, soporte técnico, entre otras funciones.</p>
                        </div>
                    </transition>

                    <transition name="slide-left" mode="out-in">
                        <div class="group-down-boxes" id="Modeladora3D" ref="modeladora3D" @mouseenter="job = 'Modeladora3D'" @mouseleave="job = 'WebDeveloper'">
                            <h2>Modeladora 3D</h2>
                            <p>Nimoria Studio | Octubre 2020 - Marzo 2021</p>
                            <p>Modelado de personajes y escenarios en 3D para videojuegos.</p>
                        </div>
                    </transition>
                    
                </div>
            </div>
            <div class="group-right">
                <div class="group-video">   
                    <transition name="slide-right" mode="out-in">              
                        <template v-if="job === 'WebDeveloper'">
                            <video id="jobVideo" ref="jobVideo" muted autoplay loop>
                                <source src="../../assets/webdeveloper.webm" type="video/mp4">
                            </video>
                        </template>
                        <template v-else-if="job === 'McDonalds'">
                            <video id="jobVideo" ref="jobVideo" muted autoplay loop>
                                <source src="../../assets/mcdonalds.webm" type="video/mp4">
                            </video>
                        </template>
                        <template v-else-if="job === 'Telemarketing'">
                            <video id="jobVideo" ref="jobVideo" muted autoplay loop>
                                <source src="../../assets/teleoperator.webm" type="video/mp4">
                            </video>
                        </template>
                        <template v-else-if="job === 'Modeladora3D'">
                            <video id="jobVideo" ref="jobVideo" muted autoplay loop>
                                <source src="../../assets/3dmodeler.webm" type="video/mp4">
                            </video>
                        </template>
                    </transition>
                </div>
            </div>
        </div>
    </div>



</template>

<script>
export default {
  data() {
    return {
      job: 'WebDeveloper',
    };
  }, /*mounted() {
    const viewportHeight = window.innerHeight;

    const elements = [
      this.$refs.mcdonalds,
      this.$refs.webDeveloper,
      this.$refs.telemarketing,
      this.$refs.modeladora3D
    ];

    elements.forEach((element) => {
        const options = {
          threshold: Math.min(1, (viewportHeight / element.clientHeight * 0.6)/100)
        };
        console.log(options.threshold);
        const observer = new IntersectionObserver((entries) => {
          entries.forEach(entry => {
            if (entry.isIntersecting) {
              entry.target.classList.add('slide-left-enter-active');
              entry.target.classList.remove('slide-left-leave-active');
            } else if (entry.boundingClientRect.top > 0) {
              entry.target.classList.remove('slide-left-enter-active');
              entry.target.classList.add('slide-left-leave-active');
            }
          });
        }, options);

        observer.observe(element);
    });
  }*/
  mounted() {
    const elements = [
      this.$refs.mcdonalds,
      this.$refs.webDeveloper,
      this.$refs.telemarketing,
      this.$refs.modeladora3D
    ];

    elements.forEach((element) => {
        const options = {
          threshold: 0.5, // Ajusta el umbral según sea necesario
        };
        const observer = new IntersectionObserver((entries) => {
          entries.forEach(entry => {
            if (entry.isIntersecting) {
              entry.target.classList.add('slide-left-enter-active');
              entry.target.classList.remove('slide-left-leave-active');
            } else if (entry.boundingClientRect.top > 0) {
              entry.target.classList.remove('slide-left-enter-active');
              entry.target.classList.add('slide-left-leave-active');
            }
          });
        }, options);

        observer.observe(element);
    });
  }
};
</script>

<style scoped>

    .group{
        display: flex;
        width: 100%;
        flex-direction: column;
        justify-content: center;
        align-items: center;

    }

   .group-description{
        font-family: Roboto;
        display: grid;
        grid-template-columns: 1fr 1fr;
        width: 100%;
    }
    .group-right{
        display: flex;
        flex-direction:column;
        justify-content: center;
        align-items: center;
        background-color: #faf3e1;
    }

    .group-left{
        display: flex;
        flex-direction:column;
        justify-content: center;
        align-items: center;
        background-color: #faf3e1;
    }
    .group-title{

        display: flex;
        justify-content: center;
        h1{
            font-size: 2.5vw;
        }
    }

    .group-down{
        font-size: 1em;
        margin: 1em;
        width: 95%;

    }

    .group-down-boxes{
        margin-left: 4em;
        background-color: #fdf9f8;
        border-radius: 1em;
        border: 2px solid #000000;
        box-shadow:0.2vw 0.2vw 0.1vw #000000;
        padding: 0.3em;
        padding-left: 1em;
        margin-bottom: 1em; 

        transition: all 0.5s ease;
        
        h2{
            font-size: 1.2vw;
        }

        p{
            font-size: 0.8vw;
        }
    }

    .group-down-boxes-visible{
        opacity: 1;
    }

    .group-down-boxes:hover{
        background-color: #78c2a7;
    }


    .group-video{
        width: 30vw;
        height: 30vw;
        overflow: hidden;
        display: flex;
        justify-content: center;
        align-items: center;
        border-radius: 1em;
    }

    .group-video video{
        transform: scale(0.7);
    }

    .slide-left-enter-active {
        transition: all 1s ease-out;
        transform: translateX(0%);
        opacity: 1;
    }

    .slide-left-leave-active {
        transition: all 0.2s ease;
        transform: translateX(-50%);
        opacity: 0;
    }



    /*----------Version Movil---------- */

    @media (max-width: 1024px) {
        .group{
            justify-content: flex-start;
        }
        .group-description{
            display: flex;
            flex-direction: column;
        }

        .group-title{
            display: flex;
            h1{
                font-size: 8vw;
            }
        }
        .group-left {
            width: 100%;
            align-items: center;
            
            h1{
                padding-left: 0;
                font-size: 10vw;
            }
        }

        .group-down-boxes{
            margin-left: 0; /* NO FUNIONA SI QUITO EL MARING LEFT, PASA LO MISMO DEL FALLO DE CALCULO */
            height: 25vw;


            transition: all 0.5s ease;
            
            h2{
                font-size: 4vw;
            }

            p{
                font-size: 2.5vw;
            }
        }
        .group-right {
            display: none;
        }

    }

</style>