<template>
    <div class="menu">
        <a href="#Intro">
            <img alt="Logo" src="../assets/logo.svg">
        </a>
        <div class="menu-links">
            <a href="#Intro">Inicio</a>
            <a href="#AboutMe">Descripción</a>
            <a href="#Experience">Experiencia</a>
            <a href="#Technologies">Tecnologías</a>
            <a href="#Projects">Proyectos</a>
        </div>
        
        <a  href="#Contact" class="contact">Contacto</a>
    </div>
    <div class="mobile-menu">
        <a href="#Intro">
            <img alt="Logo" src="../assets/logo.svg" class="mobile-logo">
        </a>
        <button class="menu-button" :class="{ 'open': isMenuOpen }" @click="toggleMenu">
            <div></div>
            <div></div>
            <div></div>
        </button>
        <transition name="fade">       
            <div v-if="isMenuOpen" class="menu-links">
                <a href="#Intro">Inicio</a>
                <a href="#AboutMe">Descripción</a>
                <a href="#Experience">Experiencia</a>
                <a href="#Technologies">Tecnologías</a>
                <a href="#Projects">Proyectos</a>
                <a href="#Contact">Contacto</a>
            </div>
        </transition>
    </div>
</template>
  
<script>
export default {
    data() {
        return {
            isMenuOpen: false
        };
    },
    methods: {
        toggleMenu() {
            this.isMenuOpen = !this.isMenuOpen;
        }
    }
};
</script>
  
  <!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
    .menu{
        font-family: Roboto;
        display: flex;
        position: fixed;
        height: 10vh;
        width: 100dvw;
        justify-content: space-between;
        align-items: center;
        background-color: #faf3e1;
        z-index: 10;
        
    }
    .menu img{
        width: 5dvw;
        margin: 1vw 0 1vw 3vw;
        
    }
    .menu-links a{
        margin: 0 10px;
        text-decoration: none;
        color: #000;
        padding: 5px 12px;
        font-size: 1vw;
        box-sizing: border-box;
        border: 0.1vw solid transparent;
    }
    .menu-links a:hover{
        border-color: #34322c;
        border-radius: 1vw;

    }
    .contact{
        padding: 0.5dvw 1dvw;
        font-size: 1dvw;
        background-color: #34322c;
        color: white;
        border: none;
        border-radius: 20px;
        cursor: pointer;
        margin: 1vw 3vw 1vw 0;
        text-decoration: none;
    }

    /*--------Mobile Menu-------*/
    
    .mobile-menu {
        display: none;
        align-items: center;
        justify-content: space-between;
    }

    .mobile-logo {
        width: 15vw;
        padding-left: 2vw;
    }

    .menu-button{
        display: flex;
        flex-direction: column;
        width: 3rem;
        height: 2rem;
        border: 0;
        background: transparent;
        gap: .65rem;
        margin-right: 2vw;
    }

    .menu-button > div {
        background-color: #000;
        height: 2px;
        width: 100%;
        border-radius: 5px;
        transition: all .5s;
        transform-origin: left;
    }

    .menu-button.open > div:first-child{
        transform: rotate(45deg);
    }

    .menu-button.open > div:nth-child(2){
        opacity: 0;
    }

    .menu-button.open > div:last-child{
        transform: rotate(-45deg);
    }

    .fade-enter-active{
        transition: all .5s ease-out;
    }

    .fade-leave-active{
        transition: all .8s ease;
    }

    .fade-enter-from, .fade-leave-to{
        transform: translateY(-50px);
        opacity: 0;
    }




@media (min-width: 2560px){
    .menu-links a{
        font-size: 1.2vw;
    }
}

@media (max-width: 1024px) {
    .menu {
        display: none;
    }
    .mobile-menu {
        display: flex;
        position: fixed;
        top: 0;
        left: 0;
        right: 0;
        background-color: #faf3e1;
        width: 100vw;
        height: 10vh;
        z-index: 10;
        justify-content: space-between;
        align-items: center;
    }
    .mobile-menu .menu-links {
        display: flex;
        flex-direction: column;
        position: absolute;
        top: 10vh;
        right: 0;
        background-color: #dfd5be;
        width: 30%;
        text-align: left;
        border-radius: 1rem 0 1rem 1rem;
    }
    .mobile-menu .menu-links a {
        padding: 1rem;
        font-size: 3.4vw;
    }

    .menu-links a:hover{
        border-radius: 6vw;
    }

}

        
</style>