<script setup>
import EpisodeCard from '~/components/episodeCard.vue';

const { id } = useRoute().params
const { data: seasons } = await useFetch(
    `https://api.tvmaze.com/seasons/${id}/episodes`
)

</script>

<template>
    <div style="background-color: black; height: 100%; padding-top: 100px; padding: 50px">

        <div style="display: flex;">
            <NuxtLink to="/"
                class="inline-flex items-center px-2 py-1.5 text-gray-800 bg-gray-100 border border-gray-200 rounded-lg dark:bg-gray-600 dark:text-gray-100 dark:border-gray-500">
                <svg class="w-4 h-4" aria-hidden="true" fill="currentColor" xmlns="http://www.w3.org/2000/svg"
                    viewBox="0 0 256 512">
                    <path
                        d="M137.4 406.6l-128-127.1C3.125 272.4 0 264.2 0 255.1s3.125-16.38 9.375-22.63l128-127.1c9.156-9.156 22.91-11.9 34.88-6.943S192 115.1 192 128v255.1c0 12.94-7.781 24.62-19.75 29.58S146.5 415.8 137.4 406.6z" />
                </svg>
            </NuxtLink>
            <p style="color: orange; margin-left: 10px; font-size: 20px;">Back</p>
        </div>
        <h1 style="color: white; margin-top: 40px; font-size: 36px;"> Season {{ seasons[0]?.season }} - List Episodes</h1>

        <Swiper>
            <SwiperSlide v-for="season in seasons" key="season.id" style="max-width: fit-content; padding: 50px 0px;">
                <EpisodeCard :season="season" />
            </SwiperSlide>
        </Swiper>
    </div>
</template>