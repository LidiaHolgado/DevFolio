<template>
    <div class="group-description" id="AboutMe">
            <div class="group-left">
                <img ref="groupLeft" src="../../assets/aboutmeImg.webp" alt="Imagen About Me">  
            </div>
            <div class="group-right">
                <div class="group-up" ref="groupUp">
                    <h1>Sobre mi</h1>
                </div>
                <div class="group-down" ref="groupDown">
                    <div class="group-down-text">
                        <p>Soy Lidia Holgado Romero, actualmente he terminado el Grado Superior de Desarrollo de Aplicaciones Web en Medac Sevilla, con el propósito de consolidar mi carrera como desarrolladora web.</p>
                        <p>Cuento con una titulación previa como Técnico Superior en Animaciones 3D, Juegos y Entornos Interactivos, lo que ha proporcionado una base sólida para mi formación. Además, he complementado mi aprendizaje con diversos cursos autodidactas a través de plataformas como Udemy, OpenBootCamp y OpenWebinars.</p>
                        <p>Soy una persona apasionada por la informática, con un enfoque específico en el desarrollo web. Mi motivación principal es alcanzar metas y objetivos profesionales que me permitan crecer y desarrollarme en este campo.</p>
                        <p>Mi interés y entusiasmo se centran especialmente en el ámbito de la web development, donde aspiro a aplicar mis habilidades y conocimientos de manera creativa. Estoy ansiosa por encontrar oportunidades laborales que me permitan contribuir al mundo digital y seguir evolucionando en mi carrera profesional.</p>
                    </div>
                </div>
            </div>
    </div>
</template>

<script>
import 'animate.css';
export default {
    mounted() {
        let lastScrollTop = 0;
        const observer = new IntersectionObserver((entries) => {
            entries.forEach(entry => {
                let scrollTop = window.scrollY || document.documentElement.scrollTop;
                if (entry.isIntersecting && scrollTop > lastScrollTop) {
                    if (entry.target === this.$refs.groupLeft) {
                        entry.target.classList.add('animate__animated', 'animate__fadeInLeft');
                    } else if (entry.target === this.$refs.groupUp) {
                        entry.target.classList.add('animate__animated', 'animate__fadeInDown', 'animate__slow');
                    } else if (entry.target === this.$refs.groupDown) {
                        entry.target.classList.add('animate__animated', 'animate__fadeIn', 'animate__slow');
                    }
                } else if (!entry.isIntersecting) {
                    if (entry.target === this.$refs.groupLeft) {
                        entry.target.classList.remove('animate__animated', 'animate__fadeInLeft');
                    } else if (entry.target === this.$refs.groupUp) {
                        entry.target.classList.remove('animate__animated', 'animate__fadeInDown', 'animate__slow');
                    } else if (entry.target === this.$refs.groupDown) {
                        entry.target.classList.remove('animate__animated', 'animate__fadeIn', 'animate__slow');
                    }
                }
                lastScrollTop = scrollTop <= 0 ? 0 : scrollTop;
            });
        });

        observer.observe(this.$refs.groupLeft);
        observer.observe(this.$refs.groupUp);
        observer.observe(this.$refs.groupDown);
    }
}
</script>

<style scoped>
    .group-description{
        font-family: Roboto;
        display: grid;
        grid-template-columns: 1fr 1fr;
        width: 100%;
    }
    .group-left{
        display: flex;
        flex-direction:column;
        justify-content: center;
        align-items: center;
        background-color: #faf3e1;

        img{
            width: 70%;
            border-radius: 1em;
        }
    }

    .group-right{
        display: flex;
        flex-direction:column;
        justify-content: center;
        align-items: center;

    }
    .group-up{
        h1{
            font-size: 2dvw;
            margin: 0;
        }
    }

    .group-down{
        font-size: 1dvw;
        margin-top: 3em;
        width: 60%;
    }


    @media (max-width: 1024px) {
        .group-description{
            display: flex;
            flex-direction: column;

        }
        .group-left {
            width: 100%;
            height: 40vw;
            margin: 0;
            
            img{
                height: 90%;
                width: 80%;
                border-radius: 1em;
                object-fit: cover;
                object-position: center;
            }
        }

        .group-up{
        h1{
            font-size: 8vw;
            margin: 0;
        }
    }

        .group-down{
            font-size: 3vw;
            text-align: center;

        }

    }

</style>