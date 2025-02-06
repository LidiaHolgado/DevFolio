<template>
    <div class="group-tecnologies" id="Technologies" ref="groupTecnologies">
        <div class="group-up" ref="groupUp">
            <h1>Tecnologías</h1>
        </div>
        <div class="technologies-menu" ref="technologiesMenu">
            <button class="menu-button" id="frontend" @click="type = 'frontend'" :class="{active: type === 'frontend'}">Frontend</button>
            <button class="menu-button" id="backend" @click="type = 'backend'" :class="{active: type === 'backend'}">Backend</button>
            <button class="menu-button" id="bbdd" @click="type = 'bbdd'" :class="{active: type === 'bbdd'}">BBDD</button>
            <button class="menu-button" id="version" @click="type = 'version'" :class="{active: type === 'version'}">Control de versiones</button>
            <button class="menu-button" id="testing" @click="type = 'testing'" :class="{active: type === 'testing'}">Testing</button>
            <button class="menu-button" id="ide" @click="type = 'ide'" :class="{ active: type === 'ide' }">IDE</button>
        </div>
        <div class="group-down">
            <transition name="fade" mode="out-in">
                <div key="frontend" v-if="type === 'frontend'" class="group-down-boxes">
                    <TecnologiesBox v-for="(img, index) in frontendImgs" :key="index" :ref="'frontendBox' + index" :img="img.src" :title="img.title"></TecnologiesBox>
                </div>
                <div key="backend" v-else-if="type === 'backend'" class="group-down-boxes">
                    <TecnologiesBox v-for="(img, index) in backendImgs" :key="index" :ref="'backendBox' + index" :img="img.src" :title="img.title"></TecnologiesBox>
                </div>
                <div key="bbdd" v-else-if="type === 'bbdd'" class="group-down-boxes">
                    <TecnologiesBox v-for="(img, index) in bbddImgs" :key="index" :ref="'bbddBox' + index" :img="img.src" :title="img.title"></TecnologiesBox>
                </div>
                <div key="version" v-else-if="type === 'version'" class="group-down-boxes">
                    <TecnologiesBox v-for="(img, index) in versionImgs" :key="index" :ref="'versionBox' + index" :img="img.src" :title="img.title"></TecnologiesBox>
                </div>
                <div key="testing" v-else-if="type === 'testing'" class="group-down-boxes">
                    <TecnologiesBox v-for="(img, index) in testingImgs" :key="index" :ref="'testingBox' + index" :img="img.src" :title="img.title"></TecnologiesBox>
                </div>
                <div key="ide" v-else-if="type === 'ide'" class="group-down-boxes">
                    <TecnologiesBox v-for="(img, index) in ideImgs" :key="index" :ref="'ideBox' + index" :img="img.src" :title="img.title"></TecnologiesBox>
                </div>
            </transition>
        </div>
    </div>
</template>

<script>
import TecnologiesBox from '../TecnologiesBox.vue';
import 'animate.css';

