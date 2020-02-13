<template>
    <b-container class="mt-5" id="inscription">
        <b-row>
            <b-col xl="12">
                <h1 class="text-center">Inscris-toi vite !</h1>
            </b-col>
        </b-row>
        <b-row>
            <b-col xl="12" >
                <b-form @submit="onSubmit">

                    <b-form-group id="input-group-1" label="Entre ton prénom :" label-for="input-1">
                        <b-form-input
                                id="input-1"
                                v-model="form.name"
                                required
                                placeholder="Enter name"
                        ></b-form-input>
                    </b-form-group>

                    <b-form-group id="input-group-2" label="Entre ton nom :" label-for="input-2">
                        <b-form-input
                                id="input-2"
                                v-model="form.lastname"
                                required
                                placeholder="Enter lastname"
                        ></b-form-input>
                    </b-form-group>

                    <b-form-group
                            id="input-group-3"
                            label="Entre ton email :"
                            label-for="input-3"
                            description="We'll never share your email with anyone else."
                    >
                        <b-form-input
                                id="input-3"
                                v-model="form.email"
                                type="email"
                                required
                                placeholder="Enter email"
                        ></b-form-input>
                    </b-form-group>

                    <b-button type="submit" variant="primary">Submit</b-button>

                </b-form>



            </b-col>
        </b-row>
    </b-container>
</template>

<script>
    export default {
        name: "Inscription",
        data() {
            return {
                form: {
                    name: '',
                    lastname:'',
                    email: '',
                },

            }
        },
        methods: {
            onSubmit(evt) {
                evt.preventDefault()
                alert('Votre inscription a été validée !')
            },
        }
    }
</script>

<style scoped>

</style>