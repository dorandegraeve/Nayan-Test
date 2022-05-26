<template>
    <section class="info">
        <div class="info__column">
            <div class="info__number">1</div>
            <h2 class="info__title">Save the Date</h2>
            <p class="info__text">
                The countdown to Samsonite’s Black Friday Sales is on! Be sure to check back for the
                best Black Friday Deals on suitcases and bags.
            </p>
        </div>
        <div class="info__column">
            <div class="info__number">2</div>
            <h2 class="info__title">When is Black Friday 2022?</h2>
            <p class="info__text">
                This year, Black Friday occurs on <b>22 November 2022</b>. Save this date and you’ll be
                guaranteed some fantastic discounts on selected Samsonite products.
            </p>
        </div>
        <div class="info__column">
            <div class="info__number">3</div>
            <h2 class="info__title">What is Black Friday?</h2>
            <p class="info__text">
                Black Friday is one of the most popular shopping days of the year with several
                retailers and brands offering huge discounts, deals and promotions. Originating in
                the USA, Black Friday occurs on the 4th Friday in November – the day after
                Thanksgiving in America – and marks the start of the Christmas shopping period.
            </p>
        </div>
    </section>
</template>

<script>
export default {
    props: {
        title: {
            type: String
        }
    }
};
</script>

<style lang="scss" scoped>
@import './Info.scss';
@import '../../scss/main.scss';
</style>

