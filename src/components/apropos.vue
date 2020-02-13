<template>
    <section id="apropos">
        <h1 class="text-center"> A propos </h1>
        <Video></Video>
        <Texte></Texte>
        <Carte></Carte>
        <Inscription></Inscription>
    </section>
</template>

<script>
    import Video from "@/components/Video";
    import Texte from "@/components/Texte";
    import Carte from "@/components/Carte";
    import Inscription from "@/components/inscription";
    export default {
        name: "apropos",
        components: {
            Inscription,
            Carte,
            Texte,
            Video,

        }
    }
</script>

<style scoped>

</style>