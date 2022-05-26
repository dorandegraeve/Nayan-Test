<template>
    <section class="countdown">
        <h1 class="countdown__title">{{ title }}</h1>
        <h1 class="countdown__subtitle">{{ subtitle }}</h1>
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
@import './Countdown.scss';
@import '../../scss/main.scss';
</style>
