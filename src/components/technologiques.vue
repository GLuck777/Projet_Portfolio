<template>
    <div class="languages-page">
      <h1>Mes Compétences en Langages de Programmation</h1>
  
      <section class="languages-section">
        <h2>Front-end</h2>
        <div class="language" v-for="(language, index) in frontEndLanguages" :key="index">
          <h3 @click="toggleDetails(index, 'front')">{{ language.name }}</h3>
          <p v-if="language.showDetails">{{ language.description }}</p>
        </div>
      </section>
  
      <section class="languages-section">
        <h2>Back-end</h2>
        <div class="language" v-for="(language, index) in backEndLanguages" :key="index">
          <h3 @click="toggleDetails(index, 'back')">{{ language.name }}</h3>
          <p v-if="language.showDetails">{{ language.description }}</p>
        </div>
      </section>
    </div>
  </template>
  
  <script lang="ts">
  import { defineComponent, ref } from 'vue';
  
  export default defineComponent({
    setup() {
      const frontEndLanguages = ref([
        {
          name: "HTML",
          description: "Utilisé pour structurer le contenu des pages web.",
          showDetails: true,
        },
        {
          name: "CSS",
          description: "Permet de styliser et de mettre en forme les pages web.",
          showDetails: true,
        },
        {
          name: "JavaScript",
          description: "Langage de programmation essentiel pour rendre les pages interactives.",
          showDetails: true,
        },
      ]);
  
      const backEndLanguages = ref([
        {
          name: "Node.js (JavaScript)",
          description: "Utilisé côté serveur pour exécuter JavaScript et construire des API et des applications serveur performantes.",
          showDetails: true,
        },
        {
          name: "Python",
          description: "Langage polyvalent souvent employé avec Django ou Flask pour créer des applications web et automatiser des tâches.",
          showDetails: true,
        },
        {
          name: "Go (Golang)",
          description: "Langage rapide et efficace, idéal pour construire des microservices et des API scalables.",
          showDetails: true,
        },
        {
          name: "Rust",
          description: "Axé sur la sécurité et la performance, utilisé pour les applications à forte charge nécessitant une gestion fine de la mémoire.",
          showDetails: true,
        },
        {
          name: "C#",
          description: "Utilisé avec .NET pour construire des applications web, des API, et des services cloud robustes.",
          showDetails: true,
        },
        {
          name: "PHP",
          description: "Langage côté serveur populaire pour créer des applications web dynamiques, des API REST et des sites interactifs.",
          showDetails: true,
        },
      ]);
  
      const toggleDetails = (index: number, section: string) => {
        if (section === "front") {
          frontEndLanguages.value[index].showDetails = !frontEndLanguages.value[index].showDetails;
        } else if (section === "back") {
          backEndLanguages.value[index].showDetails = !backEndLanguages.value[index].showDetails;
        }
      };
  
      return {
        frontEndLanguages,
        backEndLanguages,
        toggleDetails,
      };
    },
  });
  </script>
  
  <style scoped>
  .languages-page {
    max-width: 800px;
    margin: auto;
    padding: 20px;
    font-family: Arial, sans-serif;
  }
  
  .languages-section {
    margin-bottom: 20px;
  }
  
  .language h3 {
    cursor: pointer;
    color: #007acc;
    transition: color 0.2s;
  }
  
  .language h3:hover {
    color: #005f99;
  }
  
  .language p {
    margin: 10px 0;
    padding-left: 10px;
    color: #333;
  }
  </style>
  