<template>
    <div>
        <div v-for="starIndex in 5" :key="starIndex" class="star">
            {{ console.log(starIndex, fullStarsCount, hasHalfStar, this.rating, '<<') }} <svg-icon
                v-if="starIndex <= fullStarsCount" type="mdi" :path="path.fullStar"></svg-icon>

                <svg-icon v-else-if="starIndex === fullStarsCount && hasHalfStar" type="mdi"
                    :path="path.halfStar"></svg-icon>

                <svg-icon v-else type="mdi" :path="path.emptyStar"></svg-icon>
        </div>
    </div>
</template>
  
<script>
import SvgIcon from '@jamescoyle/vue-icon';
import { mdiStar } from '@mdi/js';
import { mdiStarHalf } from '@mdi/js';
import { mdiStarOutline } from '@mdi/js';

export default {
    props: ['rating'],
    name: 'MyComponent',
    components: {
        SvgIcon
    },
    computed: {
        fullStarsCount() {
            return Math.floor(this.rating) / 2;
        },
        hasHalfStar() {
            const decimalPart = this.rating - Math.floor(this.rating);
            return decimalPart >= 0.1 && decimalPart <= 0.9;
        }
    },
    data() {
        console.log(typeof (this.rating));

        return {
            path: {
                fullStar: mdiStar,
                halfStar: mdiStarHalf,
                emptyStar: mdiStarOutline
            }
        };
    }
};
</script>
  
<style scoped>
.star {
    display: inline-block;
}
</style>
  