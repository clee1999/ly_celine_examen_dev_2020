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


                <div v-if="errors.length">
                    <b>Please correct the following error(s):</b>
                    <ul>
                        <li v-for="error in errors" :key="error.id">{{error}}</li>
                    </ul>
                </div>

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

                errors : [],

            }
        },
        methods: {
            onSubmit(evt) {
                evt.preventDefault()
                this.errors = [];

                let access_key = '7b37b087dc3f6d22f6b7f2221dcca41a';
                let email_address = this.form.email;

                fetch('http://apilayer.net/api/check?access_key=' + access_key + '&email=' + email_address)
                    .then(function(response) {
                        response.json().then(function (data) {
                            console.log(data);
                            console.log(data.smtp_check);
                            if (data.smtp_check === false) {
                                console.log('cette adresse est fausse')
                                alert('Attention, ton email existe pas, donc recommence à nouveau')
                                this.errors.push('Email not existed');
                                return
                            } else {
                                console.log('cette adresse est vraie')
                                alert('Votre inscription a été validée !')
                               this.errors.push('Email existed');
                            }
                        });
                    })
                    .catch(function(err) {
                        console.log('Fetch Error :-S', err);
                    })
            },
        },
    }


</script>

<style scoped>

</style>