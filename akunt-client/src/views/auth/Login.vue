<template>
    <div class="container my-5">
        <div class="row justify-content-center">
            <div class="col-8">
                <div class="card rounded shadow">
                    <div class="card-header">
                        Login
                    </div>
                    <div class="card-body">
                        <form @submit.prevent="auth()">

                            <div class="mb-3">
                                <label class="form-label">Email</label>
                                <input type="text" class="form-control">
                                <div class="text-danger">

                                </div>
                            </div>
                            <div class="mb-3">
                                <label class="form-label">Password</label>
                                <input type="text" class="form-control">
                                <div class="text-danger">

                                </div>
                            </div>
                            <button class="btn btn-outline-primary">Submit</button>
                        </form>
                    </div>
                </div>
            </div>
        </div>
    </div>
</template>

<script>
    import axios from "axios"
    import {
        reactive,
        ref
    } from 'vue'
    import {
        useRouter
    } from 'vue-router'

    export default {
        setup() {
            //data binding
            const user = reactive({
                email: '',
                password: ''
            })

            function auth() {
                axios.post(
                        'http://127.0.0.1:8000/api/login',
                        user
                    )
                    .then((res) => {
                        console.log(res)
                    }).catch((err) => {
                        console.log(err)
                    });
            }
            return {
                auth
            }
        }
    }
</script>