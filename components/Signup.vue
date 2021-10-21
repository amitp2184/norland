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
                        <form>
                            <div class="form-group">
                                <input type="text" name="" class="form-control" placeholder="Email">
                            </div>
                            <div class="form-group">
                                <input type="password" name="" class="form-control" placeholder="password">
                            </div>
                            <div class="form-group password-contain">
                                <input type="password" name="" class="form-control" placeholder="Confirm Password">
                                <h6>
                                  <span>
                                    <input type="checkbox"/>
                                    <label for="customRadioInline"> Password must contain Alphabets and Numbers</label>
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
                                <a href="#"><img src="~assets/images/google-icons.png"> SIGN UP With GOOGLE</a>
                            </div>
                        </form>
                    </div>
                </div>
            </div>
        </div>
    </div>
</template>
