<script setup>
    import { ref } from 'vue'


    import TitreNiveau2 from './TitreNiveau2.vue';
    import Courses from '@/components/Courses.vue';
    import Experiences from '@/components/Experiences.vue';
    import Skills from '@/components/Skills.vue';
import Techniques from './techniques.vue';

    
  const presentationFilter = ref( 'courses' )
</script>

<template>
    <div id="about">
        <div class="presentation">
            <div class="presentation__text">
                <TitreNiveau2>Présentation</TitreNiveau2>
                <p>Je suis Jeremy Pélage, passionné par le développement Fullstack. En tant que développeur Fullstack recemment sur le marché, je suis motivé et curieux d'apprendre de nouveaux langages, aussi bien en front qu'en back end. <br>
                    Bien que mon expérience soit récente, j'ai acquis des compétences solides en HTML, CSS, JavaScript, ainsi qu'en Go, Rust, et C#. <br>
                    Ce portfolio présente quelques exemples de mes projets, illustrant ma passion pour le développement Fullstack et mon aptitude à maîtriser rapidement de nouvelles technologies. <br>
                    Je serais ravi de discuter de vos besoins et de voir comment je peux contribuer à vos projets web. N'hésitez pas à me contacter pour en savoir plus ou pour toute question.</p>
                <router-link class="CTA" :to="{hash:'#contact'}">Me contacter</router-link>
            </div>
        
            <img src="@/assets/images/jeremy_pelage.jpg" alt="Photo de jeremy">
        </div>
    
        <div class="about__filter">
            <button class="about__filter__button CTA" @click="presentationFilter='courses'">Parcours</button>
            <button class="about__filter__button CTA" @click="presentationFilter='experiences'">Expériences</button>
            <button class="about__filter__button CTA" @click="presentationFilter='skills'">Compétences</button>  
            <button class="about__filter__button CTA" @click="presentationFilter='techniques'">Techniques</button>  
        </div>
    
        <div class="about__content">
            <Courses v-if="presentationFilter === 'courses' "/>
        
            <Experiences v-if="presentationFilter === 'experiences' "/>
        
            <Skills v-if="presentationFilter === 'skills' "/>
            
            <Techniques v-if="presentationFilter === 'techniques' "/>
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