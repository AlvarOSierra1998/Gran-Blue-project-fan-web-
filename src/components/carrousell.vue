<template>
    <div class="carousel">
        <div class="carousel-item" v-for="(image, index) in images" :key="index" :class="{ active: index === activeIndex }">
            <img class="photo" :src="image" alt="Carousel image">
            <div class="button-container">
                <button @click="prev">Previous</button>
                <button @click="next">Next</button>
            </div>

        </div>

    </div>
</template>

<script setup>
import { ref } from 'vue';

const images = [
    new URL('../assets/fondo1.jpg', import.meta.url),
    new URL('../assets/fondo2.jpg', import.meta.url),
    new URL('../assets/fondo4.jpg', import.meta.url),
    new URL('../assets/fondo5.jpeg', import.meta.url),
    new URL('../assets/fondo6.jpeg', import.meta.url),
    // Add more image paths as needed
];

const activeIndex = ref(0);

const next = () => {
    activeIndex.value = (activeIndex.value + 1) % images.length;

};

const prev = () => {
    activeIndex.value = (activeIndex.value - 1 + images.length) % images.length;
};


</script>

<style scoped>
.carousel {
    display: inline-flex;
    margin: auto;
    position: relative;
    left: 2%;
    max-width: 100%;
}

.photo {
    width: 130%;
    border-radius: 10px;
    box-shadow: 20px 20px 30px 0 rgba(0, 0, 0, 0.5);
}

.carousel-item {
    display: none;
}

.carousel-item.active {
    display: block;
}

.button-container {
    display: flex;
    justify-content: center;
    align-items: center;
    margin: auto;
    width: 130%;
}

.button-container button {
    margin: 0 10px;
    padding: 10px 20px;
    border: none;
    border-radius: 5px;
    cursor: pointer;
    background: none;
    font-size: 1.5rem;
}

.button-container button:hover {
    background-color: rgba(0, 0, 0, 0.507);
    color: wheat;
    box-shadow: 2px 30px 40px #000000;
    transition: 0.5s;
}

/* Tablet y móvil */
@media screen and (max-width: 1186px) {
    .carousel {
        display: block;
        left: 0;
        width: 100%;
    }

    .carousel-item.active {
        width: 100%;
    }

    .photo {
        width: 100%;
        max-width: 100%;
        height: auto;
    }

    .button-container {
        width: 100%;
    }

    .button-container button {
        font-size: 1rem;
        padding: 8px 14px;
    }
}
</style>