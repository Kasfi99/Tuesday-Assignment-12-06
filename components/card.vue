<script setup>
const { season } = defineProps(['season'])
</script>

<template>
    <div style="display: flex;">
        <div style="position: relative;"
            class="max-w-sm border-gray-200 rounded-lg shadow dark:bg-gray-800 dark:border-gray-700">
            <p class="imageText">
                Season {{ season.number }}
            </p>

            <a href="#">
                <img class="image" :src="season.image.original" alt="seasons image" />
            </a>
            <NuxtLink :to="`listEpisode/${season.id}`"
                class="absolute bottom-4 right-4 inline-flex items-center px-3 py-2 text-sm font-medium text-center text-black bg-yellow-400 rounded-lg hover:bg-black hover:text-white focus:ring-4 focus:outline-none focus:ring-blue-300 dark:bg-blue-600 dark:hover:bg-blue-700 dark:focus:ring-blue-800">
                More Info
            </NuxtLink>
        </div>
    </div>
</template>

<style>
.image {
    height: 250px;
    width: 200px;
    border-radius: 20px;
}

.imageText {
    color: white;
    font-size: 22px;
    font-weight: 700;
    position: absolute;
    top: 30px;
    left: 15px;
}
</style>