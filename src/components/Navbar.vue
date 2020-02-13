<template>
    <b-navbar toggleable="sm" type="light" variant="light">
        <b-navbar-toggle target="nav-text-collapse"></b-navbar-toggle>

        <b-navbar-brand>VueJSExam</b-navbar-brand>

        <b-collapse id="nav-text-collapse" is-nav>
            <b-navbar-nav>
                <b-link href="#video" >Video</b-link>
                <b-link href="#texte" class="ml-3">Texte</b-link>
                <b-link href="#carte" class="ml-3">Carte</b-link>
                <b-link href="#inscription" class="ml-3">Inscription</b-link>
            </b-navbar-nav>
        </b-collapse>
    </b-navbar>
</template>

<script>
    export default {
        name: "Navbar"
    }
</script>

<style scoped>

</style>