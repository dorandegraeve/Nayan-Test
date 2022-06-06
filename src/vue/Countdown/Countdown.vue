<template>
    <section class="countdown">
        <h1 class="countdown__title">{{ title }} <br><span class="countdown__title--breakline">{{ subtitle }}</span></h1>   
        <Counter
            :year="2022"
            :month="11"
            :day="25"
            :hour="0"
            :minute="0"
            :second="0"
            :millisecond="0"
        />
    </section>
</template>

<script>
import Counter from '../Counter/Counter.vue';
export default {
    components: {
        Counter
    },
    props: {
        title: {
            type: String
        },
        subtitle: {
            type: String
        }
    }
};
</script>

<style lang="scss" scoped>
@import '../../scss/abstracts/mixins';
@import '../../scss/abstracts/variables';
@import './Countdown.scss';
</style>
