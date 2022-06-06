<template>
    <div class="counter">
        <div class="counter__number">
            {{ displayDays }}<span class="countdown__number-description">Days</span>
        </div>
        <div class="counter__number">
            {{ displayHours }}<span class="countdown__number-description">Hours</span>
        </div>
        <div class="counter__number">
            {{ displayMinutes }}<span class="countdown__number-description">Min</span>
        </div>
        <div class="counter__number">
            {{ displaySeconds }}<span class="countdown__number-description">Sec</span>
        </div>
        
    </div>
</template>

<script>
export default {
    //getting the values from the parent component
    props: ['year', 'month', 'day', 'hour', 'minute', 'second', 'millisecond'],
    data: () => ({
        displayDays: 0,
        displayHours: 0,
        displayMinutes: 0,
        displaySeconds: 0
    }),
    //computed property is used for complex logic that includes reactive data
    computed: {
        _seconds: () => 1000, //1000 milliseconds
        //.this points to the component
        _minutes() {
            return this._seconds * 60;
        },
        _hours() {
            return this._minutes * 60;
        },
        _days() {
            return this._hours * 24;
        },
        end() {
            return new Date(
                this.year,
                this.month - 1,
                this.day - 1,
                this.hour,
                this.minute,
                this.second,
                this.millisecond
            );
        },
        
    },
    //run the methods
    mounted() {
        this.showRemaining();
    },
    //here you can write the methods of the component
    methods: {
        //adds a 0 in front of the number if its smaller than 10
        formatNumber: (number) => (number < 10 ? '0' + number : number),

        showRemaining() {
            //setInterval: repeatedly calls a function or executes a code snippet, with a fixed time delay between each call
            const timer = setInterval(() => {
                const now = new Date();
                const distance = this.end.getTime() - now.getTime();
                
                if (distance < 0) {
                    clearInterval(timer);
                    return;
                }

                //Math.floor shows the largest integer less than or equal to a given number
                //The difference between the desired date and now, divided by the day calculation of the computed property
                const days = Math.floor(distance / this._days);
                //% is Division Remainder
                const hours = Math.floor((distance % this._days) / this._hours);
                const minutes = Math.floor((distance % this._hours) / this._minutes);
                const seconds = Math.floor((distance % this._minutes) / this._seconds);

                //changes the values from the data property in the calculated values
                this.displayMinutes = this.formatNumber(minutes);
                this.displaySeconds = this.formatNumber(seconds);
                this.displayHours = this.formatNumber(hours);
                this.displayDays = this.formatNumber(days);
               
            });
        }
    }
};
</script>

<style lang="scss" scoped>
@import '../../scss/abstracts/mixins';
@import '../../scss/abstracts/variables';
@import './Counter.scss';
</style>
