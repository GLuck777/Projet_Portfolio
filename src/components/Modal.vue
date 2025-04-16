
<script setup>
    import { ref, computed } from 'vue';
    const props = defineProps(['projet'])
    const baseUrl = import.meta.env.BASE_URL;
    // defineEmits(['close']);

    const selectedImageIndex = ref(-1);

    const images = computed(() => Array.isArray(props.projet.image) ? props.projet.image : []);

    // Fonction pour afficher une image dans la modal__imagebis
    const showImage = (ind) => {
        console.log("showImage:", ind, "facteur", selectedImageIndex);
        if (ind >= 0){
            selectedImageIndex.value = ind;
        }
    };

    // Fonction pour naviguer entre les images
    const prevImage = () => {
        if (selectedImageIndex.value > 0) {
            selectedImageIndex.value--;
        }
    };

    const nextImage = () => {
        if (selectedImageIndex.value < props.projet.image.length - 1) {
            selectedImageIndex.value++;
        }
    };

    // Fonction pour fermer l'image agrandie
    const closeImage = () => {
        selectedImageIndex.value = -1; // null
    };
</script>

<template>
    <div class="modal__background" @click="$emit('close')"></div>
    <div class="modal">
        <span class="material-symbols-outlined" @click="$emit('close')">close</span>
        
        <h3 class="modal__header">{{ projet.name }}</h3>

        <div class="modal__aside">
            <ul class="modal__techno">
                <p v-if="projet.tag.length == 1">Technologie :</p>
                <p v-else-if="projet.tag.length > 1">Technologies :</p>
                <p></p>
                <li v-for="i in projet.tag">{{ i }}</li>
            </ul>
            <p>Date de création : {{ projet.createDate }}</p>
        </div>

        <div class="modal__main">
            <div class="modal__images">
                <h3 v-if="projet.image.length<2">Image</h3>
                <h3 v-else>Images</h3>
                <img v-for="i in projet.image"
                :key="0" 
                :src="`${baseUrl}${i.src}`" 
                :alt="i.alt"
                @click="showImage(0)"
                class="modal__thumbnail">
                
            </div>
            <div class="modal__info">
                <h3>Informations</h3>
                <div class="modal__info__link">
                    <h4>Lien :</h4>
                    <a :href="projet.link" target="_blank">{{ projet.link }}</a>
                </div>
                <div class="modal__info__description">
                    <h4>Description</h4>
                    <p>{{ projet.description }}</p>
                    <h4>Apport</h4>
                    <p>{{ projet.apport }}</p>
                </div>
            </div>
        </div>
    </div>
    <!-- Modal pour afficher l'image en grand -->
    <div v-if="selectedImageIndex !== -1" class="modal__imagebis" @click="closeImage">
        <!-- <span class="close" @click="closeImage">&times;</span> -->
        <div v-if="selectedImageIndex !== -1" class="modal__content" @click.stop>
            <button v-if="selectedImageIndex > 0" class="prev" @click="prevImage">&#10094;</button>
            <img v-if="images[selectedImageIndex]" :src="`${baseUrl}${images[selectedImageIndex].src}`" :alt="images[selectedImageIndex].alt" @click.stop>
            <button v-if="selectedImageIndex < projet.image.length - 1" class="next" @click="nextImage">&#10095;</button>
        </div>
    </div>
</template>
<script>
let 
zoom
</script>

<style scoped>
    .modal__info {
        width: 45%;
    }

    .modal__info__description {
        text-align: justify;
        overflow-y: auto;
        height: 100vh;
    }

    .modal__info h4 {
        margin-top: 1em;
        border-top: 1px solid #060640;
    }

    .modal__images img {
        width: 95%;
        height: auto;
    }

    .modal__images {
        display: flex;
        gap: 15px;
        /* flex-wrap: wrap; */
        flex-direction: column;
    
        width: 50%;
        /* justify-content: center; */
        height: 100vh;
        overflow-y: scroll;
        scrollbar-color: #060640 transparent;
        /* scrollbar-color: #060640; */
        scrollbar-width: auto;    
    }
    /* Modal d'affichage de l'image sélectionnée */
    .modal__imagebis {
        position: fixed;
        top: 0;
        left: 0;
        width: 100%;
        height: 100%;
        background: rgba(0, 0, 0, 0.8);
        /* display: flex;
        justify-content: center;
        align-items: center;
        flex-direction: column; */
    }
    .modal__content{
        margin: 0 auto;
        display: flex;
        justify-content: center;
        align-items: center;
        flex-direction: column;
        width: 80%;
        position: fixed;
        z-index: 4;
        top: 0;
        bottom: 0;
        left: 0;
        right: 0;
        margin-inline: auto;
    }

    .modal__content img {
        max-width: 80%;
        max-height: 80vh;
        border-radius: 5px;
        width: fit-content !important;
    }

    /* Bouton de fermeture */
    .close {
        position: absolute;
        top: 20px;
        right: 30px;
        /* font-size: 30px; */
        font-size: 5.5em;
        color: white;
        cursor: pointer;
    }

    /* Boutons de navigation */
    .prev, .next {
        position: absolute;
        top: 50%;
        background: rgba(255, 255, 255, 0.5);
        border: none;
        font-size: 30px;
        cursor: pointer;
        padding: 10px;
        transform: translateY(-50%);
    }

    .prev { left: 20px; }
    .next { right: 20px; }

    .prev:hover, .next:hover {
        background: rgba(255, 255, 255, 0.8);
    }
    .modal__imagebis img{
        width: 100%;
    }

    .modal__main {
        display: flex;
        gap: 1em;
        flex-wrap: wrap;
        margin-top: 1em;
        justify-content: center;
    }

    .modal__main h3 {
        font-size: 1.2em;
    }

    .modal__aside {
        display: flex;
        flex-wrap: wrap-reverse;
        justify-content: space-between;
        gap: 2em;
    }

    .modal__techno {
        display: flex;
        gap: 2em;
    }

    .modal__header {
        font-size: 1.5em;
        border-bottom: 2px solid #060640;
        margin-bottom: 10px;
    }

    .modal__background {
        position: fixed;
        top: 0;
        left: 0;
        width: 100%;
        height: 100%;
        overflow: auto;
        border: 1px solid black;
    }

    .modal {
        position: fixed;
        top: 2.5%;
        left: 5%;
        background-color: white;
        border: 1px solid #060640;
        border-radius: 25px;
        box-sizing: border-box;
        height: 95%;
        width: 90%;
        padding: 1em;
        overflow: auto;
    }

    .material-symbols-outlined {
        position: absolute;
        top: 10px;
        right: 10px;
        color: #060640;
        cursor: pointer;
    }

    @media screen and (max-width: 480px) {
        .modal {
            top: 0;
            left: 0;
            height: 100%;
            width: 100%;
            border-radius: 0;
        }

        .modal__main {
            flex-direction: column-reverse;
        }

        .modal__images, .modal__info{
            width: 95%;
        }
    }
</style>