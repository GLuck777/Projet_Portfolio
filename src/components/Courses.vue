<script setup>
    import TitreNiveau2 from './TitreNiveau2.vue';
//preparation de niveau 6 concepteur developpeur d'application bac +3 RNCP37873
// Mon cursus exacte formation de 3 an formation initial + alternance 3 année en alternance 3 semaine entreprises 1 semaine ecole 
    const parcours = {
        annee1: {
            ecole: 'Sacrée Coeur',
            date: '2014 - 2015',
            title: 'Bac STMG Gestion-Finance',
            comment: 'Validation année 1.' //Technologies : HTML - CSS - Java - Python
        },
        annee2: {
            ecole: 'ESC Clermont',
            date: '2017 - 2020',
            title: 'Master 2 en Management', //(interrompu en dernière années)
            comment: "Diplôme d'Etudes Supérieures en Commerce et Management Opérationnel - Responsable événementiel au sein de l’association ESC Clermont."
        },
        annee3: {
            ecole: 'ID Formation - Centre SER',
            date: '2021 - 2022',
            title: 'Titre professionnel : Développement web et web mobile Diplôme BAC+2',
            comment: 'Master 1 - Management des ventes et de la marque.'
        },
        annee4: {
            ecole: 'Zone01',
            date : 'Mai 2023 - Mai 2025',
            title: 'Concepteur développeur d\'application bac+3 RNCP37873',
            comment: 'Technologies : HTML - CSS - JavaScript - Vue.Js - Git/GitHub - Rust - React.js - Go - Angular - SQL / MySQL - Django - Node.js - PHP'
        }
    }
</script>

<template>
    <div class="courses">
        <div class="courses__title">
            <span class="material-symbols-outlined">school</span><br>
            <TitreNiveau2>Mon parcours</TitreNiveau2>
        </div>
    
        <div class="parcours">
            <div class="ecole" v-for="annee in parcours">
                <h3 class="ecole__title">{{ annee.ecole }}</h3>
                <h4 class="ecole__info">{{ annee.title }} <span class="separation">|</span> {{ annee.date }}</h4>
                <p class="ecole__comment">{{ annee.comment }}</p>
            </div>
        </div>
    </div>
</template>

<style scoped>
    .courses {
        width: 60%;
        display: flex;
        flex-direction: column;
        align-items: center;
        margin: auto;
    }

    .courses__title {
        text-align: center;
    }

    .material-symbols-outlined {
        font-size: 4em;
    }

    .ecole__title {
        font-size: 1.25em;
    }

    .ecole__info {
        font-size: 1.05em;
    }

    .separation {
        font-style: italic;
        color: #A0006D;
    }

    .ecole__comment {
        text-indent: 2em;
        text-align: justify;
    }

    .parcours {
        margin-top: 15px;
        display: flex;
        flex-direction: column-reverse;
        gap: 25px;
    }

    .ecole {
        padding: 15px;
        /* background-color: #EFFAFD; */
        background-color: #4651f0bd;
        border-radius: 25px;
        box-shadow: -4px 5px 10px #060640;
    }

    @media screen and (max-width: 480px) {
        .courses {
            width: 85%;
        }
    }
</style>