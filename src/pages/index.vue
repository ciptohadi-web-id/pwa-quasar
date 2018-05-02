<template>
    <q-page padding="padding">
        
        <!-- <div>
                <div>
                    <h2>Search and add a pin</h2>
                    <label>
                    <gmap-autocomplete
                      @place_changed="setPlace">
                    </gmap-autocomplete>
                    <button @click="addMarker">Add</button>
                  </label>
                    <br/>
                </div>
                <br>
                <gmap-map :center="center" :zoom="12" style="width:100%;  height: 400px;">
                    <gmap-marker :key="index" v-for="(m, index) in markers" :position="m.position" @click="center=m.position"></gmap-marker>
                </gmap-map>
            </div> -->
    </q-page>
</template>

<script>
    // Don't forget to specify which animations you are using in quasar.conf.js >
    // animations
    import Vue from "vue";
    import * as VueGoogleMaps from "vue2-google-maps";
    Vue.use(VueGoogleMaps, {
        load: {
            key: "AIzaSyDXWAdr5dTvEojqcKhKwCDj0Uvu_CnMMF8",
            libraries: "places" // necessary for places input
        }
    });
    export default {
        data() {
            return {
                // default to Montreal to keep it simple
                // change this to whatever makes sense
                center: {
                    lat: 45.508,
                    lng: -73.587
                },
                markers: [],
                places: [],
                currentPlace: null
            };
        },
        mounted() {
            this.geolocate();
        },
        methods: {
            // receives a place object via the autocomplete component
            setPlace(place) {
                this.currentPlace = place;
            },
            addMarker() {
                if (this.currentPlace) {
                    const marker = {
                        lat: this.currentPlace.geometry.location.lat(),
                        lng: this.currentPlace.geometry.location.lng()
                    };
                    this.markers.push({
                        position: marker
                    });
                    this.places.push(this.currentPlace);
                    this.center = marker;
                    this.currentPlace = null;
                }
            },
            geolocate: function() {
                navigator.geolocation.getCurrentPosition(position => {
                    this.center = {
                        lat: position.coords.latitude,
                        lng: position.coords.longitude
                    };
                });
            }
        }
    };
</script>

<style scoped="scoped" lang="stylus">
</style>