<template>
    <div class="final-footer">
        <div class="footer-left">
            <a href="https://github.com/LidiaHolgado" target="_blank"><img src="../assets/icons/rrss/icons8-github.svg" alt="Github"></a>
            <a href="https://www.linkedin.com/in/lidiaholgadoromero/" target="_blank"><img src="../assets/icons/rrss/icons8-linkedin.svg" alt="Linkedin"></a>
        </div>
        <div class="footer-right">
            <h3>Copyright © 2025 LidiaHolgado</h3>
        </div>
    </div>
</template>

<script>
</script>

<style scoped>
    .final-footer{
        font-family: 'Roboto', sans-serif;
        font-size: 1dvw;

        height: 10vh;
        display: flex;
        justify-content: space-between;
        align-items: center;
        background-color: #1a1a1a;

        color: white;
    }

    img{
        width: 2em;
        height: 2em;
        margin: 10px;
    }

    .footer-left{
        margin-left: 2em;
    }

    .footer-right{
        margin-right: 2em;
    }
    

    @media (max-width: 1024px){

        .final-footer{
            font-size: 3dvw;
        }
    }
    
</style>