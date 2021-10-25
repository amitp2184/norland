<template>
    <div class="sign-main">
        <div class="container">
            <div class="row">

                <div class="col-lg-6 col-md-5">
                    <div class="sign-box-img">
                        <img src="~assets/images/logo.png" class="logo-part">
                        <h1>It’s getting crowded everyday. </h1>
                        <img src="~assets/images/sign-up.png" class="signimg">
                    </div>
                </div>

                <div class="col-lg-6 col-md-7">
                    <div class="sign-form">
                        <ul>
                            <li><a href="#" class="active">Sign Up<span class="bottom-border"></span></a></li>
                            <li><NuxtLink to="/signin">Sign in</NuxtLink></li>
                        </ul>

                        <form @submit.prevent="submit">
                            <div class="form-group" :class="{error: validation.hasError('formValues.email')}">
                                <input type="email" v-model="formValues.email" name="email" class="form-control" placeholder="Email">
                                <span v-if="validation.hasError('formValues.email')" class="error">
                                    {{ validation.firstError('formValues.email') }}
                                </span>
                            </div>
                            <div class="form-group" :class="{error: validation.hasError('formValues.email')}">
                                <input type="password" v-model="formValues.password" name="password" class="form-control" placeholder="Password">
                                <span v-if="validation.hasError('formValues.password')" class="error">
                                    {{ validation.firstError('formValues.password') }}
                                </span>
                            </div>
                            <div class="form-group password-contain" :class="{error: validation.hasError('formValues.email')}">
                                <input type="password" v-model="formValues.confirm_password" name="confirm_password" class="form-control" placeholder="Confirm Password">
                                <span v-if="validation.hasError('formValues.confirm_password')" class="error">
                                    {{ validation.firstError('formValues.confirm_password') }}
                                </span>
                                <h6>
                                  <span>
                                    <input type="checkbox"/>
                                    <label> Password must contain Alphabets and Numbers</label>
                                  </span>
                                </h6>
                                <h6>
                                  <span>
                                    <input type="checkbox"/>
                                    <label> Password must contain Special Characters</label>
                                  </span>
                                </h6>
                            </div>
                            <div class="form-group condi-check">
                                <h6>
                                  <span>
                                    <input type="checkbox" id="customRadioInline1" name="customRadioInline1"/>
                                    <label for="customRadioInline1"> I agree to Terms and Conditions</label>
                                  </span>
                                </h6>
                            </div>

                            <button type="submit">SIGN UP</button>
                            <div class="google-link-button">
                                <NuxtLink to="/dashboard"><img src="~assets/images/google-icons.png"> SIGN UP With GOOGLE</NuxtLink>
                            </div>
                        </form>
                    </div>
                </div>
            </div>
        </div>
    </div>
</template>

<script>
    import Notification from '~/components/Notification'
    import { Validator } from 'simple-vue-validator'

    export default {
        components: {
            Notification,
        },
        data() {
            return {
                formValues: {
                    email: '',
                    password: '',
                    confirm_password: '',
                },
            }
        },
        validators: {
            'formValues.email' (value) {
                return Validator.value(value).required('Please enter email').email('That doesn\'t look like a valid email address.')
            },
            'formValues.password' (value) {
                /*return Validator.value(value).required('Please enter password').minLength(6).regex('^[A-Za-z0-9*&@]*$', 'Must contain alphabets, number and spacial characters.')*/
                return Validator.custom(function () {
                    if (Validator.isEmpty(value)) {
                        return 'Please enter password';
                    } else if (value.length < 6) {
                        return 'Password must have at least 6 characters.';
                    } else {
                        let specialCharacterFormat = /[!@#$%^&*()_+\-=\[\]{};':"\\|,.<>\/?]+/;
                        let numberFormat = value.match(/\d+/g);
                        let alphabetFormat = /[a-zA-Z]/g;
                        let passwordFormatCheck = false;
                        if((numberFormat != null) && (specialCharacterFormat.test(value)) && (alphabetFormat.test(value))){
                            passwordFormatCheck = true;
                        }
                        if (!passwordFormatCheck) {
                            return "Password must contain Alphabets, Numbers and Special Characters";
                        }
                    }
                });
            },
            'formValues.confirm_password, formValues.password' (repeat, password) {
                if (this.submitted || this.validation.isTouched('formValues.confirm_password')) {
                    return Validator.value(repeat).required('Please enter confirm password').match(password, 'Password not matched')
                }
            }
        },
        methods: {
            async submit(event) {
                event.preventDefault();
                console.log('submitted');
                this.$validate()
                    .then(function (success) {
                        if (success) {
                            console.log('Validation succeeded!')
                        } else {
                            console.log('Validation failed!')
                        }
                    })
                /*try {
                    await this.$axios.post('register', {
                        email: this.email,
                        password: this.password
                    })

                    await this.$auth.loginWith('local', {
                        data: {
                            email: this.email,
                            password: this.password
                        },
                    })
                    this.$router.push('/')
                } catch (e) {
                    this.error = e.response.data.message
                }*/
            }
        }
    }
</script>
