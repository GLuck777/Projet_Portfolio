<script setup>
    import TitreNiveau2 from './TitreNiveau2.vue';
//’
    const parcours = {
        // annee1: {
        //     entreprise: 'Groupe Esprit Jardin',
        //     date: 'Mars 2021 - Mai 2021',
        //     title: 'Assistant chargé gestion de projet - Stage 3 mois',
        //     comment: "Missions : Gestion de l'implantation d'une nouvelle gamme de produit ; Réalisation d'une veille concurrentielle ; Élaboration d'un questionnaire satisfaction client ; Réception de commande ; Service clients."
        // },
        annee2: {
            entreprise: 'ESC Clermont',
            date: '2018 - 2018',
            title: 'Chargé de taches',
            comment: "Missions : Création d'un questionnaire pour l'expérience Gestion d'ateliers et récupération des informations de suivi."
        },
        annee3: {
            entreprise: 'Delegation Regionale EDF',
            date: '2020 - 2020',
            title: 'Chargé de communication - Stage 6 mois',
            comment: "Missions : Réception de la clientèle ; Création de document officiels confidentiels; Gestion en commun de l'espace de vie et du réapprovisionnement; création d'un logiciel Excel facturation"
        },
        annee4: {
            entreprise: 'La ferme linguistique',
            date: 'Janvier 2025 - à Mars 2025',
            title: 'Développeur FullStack - Stage 2 mois',
            comment: "Missions : Conception et refonte de page sur le site principal; \nCréation d'une page Statistique : Extraction de données en PHP pour leur exploitation dynamique en JavaScript (tableaux interactifs, graphiques via canvas, analyses statistiques). \nModification de la page de Communication : Optimisation de la gestion des données (récupération, modification dynamique) et implémentation du système d\'envoi de mails."
        },
    }
</script>

<template>
    <div class="experience">
        <div class="experience__title">
            <span class="material-symbols-outlined">work</span><br>
            <TitreNiveau2>Mes expériences professionnelles</TitreNiveau2>
        </div>
    
        <div class="annee">
            <div class="job" v-for="annee in parcours">
                <h3 class="job__title">{{ annee.entreprise }}</h3>
                <h4 class="job__info">{{ annee.title }} <span class="separation">|</span> {{ annee.date }}</h4>
                <p class="job__comment">{{ annee.comment }}</p>
            </div>
        </div>
    </div>
</template>

<style scoped>
    .experience {
        width: 60%;
        display: flex;
        flex-direction: column;
        align-items: center;
        margin: auto;
    }

    .experience__title {
        text-align: center;
    }

    .material-symbols-outlined {
        font-size: 4em;
    }

    .job__title {
        font-size: 1.25em;
    }

    .job__info {
        font-size: 1.05em;
    }

    .separation {
        font-style: italic;
        color: #A0006D;
    }

    .job__comment {
        text-indent: 2em;
        text-align: justify;
    }

    .annee {
        margin-top: 15px;
        display: flex;
        flex-direction: column-reverse;
        gap: 25px;
    }

    .job {
        padding: 15px;
        /* background-color: #EFFAFD; */
        background-color: #4651f0bd;
        border-radius: 25px;
        box-shadow: -4px 5px 10px #060640;
    }

    @media screen and (max-width: 480px) {
        .experience {
            width: 85%;
        }
    }
</style>