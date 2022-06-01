<template>
    <section class="countdown">
        <h1 class="countdown__title">{{ title }}</h1>
        <h1 class="countdown__subtitle">{{ subtitle }}</h1>
        <Counter
            :year="2022"
            :month="11"
            :day="22"
            :hour="23"
            :minute="59"
            :second="59"
            :millisecond="59"
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
@import '../../scss/main.scss';
@import './Countdown.scss';
</style>
