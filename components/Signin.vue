<template>
    <div class="sign-main">
        <div class="container">
            <div class="row">

                <div class="col-lg-6 col-md-5">
                    <div class="sign-box-img">
                        <img src="~assets/images/logo.png" class="logo-part">
                        <h1>Welcome back !</h1>
                        <img src="~assets/images/sign-in.png" class="sign-in-img">
                    </div>
                </div>

                <div class="col-lg-6 col-md-7">
                    <div class="sign-form">
                        <ul>
                            <li><NuxtLink to="/">Sign Up</NuxtLink></li>
                            <li><a href="#" class="active">Sign in<span class="bottom-border"></span></a></li>
                        </ul>
                        <form>
                            <div class="form-group">
                                <input type="text" name="" class="form-control" placeholder="Email">
                            </div>
                            <div class="form-group">
                                <input type="password" name="" class="form-control" placeholder="password">
                            </div>

                            <button type="submit">SIGN UP</button>
                            <div class="google-link-button">
                                <a href="#"><img src="~assets/images/google-icons.png"> SIGN IN With GOOGLE</a>
                            </div>
                            <div class="forgot-bnt">
                                <a href="#">Forgot Email/Password ?</a>
                            </div>
                        </form>
                    </div>
                </div>
            </div>
        </div>
    </div>
</template>
