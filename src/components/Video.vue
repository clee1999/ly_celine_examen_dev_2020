<template>
    <b-container>
        <b-row class="mt-5">
            <b-col xl="12">
                <h1 class="text-center">Watch the video</h1>
                <b-embed class="mt-5"
                        type="iframe"
                        aspect="16by9"
                        src="https://www.youtube.com/embed/zpOULjyy-n8?rel=0"
                        allowfullscreen
                ></b-embed>
            </b-col>
        </b-row>
        <b-row class="text-center">
            <b-col xl="12">
                <b-button href="#carte" class="mt-5">Clique sur moi pour bouger</b-button>
            </b-col>
        </b-row>
    </b-container>
</template>

<script>
    export default {
        name: "Video"
    }
</script>

<style scoped>

</style>