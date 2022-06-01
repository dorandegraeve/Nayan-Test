<template>
    <section class="newsletter">
        <h2 class="newsletter__title">Can't wait until Black Friday?</h2>
        <p class="newsletter__text">
            Sign up to our VIP newsletter and we’ll let you know when our Black Friday pre-sale
            starts! Plus you’ll always be kept up to date with the latest sales and promotions
            throughout the year with exclusive access to private sales and special discounts.
        </p>
        <!-- submit.prevent makes sure the page does not refresh when submitting -->
        <form @submit.prevent="submitForm()">
         <!-- :class="" adds a class conditionally -->
            <input
               
                class="newsletter__input" :class="{'newsletter__input--invalid': emailValidity === 'invalid', 'newsletter__input--valid': emailValidity === 'valid' }"
                type="email"
                id="email"
                name="email"
                placeholder="Enter your email"
                v-model="email"
            />
            <button class="newsletter__button">&#9658;</button>
            <!-- v-if shows the element conditionally -->
            <p v-if="emailValidity === 'invalid'" class="newsletter__invalid">Your email is already registered!</p>
            <p v-if="emailValidity === 'valid'" class="newsletter__valid">Your email is successfully registered!</p>
        </form>
    </section>
</template>

<script>
export default {
    data() {
        return {
            email: '',
            emailValidity: '',
        };
    },
    methods: {
        submitForm() {
            // console.log('Email: ' + this.email);

            fetch('http://localhost:8080/api/newsletter', {
                method: 'POST',
                headers: {
                    'Content-Type': 'application/json'
                },
                //property: emailAddress
                body: JSON.stringify({ emailAddress: this.email })
            })
                .then((res) => res.json())
                .then((data) => {
                    console.log(data);
                    if (data.success === false && data.errorMessage === 'EXISTING_USER') {
                        this.validateInput('invalid');
                        // console.log(this.emailValidity);
                    } else if(data.success === true) {
                        this.validateInput('valid')
                        // console.log(this.emailValidity);
                    }
                });
        },


        validateInput(validate) {
                this.emailValidity = validate;
        }
    }
};
</script>

<style lang="scss" scoped>
@import '../../scss/main.scss';
@import './Newsletter.scss';
</style>
