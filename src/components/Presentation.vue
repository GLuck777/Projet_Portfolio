<script setup>
    import { ref } from 'vue'


    import TitreNiveau2 from './TitreNiveau2.vue';
    import Courses from '@/components/Courses.vue';
    import Experiences from '@/components/Experiences.vue';
    import Skills from '@/components/Skills.vue';
import Technologiques from './technologiques.vue';

    
  const presentationFilter = ref( 'courses' )
</script>

<template>
    <div id="about">
        <div class="presentation">
            <div class="presentation__text">
                <TitreNiveau2>Présentation</TitreNiveau2>
                <h3>Développeur Fullstack passionné par l'apprentissage et l'innovation</h3>
                <p>Curieux et motivé, je me suis lancé récemment dans le développement web Fullstack, avec une volonté constante d'apprendre et d'évoluer, aussi bien côté front-end que back-end.</p>
                <p>Mon parcours m'a permis de me forger une base solide en HTML, CSS et JavaScript, tout en explorant des langages plus techniques comme Go, Rust ou encore C#.</p>
                <p>Ce portfolio reflète ma passion pour le code, ma capacité à monter en compétence rapidement, et mon envie de créer des solutions modernes, performantes et bien pensées.</p>
                <p>Si vous avez un projet en tête ou des besoins techniques à concrétiser, je serais ravi d'en discuter avec vous. N'hésitez pas à me contacter, je suis ouvert à toute opportunité ou collaboration.</p>
                <router-link class="CTA" :to="{hash:'#contact'}">Me contacter</router-link>
            </div>
        
            <img src="@/assets/images/jeremy_pelage.jpg" alt="Photo de jeremy">
        </div>
    
        <div class="about__filter">
            <button class="about__filter__button CTA" @click="presentationFilter='courses'">Parcours</button>
            <button class="about__filter__button CTA" @click="presentationFilter='experiences'">Expériences</button>
            <button class="about__filter__button CTA" @click="presentationFilter='skills'">Compétences</button>  
            <button class="about__filter__button CTA" @click="presentationFilter='technologiques'">Technologiques</button>  
        </div>
    
        <div class="about__content">
            <Courses v-if="presentationFilter === 'courses' "/>
        
            <Experiences v-if="presentationFilter === 'experiences' "/>
        
            <Skills v-if="presentationFilter === 'skills' "/>
            
            <Technologiques v-if="presentationFilter === 'technologiques' "/>
        </div>
    </div>
</template>

<style scoped>
    .presentation {
        /* background-color: #EFFAFD; */
        background-color: #4651f0bd;
        display: flex;
        padding: 10px 10%;
        gap : 20px;
        align-items: center;
    }

    .presentation__text {
        display: flex;
        flex-direction: column;
        justify-content: center;
        align-items: center;
        gap: 15px;
    }

    .presentation__text p {
        width: 60%;
        text-align: justify;
        text-indent: 5%;
        /* color: #f0e546; */
        color: #eeeeee;
    }

    img {
        width: 25%;
        height: 25%;
        border-radius: 50%;
        box-shadow: -4px 5px 25px #060640;
    }

    .about__filter {
        display: flex;
        gap: 15px;
        margin: 15px 0;
        justify-content: center;
    }

    .about__content {
        margin-bottom: 15px;
        margin-bottom: 2em;
    }

    @media screen and (max-width: 480px) {
        .presentation {
            flex-direction: column-reverse;
            padding: 10px 0;
        }
        .presentation__text p {
            width: 85%;
        }
        img {
            width: 50%;
        }
    }
</style>