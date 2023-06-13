<script setup>
const { season } = defineProps(['season'])
</script>

<template>
    <div style="overflow: hidden; max-width: 340px; max-height: 400px; margin-right: 40px;">

        <NuxtLink :to="`detail/${season.id}`" style="position: relative;  display: flex;">

            <div class="rating">
                <p class="ratingText">{{ season.rating.average }}</p>
            </div>
            <img class="rounded-t-lg" :src="season?.image?.original" alt="seasons image"
                style="height: 400px; width: 340px; margin-right: 30px; object-fit: cover;" />


        </NuxtLink>
    </div>

    <div style="max-width: 90%;">
        <p style="color: white; margin-top: 20px; font-size: 20px;">{{ season?.name }}</p>
        <div class="star">
            <star-rating style="color: orange;" :rating="season.rating.average" />
        </div>
        <p style="color: white; margin-top: 25px; font-size: 20px;">Episode {{ season.number }}</p>
    </div>
</template>

<style>
.rating {
    background-color: orange;
    width: 100px;
    height: 40px;
    border-radius: 10px;
    position: absolute;
    right: -30px;
    top: -10px;

}

.ratingText {
    color: black;
    font-size: 26px;
    font-weight: 600;
    margin: 0;
    padding-top: 5px;
    padding-left: 20px;
}

.star {
    margin-top: 53%;
    margin-left: -8%;
}
</style>
