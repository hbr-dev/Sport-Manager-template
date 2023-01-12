<template>
    <div class="signup-box">
        <h1>Sign-Up Page : </h1>
        <form>
            <!-- 2 column grid layout with text inputs for the first and last names -->
            <div class="row mb-4">
                <div class="col">
                <div class="form-outline">
                    <label class="form-label" for="form3Example1">Name</label>
                    <input type="text" id="form3Example1" class="form-control" v-model="signupForm.name" />
                </div>
                </div>
            </div>

            <!-- Email input -->
            <div class="form-outline mb-4">
                <label class="form-label" for="form3Example3">Email address</label>
                <input type="email" id="form3Example3" class="form-control" v-model="signupForm.email"/>
            </div>

            <!-- Password input -->
            <div class="form-outline mb-4">
                <label class="form-label" for="form3Example4">Password</label>
                <input type="password" id="form3Example4" class="form-control" v-model="signupForm.password"/>
            </div>

            <!-- Password re input -->
            <div class="form-outline mb-4">
                <label class="form-label" for="form3Example4">Re-enter Password</label>
                <input type="password" id="form3Example4" class="form-control" />
            </div>

            <!-- Checkbox -->
            <div class="form-check d-flex justify-content-center mb-4">
                <input class="form-check-input me-2" type="checkbox" value="" id="form2Example33" checked />
                <label class="form-check-label" for="form2Example33">
                Subscribe to our newsletter
                </label>
            </div>

            <div class="login-link">
                <p>Have you an account ?: </p>
                <p><router-link style="text-decoration: none;" to="/Login">Login</router-link></p>
            </div>

            <!-- Submit button -->
            <button type="submit" class="btn btn-primary btn-block mb-4">Sign up</button>
        </form> 
    </div>
</template>

<style scoped>
    @import 'https://cdn.jsdelivr.net/npm/bootstrap@5.2.3/dist/css/bootstrap.min.css';
    .signup-box {
        padding: 50px 350px;
    }
    h1 {
        font-family: 'Montserrat', sans-serif;
        -webkit-font-smoothing: antialiased;
        -moz-osx-font-smoothing: grayscale;
        text-align: center;
        color: #262930;
        font-weight: 400;
        margin-bottom: 25px;
    }
    .login-link {
        display: flex;
        align-items: center;
        justify-content: center;
        margin-bottom: 25px;
    }
</style>

<script>
export default {
    setup() {
        return {
            signupForm: {
                name: '',
                email: '',
                password: '',
                rememberMe: false,
                errors: []
            }
        }
    },
}
</script>