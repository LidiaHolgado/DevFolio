<template>
    <div class="group" id="Intro">
        <div class="group-left">
            <h1 class="typewriter" data-text="&lt;Lidia Holgado Romero/&gt;"> </h1>
            <h3 class="typewriter-placeholder color-h3" data-text="Web Developer"></h3>
            <div class="rrss">
              <a href="#"  @click="downloadCV" class="download-button hidden"> Descargar CV</a>
              <a href="https://github.com/LidiaHolgado" target="_blank"><img src="../../assets/icons/rrss/icons8-github.svg" alt="Github" class="hidden"></a>
              <a href="https://www.linkedin.com/in/lidiaholgadoromero/" target="_blank"><img src="../../assets/icons/rrss/icons8-linkedin.svg" alt="Linkedin" class="hidden"></a>
            </div>
        </div>
        <div class="group-right">
            <img  src="../../assets/imgperfil.png" class="animate__animated animate__fadeIn animate_slower animate__delay-1s" >
        </div>
    </div>
</template>

<script>
import 'animate.css'
export default {
  mounted() {
    const typewriterElements = document.querySelectorAll('.typewriter, .typewriter-placeholder');
    let currentElementIndex = 0;
    let i = 0;
    const speed = 100; // Velocidad de escritura en milisegundos

    function typeWriterEffect() {
      const currentElement = typewriterElements[currentElementIndex];
      const text = currentElement.getAttribute('data-text');
      currentElement.textContent = '';
      currentElement.style.visibility = 'visible'; // Asegúrate de que el h3 sea visible

      function type() {
        if (i < text.length) {
          currentElement.textContent = text.substring(0, i + 1);
          i++;
          setTimeout(type, speed);
        } else {
          currentElement.classList.remove('typewriter'); // Eliminar cursor fijo al terminar de escribir
          if (currentElementIndex === 0) {
            currentElementIndex++;
            i = 0;
            const nextElement = typewriterElements[currentElementIndex];
            nextElement.classList.add('typewriter'); // Añadir cursor fijo al h3
            nextElement.classList.remove('typewriter-placeholder'); // Eliminar placeholder
            setTimeout(typeWriterEffect, 500); // Espera antes de empezar a escribir el siguiente texto
          } else {
            // Mostrar las imágenes con animación
            const images = document.querySelectorAll('.rrss img, .rrss .download-button');
            images.forEach(img => {
              img.classList.remove('hidden');
              img.classList.add('fade-in');
            });
            currentElement.classList.add('blinking-cursor'); // Añadir cursor parpadeante al final del h3
          }
        }
      }
      type();
    }
    typeWriterEffect();
  },
  methods: {
  downloadCV() {
    const link = document.createElement("a");
    link.href = "/cv/LIDIA_HOLGADO_ROMERO_CV.pdf";
    link.setAttribute("download", "LIDIA_HOLGADO_ROMERO_CV.pdf");
    document.body.appendChild(link);
    link.click();
    document.body.removeChild(link);
  }
}
}
</script>

<style scoped>
    .group{
        font-family: Roboto;
        display: grid;
        grid-template-columns: 1fr 1fr;
        width: 100%;
        background-color: #faf3e1;
    }
    .group-left{
        display: flex;
        flex-direction:column;
        justify-content: center;
        align-items: flex-start;
        background-color: #faf3e1;

        h1{
            font-size: 4dvw;
            margin: 0;
            padding-left: 20%;
        }
    
        h3{
            font-size: 2dvw;
            margin: 0;
            padding-left: 20%;
        }
    }

    .group-right{
        display: flex;
        flex-direction:column;
        justify-content: center;
        align-items: center;
        background-color: #faf3e1;
        img{
            width: 90%;

        }
    }


    .rrss{
        display: flex;
        justify-content: center;
        align-items: center;
        margin-top: 2em;
        padding-left: 19%;

        img{
          filter: invert(0%) sepia(0%) saturate(0%) hue-rotate(0deg) brightness(0%) contrast(70%);
          width: 3dvw;

        }
        .download-button {

        padding: 0.8vw 0.8vw;
        font-size: 1vw;
        background-color: #262626;
        color: #faf3e1;
        border: none;
        border-radius: 20px;
        cursor: pointer;
        text-decoration: none;
        }
    }

  .color-h3{
    color: #78c2a7;
  }

    .hidden {
    opacity: 0;
  }

    .fade-in {
      animation: fadeIn 2s forwards;
    }

  @keyframes fadeIn {
    from {
      opacity: 0;
    }
    to {
      opacity: 1;
    }
  }
  .typewriter::after {
  content: '|';
  animation: none;
}

  .blinking-cursor::after {
    content: '|';
    animation: blink 1s step-end infinite;
  }

  @keyframes blink {
  from, to {
    opacity: 1;
  }
  50% {
    opacity: 0;
  }
}

.fade-enter-from, .fade-leave-to {
  opacity: 0;
}

.fade-enter-to, .fade-leave-from {
  opacity: 1;
}

.fade-enter-active, .fade-leave-active {
  transition: opacity 0.5s;
}

@media (max-width: 1024px) {

  .group{
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;
  }
  .group-left {
    order: 2;
    width: 100%;
    align-items: center;
    
    h1{
      padding-left: 0;
      font-size: 8vw;
    }
    h3{
      padding-left: 0;
      font-size: 6vw;
    }
  }

  .rrss{
    padding-left: 0;
    margin-top: 1em;
    img{
      width: 10vw;
    }
    .download-button {
    padding: 1vw 2vw;
    font-size: 4vw;
    }
  }
  .group-right {
    order: 1;
  }

}
</style>