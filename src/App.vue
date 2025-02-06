<template>
  <NavBar/>
  <CustomSection>
    <Intro/>
  </CustomSection>
  <CustomSection>
    <AboutMe/>
  </CustomSection>
  <CustomSection>
    <Experience/>
  </CustomSection>
  <CustomSection>
    <Technologies/>
  </CustomSection>
  <CustomSection>
    <Projects/>
  </CustomSection>
  <CustomSection>
    <Contact/>
  </CustomSection>
  <FinalFooter/>
</template>

<script>
import NavBar from './components/NavBar.vue';
import CustomSection from './components/CustomSection.vue';
import Intro from './components/sections/Intro.vue';
import AboutMe from './components/sections/AboutMe.vue';
import Technologies from './components/sections/Technologies.vue';
import Projects from './components/sections/Projects.vue';
import Contact from './components/sections/Contact.vue';
import FinalFooter from './components/FinalFooter.vue';
import Experience from './components/sections/Experience.vue';

export default {
  name: 'App',
  components: {
    NavBar,
    CustomSection,
    Intro,
    AboutMe,
    Technologies,
    Projects,
    Contact,
    Experience,
    FinalFooter,
  }
}
</script>

<style>
@import url('https://fonts.googleapis.com/css2?family=Roboto:ital,wght@0,100;0,300;0,400;0,500;0,700;0,900;1,100;1,300;1,400;1,500;1,700;1,900&display=swap');
@import url('https://fonts.googleapis.com/css2?family=Caveat:wght@400..700&family=Roboto:ital,wght@0,100;0,300;0,400;0,500;0,700;0,900;1,100;1,300;1,400;1,500;1,700;1,900&display=swap');
  html{
    scroll-behavior: smooth;
    scroll-padding: 10vh;
  }
  body{
    font-family: Roboto;
    color: rgb(39, 39, 39);
    margin: 0;
    padding: 0;
    font-family: Arial, sans-serif;
    section:first-of-type{
      padding-top: 10vh;
    }
  }

  :root{
    --vc-nav-height: 3vw;
    --vc-nav-width: 2vw;
  }

  .carousel__next, .carousel__prev{
    transform: translateY(0);
  }
</style>
