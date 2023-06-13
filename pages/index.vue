<script setup>
const { data: episodes } = await useFetch(
    `https://api.tvmaze.com/shows/82/episodes`
)

const { data: seasons } = await useFetch(
    `https://api.tvmaze.com/shows/82/seasons`
)

const limitedEpisodes = episodes._rawValue.slice(0, 5);
const limitedSeasons = seasons._rawValue.slice(0, 8);
</script>

<template>
    <div class="bg-black h-full">
        <div style=" max-width: 1000px; margin-left: 25vw;">

            <carousel :episodes="limitedEpisodes" />

            <h1 class="mb-12 mt-12 font-extrabold leading-none tracking-tight md:text-5xl text-white">
                List seasons</h1>

            <div style="display: flex; padding-bottom: 100px; ">
                <Swiper>
                    <SwiperSlide v-for="(season, index) in limitedSeasons" :key="index"
                        style="display: flex; max-width: fit-content; margin-right: 50px;">
                        <card :season="season" />
                    </SwiperSlide>
                </Swiper>
            </div>

        </div>
    </div>
</template>
