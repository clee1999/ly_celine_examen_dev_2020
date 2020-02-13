<template>
    <b-container class="mt-5" id="carte">
        <b-row>
            <b-col xl="12">
                <h1 class="text-center">Une carte comme une autre...</h1>
            </b-col>
        </b-row>
        <b-row>
            <b-col xl="12" class="mx-auto mt-3">
                <h3> Hello, what are you looking for in Paris?</h3>
                <p>Tape un truc si tu veux chercher autre chose que des cafés lol</p>
            </b-col>
        </b-row>
        <b-row class="mb-5 mt-2">
            <b-col xl="5" class="mx-auto">
                <b-form-input  type="text" v-model="keyword" v-on:keyup.enter="searchNearBy"></b-form-input>
            </b-col>
        </b-row>
        <b-row>
            <b-col xl="12">
                <GmapMap ref="mapRef"
                         :center="{lat:10, lng:10}"
                         :zoom="12"
                         map-type-id="terrain"
                >
                    <GmapMarker
                            :key="index"
                            v-for="(m, index) in markers"
                            :position="m.geometry.location"
                            :title="m.name"
                            :clickable="true"
                            :draggable="false   "
                            @click="openInfoWindowTemplate(m)"
                    >
                    </GmapMarker>
                    <GmapInfoWindow
                            :options="{maxWidth: 300}"
                            :position="infoWindow.position"
                            :opened="infoWindow.open"
                            @closeclick="infoWindow.open=false">
                        <!-- ici on utilise v-html et pas {{ }} car il est possible qu'on balance du html dans la div et qu'on souhaite l'interpreter -->
                        <div v-html="infoWindow.template"></div>
                    </GmapInfoWindow>
                </GmapMap>
            </b-col>
        </b-row>
    </b-container>
</template>

<script>
    export default {
        name: "Carte",
        data () {
            return {
                keyword: 'cafe',
                markers: [],
                infoWindow: {
                    position: {lat: 0, lng: 0},
                    open: false,
                    template: ''
                }
            }
        },
        methods: {
            searchNearBy(){
                this.$refs.mapRef.$mapPromise.then((map) => {
                    /* eslint-disable no-undef */
                    //let targetLatLng = new google.maps.LatLng(48.864716, 2.349014)
                    map.panTo({lat: 48.864716, lng: 2.349014})
                    // map.panTo({lat: 48.864716, lng: 2.349014})

                    /* eslint-disable no-undef */
                    let placesService = new google.maps.places.PlacesService(map)
                    placesService.nearbySearch({
                        location: {lat: 48.864716, lng: 2.349014},
                        name: this.keyword,
                        radius: 1000,
                        // types: ['store', 'restaurant']
                    }, (results, status) => {
                        this.markers = results
                        console.log(status)
                    })
                })
            },
            openInfoWindowTemplate (item) {
                this.infoWindow.template = '<img alt="Vue logo" src="'+ item.icon +'"><h1>' + item.name +'</h1>'
                this.infoWindow.position = item.geometry.location
                this.infoWindow.open = true
            }
        },
        mounted () {
            this.searchNearBy()

        }
    }

</script>

<style scoped>
    .vue-map-container {
        width: auto;
        height: 70vh;
    }

</style>