export default {
    name: 'App',
    components: {
        TecnologiesBox,
    },
    data() {
        return {
            type: 'frontend',
            frontendImgs: [
                { src: require('../../assets/icons/frontend/icons8-html-5.svg'), title: 'HTML' },
                { src: require('../../assets/icons/frontend/icons8-css.svg'), title: 'CSS' },
                { src: require('../../assets/icons/frontend/icons8-javascript.svg'), title: 'JavaScript' },
                { src: require('../../assets/icons/frontend/icons8-vuejs.svg'), title: 'Vue.js' },
                { src: require('../../assets/icons/frontend/icons8-reaccionar-nativo.svg'), title: 'React' },
                { src: require('../../assets/icons/frontend/icons8-oreja.svg'), title: 'Boostrap' },
            ],
            backendImgs: [
                { src: require('../../assets/icons/backend/icons8-java.svg'), title: 'Java' },
                { src: require('../../assets/icons/backend/icons8-python.svg'), title: 'Python' },
                { src: require('../../assets/icons/backend/icons8-php.png'), title: 'PHP' },
                { src: require('../../assets/icons/backend/icons8-springboot.svg'), title: 'Spring Boot' },
                { src: require('../../assets/icons/backend/lua.svg'), title: 'Lua' },

            ],
            bbddImgs: [
                { src: require('../../assets/icons/bbdd/icons8-mysl.png'), title: 'MySQL' },
                { src: require('../../assets/icons/bbdd/icons8-mongodb.png'), title: 'MongoDB' },
            ],
            versionImgs: [
                { src: require('../../assets/icons/version/icons8-jira.svg'), title: 'Jira' },
                { src: require('../../assets/icons/version/icons8-git.svg'), title: 'Git' },
            ],
            testingImgs: [
                { src: require('../../assets/icons/testing/jenkins.png'), title: 'Jenkings' },
                { src: require('../../assets/icons/testing/jmeter.svg'), title: 'JMeter' },
                { src: require('../../assets/icons/testing/sonarqube.svg'), title: 'SonarQube' },
            ],
            ideImgs: [
                { src: require('../../assets/icons/ide/icons8-estudio-visual.svg'), title: 'Visual Studio Code' },
                { src: require('../../assets/icons/ide/icons8-intellij-idea.svg'), title: 'IntelliJ IDEA' },
                { src: require('../../assets/icons/ide/icons8-eclipse.svg'), title: 'Eclipse' },
            ],
        };
    },
    mounted() {
        let lastScrollTop = 0;
        const observer = new IntersectionObserver((entries) => {
            entries.forEach(entry => {
                let scrollTop = window.scrollY || document.documentElement.scrollTop;
                if (entry.isIntersecting && scrollTop > lastScrollTop) {
                    this.animateTecnologiesBoxes();
                    this.animateGroupUpAndMenu();
                } else if (!entry.isIntersecting) {
                    this.resetTecnologiesBoxes();
                    this.resetGroupUpAndMenu();
                }
                lastScrollTop = scrollTop <= 0 ? 0 : scrollTop;
            });
        });

        this.$nextTick(() => {
            observer.observe(this.$refs.groupTecnologies);
        });
    },
    methods: {
        animateTecnologiesBoxes() {
            Object.keys(this.$refs).forEach(refKey => {
                if (Array.isArray(this.$refs[refKey])) {
                    this.$refs[refKey].forEach(box => {
                        box.$el.classList.add('animate__animated', 'animate__zoomIn');
                    });
                }
            });
        },
        resetTecnologiesBoxes() {
            Object.keys(this.$refs).forEach(refKey => {
                if (Array.isArray(this.$refs[refKey])) {
                    this.$refs[refKey].forEach(box => {
                        box.$el.classList.remove('animate__animated', 'animate__zoomIn');
                    });
                }
            });
        },
        animateGroupUpAndMenu() {
            if (this.$refs.groupUp) {
                this.$refs.groupUp.classList.add('animate__animated', 'animate__fadeInDown');
            }
            if (this.$refs.technologiesMenu) {
                this.$refs.technologiesMenu.classList.add('animate__animated', 'animate__fadeInDown');
            }
        },
        resetGroupUpAndMenu() {
            if (this.$refs.groupUp) {
                this.$refs.groupUp.classList.remove('animate__animated', 'animate__fadeInDown');
            }
            if (this.$refs.technologiesMenu) {
                this.$refs.technologiesMenu.classList.remove('animate__animated', 'animate__fadeInDown');
            }
        }
    }
}
</script>

<style scoped>

.group-tecnologies {
    font-family: Roboto;
    display: flex;
    flex-direction: column;
    align-items: center;
    width: 100%;
    background-color: #faf3e1;
}
.fade-enter-active, .fade-leave-active {
    transition: opacity 0.3s;
}
.fade-enter, .fade-leave-to {
    opacity: 0;
}
.group-up h1 {
    font-size: 2.5dvw;
}
.group-down {
    width: 60%;
    display: flex;
    justify-content: center;
    align-items: center;
    margin-top: 4dvw;
}
.group-down-boxes {
    display: flex;
    justify-content: center;
    align-items: center;
    flex-wrap: wrap;
    gap: 3em;
}
.technologies-menu {
    display: flex;
    justify-content: center;
    align-items: center;
    gap: 1em;
    margin-top: 2em;
    flex-wrap: wrap;
}
.menu-button {
    width: 8dvw;
    height: 2dvw;
    border-radius: 0.3dvw;
    font-size: 0.7dvw;
    cursor: pointer;    
    border: 1.8px solid #0e0e0e;
    box-shadow: 1px 1px 0px 1px #0e0e0e;
}
#frontend {
    background-color: #FF9AA2;
}
#backend {
    background-color: #FFB7B2;
}
#bbdd {
    background-color: #FFDAC1;
}
#version {
    background-color: #E2F0CB;
}
#testing {
    background-color: #B5EAD7;
}
#ide {
    background-color: #C7CEEA;
}
.menu-button.active#frontend,
.menu-button.active#backend,
.menu-button.active#bbdd,
.menu-button.active#version,
.menu-button.active#testing,
.menu-button.active#ide {
    background-color: #fdf9f8; /* Color más oscuro para el botón activo */
}
/*---------Version Movil---------- */
@media (max-width: 1024px) {
    .group-up h1 {
        font-size: 8vw;
    }
    .menu-button {
        width: 20dvw;
        height: 8dvw;
        font-size: 3dvw;
    }
    .technologies-menu {
        flex-wrap: wrap;
    }
    .group-down {
        width: 60%;
        display: flex;
        justify-content: center;
        align-items: center;
        margin-top: 15dvw;
    }
}
</style>