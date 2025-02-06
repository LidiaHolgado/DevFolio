<template>
    <div class="main-contact" id="Contact">
        <div class="group-title" ref="grouptitle">
            <h1 class="title-h1">Contacto</h1>

        </div>
        <div class="group-contact">
            <a class="group-left" ref="groupleft" href="mailto:lidiaholgadodev@gmail.com">
                <div class="group-email-video">
                    <h1>Email</h1>
                    <video src="../../assets/Animation.webm" autoplay loop muted></video>
                </div>
                <p>lidiaholgadodev@gmail.com</p>
            </a>
            <a  class="group-right" ref="groupright" href="https://g.co/kgs/F1XY5Nn" target="_blank">
                <div class="group-ubi-video">
                    <h1>Ubicación</h1>
                    <video src="../../assets/AnimationUbi.webm" autoplay loop muted></video>
                </div>
                <p>Sevilla, Andalucia, España</p>
            </a>
        </div>
    </div>
</template>

<script>
import 'animate.css'

export default{
    mounted() {
        const options = {
            threshold: 0.1
        };

        const observer = new IntersectionObserver((entries) => {
            entries.forEach(entry => {
                if (entry.isIntersecting) {
                    if (entry.target.classList.contains('group-left')) {
                        entry.target.classList.add('animate__animated', 'animate__rotateInDownLeft');
                    } else if (entry.target.classList.contains('group-right')) {
                        entry.target.classList.add('animate__animated', 'animate__rotateInDownRight');
                    }else if(entry.target.classList.contains('group-title')){
                        entry.target.classList.add('animate__animated', 'animate__fadeInDown');
                    }
                } else {

                        if (entry.target.classList.contains('group-left')) {
                            entry.target.classList.remove('animate__animated', 'animate__rotateInDownLeft');
                        } else if (entry.target.classList.contains('group-right')) {
                            entry.target.classList.remove('animate__animated', 'animate__rotateInDownRight');
                        }else if(entry.target.classList.contains('group-title')){
                            entry.target.classList.remove('animate__animated', 'animate__fadeInDown');
                        }
                    
                }
            });
        }, options);

        observer.observe(this.$refs.groupleft);
        observer.observe(this.$refs.groupright);
        observer.observe(this.$refs.grouptitle);
    }
}

</script>

<style scoped>


    .main-contact{
        display: flex;
        flex-direction: column;
        align-items: center;
        width: 100%;

        p{
            color: #0e0e0e;
        }
        
    }
    .group-title{
        display: flex;
        justify-content: center;
        align-items: center;
        flex-direction: column;
        width: 100%;
        margin-bottom: 5vw;
    }


    .title-h1{
        font-family: Roboto;
        font-size: 2.5dvw;
    }

    .group-text h1{
        font-size: 1.5dvw;
    }

    .group-contact{
        display: flex;
        justify-content:space-around;
        align-items: center;
        width: 100%;


    }

    .group-left{

        width: 30vw;
        height: 20vw;
        border-radius: 3vw;
        border: 0.15vw solid #0e0e0e;
        background-color: #f5f3ef;

        display: flex;
        flex-direction:column;
        justify-content: center;
        align-items: center;

        cursor: pointer;
        text-decoration: none;
    }


    .group-email-video{
        display: flex;
        flex-direction: row;
        justify-content: center;
        align-items: center;
    }

    .group-left:hover{
    transform: scale(1.05);
    box-shadow: 0.3dvw 0.3dvw 0dvw 0.1dvw #494949;
    transition: 0.5s;
    }
    
    .group-right{
        width: 30vw;
        height: 20vw;
        border-radius: 3vw;
        border: 0.15vw solid #0e0e0e;
        background-color: #f5f3ef;

        display: flex;
        flex-direction:column;
        justify-content: center;
        align-items: center;

        cursor: pointer;
        text-decoration: none;
    }

    .group-ubi-video{
        display: flex;
        flex-direction: row;
        justify-content: center;
        align-items: center;
    }

    .group-right:hover{
        transform: scale(1.05);
        box-shadow: 0.3dvw 0.3dvw 0dvw 0.1dvw #494949;
        transition: 0.5s;
    }

    .group-right h1, .group-left h1{
        font-family:Caveat;
        color: #78c2a7;
        font-size: 3dvw;
    }

    .group-right p, .group-left p{
        font-family: Roboto;
        font-size: 1.5dvw;
    }
    video{
        width: 10vw;
        height: 10vw;
    }

    /*-------Version Movil--------- */

    @media(max-width:1024px){

        .group-title{
            margin-top: 10vw;
            margin-bottom: 10vw;
        }

        .title-h1{
            font-family: Roboto;
            font-size: 8vw;
        }

        .group-contact{
            display: flex;
            flex-direction: column;
            justify-content: center;
            align-items: center;
        }

        .group-left, .group-right{
            width: 70vw;
            height: 40vw;
            margin: 5vw 0;
        }

        .group-right h1, .group-left h1{
            font-size: 8vw;
        }

        .group-right p, .group-left p{
            font-size: 4vw;
        }

        video{
            width: 20vw;
            height: 20vw;
        }
        
    }
    
</style>