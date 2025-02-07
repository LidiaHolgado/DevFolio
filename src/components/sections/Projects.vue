<template>
    <div class="group-tecnologies" id="Projects">
        <div class="group-up" ref="groupUp">
            <h1>Proyectos</h1>
        </div>
        <div class="group-down">
            <div class="group-down-boxes" ref="groupDownBoxes">
                <template v-if="isMobile">
                    <div v-for="(project, index) in projects" :key="index" ref="projectBox">
                        <ProjectBox
                            :bgImage="project.bgImage"
                            :title="project.title"
                            :text="project.text"
                            :link="project.link"
                        />
                    </div>
                </template>
                <template v-else>
                    <Carousel v-bind="carouselConfig">
                        <Slide v-for="(project, index) in projects" :key="index">
                            <ProjectBox
                                :bgImage="project.bgImage"
                                :title="project.title"
                                :text="project.text"
                                :link="project.link"
                            />
                        </Slide>
                        <template #addons>
                            <Navigation  style="margin-left: -5%; margin-right: -5%;"/>
                        </template>
                    </Carousel>
                </template>
            </div>
        </div>
        
    </div>
</template>

<script>
    import 'animate.css'
    import 'vue3-carousel/carousel.css';
    import { Carousel, Slide, Navigation } from 'vue3-carousel';
    import ProjectBox from '../ProjectBox.vue';

    import img1 from '@/assets/ProjectsImg/1.webp';
    import img2 from '@/assets/ProjectsImg/2.webp';
    import img3 from '@/assets/ProjectsImg/3.webp';

    export default {
        name: 'FourthSection',
        components: {
            ProjectBox,
            Carousel,
            Slide,
            Navigation
        },
        data(){
            return{
                isMobile: window.innerWidth <= 1024,
                carouselConfig:{
                    height: '100%',
                    wrapAround: true,
                    snapAlign: 'center',
                    gap: 0,
                    breakpoints: {
                        768: {
                            itemsToShow: 1.5
                        },
                        1025: {
                            itemsToShow: 3.5
                        }
                    }
                },
                projects:[
                        {
                            bgImage: img1,
                            title: 'GameMaster',
                            text: 'Web de trabajo de fin de grado realizada en React.js y Vite.js con conexió a la API de Juegos, además de tener un backend en php y una base de datos en MySQL.',
                            link: 'https://lidiaholgado.github.io/gamemaster'
                        },
                        {
                            bgImage: img2,
                            title: 'World Notes',
                            text: 'Script realizado en Lua para servidores de FiveM añadiendo nuevas funcionalidades para servidores de rol, realizado con el Lenguaje Lua además de HTML, CSS y JavaScript, aplicando una base de datos MySQL.',
                            link: 'https://forum.cfx.re/t/ox-world-notes-leave-around-notes-shared-within-all-players/5245557?u=lilytz'
                        },
                        {
                            bgImage: img3,
                            title: 'Cable Robbery',
                            text: 'Script realizado en Lua para servidores de FiveM añadiendo nuevas funcionalidades y mejoras, realizado con el Lenguaje Lua además de HTML, CSS y JavaScript, aplicando una base de datos MySQL.',
                            link: 'https://forum.cfx.re/t/cable-robbery-fivem-script-ox-qbcore-esx/5249747?u=lilytz'
                        },
                ]
            }
        },
        methods: {
            handleResize() {
                this.isMobile = window.innerWidth <= 1024;
            }
        },
        mounted() {
            window.addEventListener('resize', this.handleResize);
            const options = {
                threshold: 0.5
            };

            const observer = new IntersectionObserver((entries) => {
                entries.forEach(entry => {
                    if (entry.isIntersecting && entry.boundingClientRect.top > 0) {
                        if (entry.target.classList.contains('group-up')) {
                            entry.target.classList.add('animate__animated', 'animate__fadeInDown');
                        }
                    }else{
                        if (entry.target.classList.contains('group-up') && entry.boundingClientRect.top > 0) {
                            entry.target.classList.remove('animate__animated', 'animate__fadeInDown');
                        }
                    }
                });
            }, options);

            observer.observe(this.$refs.groupUp);

        },
        beferoDestroy(){
            window.removeEventListener('resize', this.handleResize);
        }

    }

</script>

<style scoped>

.group-tecnologies{
    width: 100%;
}

.group-up{
    text-align: center;
    h1{
        font-size: 2.5dvw;
        margin-top: 2em;
    }
}

.group-down{
    min-width: 100%;
    display:flex;
    justify-content: center; 
}

.group-down-boxes{
    width: 70dvw;
    height: 30dvw;
    display: block;
}

:root {
  --carousel-transition: 300ms;
  --carousel-opacity-inactive: 0.5;
  --carousel-opacity-active: 1;
  --carousel-opacity-near: 0.5;
}

.carousel__viewport {
  perspective: 2000px;
}

.carousel__track {
  transform-style: preserve-3d;
}

.carousel__slide--sliding {
  transition: opacity var(--carousel-transition),
    transform var(--carousel-transition);
}

.carousel.is-dragging .carousel__slide {
  transition: opacity var(--carousel-transition),
    transform var(--carousel-transition);
}

.carousel__slide {
  opacity: var(--carousel-opacity-inactive);
  transform: translateX(30px) rotateY(-12deg) scale(0.8);
}

.carousel__slide--prev {
  opacity: var(--carousel-opacity-near);
  transform: rotateY(-10deg) scale(0.85);
}

.carousel__slide--active {
  opacity: var(--carousel-opacity-active);
  transform: rotateY(0) scale(1);
}

.carousel__slide--next {
  opacity: var(--carousel-opacity-near);
  transform: rotateY(10deg) scale(0.85);
}

.carousel__slide--next ~ .carousel__slide {
  opacity: var(--carousel-opacity-inactive);
  transform: translateX(-30px) rotateY(12deg) scale(0.8);
}

@media (max-width: 1024px) {

    .group-up h1{
        font-size: 8vw;
    }

    .group-down-boxes {
        width: 90dvw;
        height: auto;
        display: flex;
        flex-direction: column;
        justify-content: center;
        align-items: center;
    }
}

</style>