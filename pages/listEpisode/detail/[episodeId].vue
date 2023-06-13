<template>
    <div style="background-color: black; height: 2000px">
        <div style="position: absolute; top: 40px; left: 100px; z-index: 100;">
            <NuxtLink to="/listEpisode/307" style="display: flex; align-items: center;">
                <svg class="w-8 h-8" style="color: white;" aria-hidden="true" fill="currentColor"
                    xmlns="http://www.w3.org/2000/svg" viewBox="0 0 256 512">
                    <path
                        d="M137.4 406.6l-128-127.1C3.125 272.4 0 264.2 0 255.1s3.125-16.38 9.375-22.63l128-127.1c9.156-9.156 22.91-11.9 34.88-6.943S192 115.1 192 128v255.1c0 12.94-7.781 24.62-19.75 29.58S146.5 415.8 137.4 406.6z" />
                </svg>
                <p style="color: yellow; margin-left: 10px; font-size: 20px;">Back</p>
            </NuxtLink>
        </div>


        <p class="heading">{{ episode?.name }}</p>
        <div>
            <star-rating class="star" :rating="episode?.rating?.average" />
        </div>
        <p class="text">{{ removePTag(episode?.summary) }}</p>



        <img :src="episode?.image.original" class="image" style="width: 100%; height: 100%; object-fit: cover;">
    </div>
</template>
  
  
  
<script setup>
const { episodeId } = useRoute().params
const { data: episode } = await useFetch(
    `https://api.tvmaze.com/episodes/${episodeId}`
)

const removePTag = (summary) => {
    const strippedSummary = summary.replace(/<\/?p>/g, '');
    return strippedSummary;
};
</script>
  
<style>
.heading {
    position: absolute;
    top: 30%;
    left: 9%;
    color: white;
    font-size: 56px;
    font-weight: 700;
    z-index: 1;
}

.star {
    position: absolute;
    top: 38%;
    left: 8%;
    z-index: 1;
    color: orange;
    width: 78px;
    height: 78px;
}

.text {
    position: absolute;
    margin-top: 25%;
    margin-left: 8%;

    color: white;
    max-width: 50%;
    font-size: 18px;
    z-index: 1;
}

.image {
    width: 100vw;
    height: 100vh;
    object-fit: cover;
    filter: brightness(80%);
    box-shadow: 0 2px 4px rgba(0, 0, 0, 0.3);
    border-radius: 0px;
}
</style>
  