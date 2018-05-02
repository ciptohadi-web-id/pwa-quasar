<template>
<q-page padding>
    <div class="row">
        <div class="col-8">
            <progressive-img src="statics/sholawat-asygil-aab-elkarimi.png" placeholder="statics/sholawat-asygil-aab-elkarimi.jpg" :blur="30" />
        </div>
    </div>
    <div class="row">
        <div class="col-8">
            <vcl-facebook></vcl-facebook>
        </div>
    </div>
    <div class="row">
        <div class="col-8">
            <vcl-instagram></vcl-instagram>
        </div>
    </div>
    <div class="row">
        <div class="col-8">
            <vue-content-loading :width="300" :height="100">
                <circle cx="20" cy="20" r="20" />
                <rect x="50" y="3" rx="4" ry="4" width="100" height="15" />
                <rect x="50" y="20" rx="4" ry="4" width="50" height="10" />
                <rect x="0" y="50" rx="4" ry="4" width="150" height="10" />
                <rect x="0" y="65" rx="4" ry="4" width="150" height="10" />
                <rect x="0" y="80" rx="4" ry="4" width="100" height="10" />
            </vue-content-loading>
        </div>
    </div>

</q-page>
</template>

<script>
// Don't forget to specify which animations
// you are using in quasar.conf.js > animations
import {
    VueContentLoading,
    VclFacebook,
    VclInstagram
} from 'vue-content-loading';
import Vue from 'vue';
import VueProgressiveImage from 'vue-progressive-image';
Vue.use(VueProgressiveImage)

export default {
    data() {
        return {}
    },
    components: {
        VueContentLoading,
        VclFacebook,
        VclInstagram
    },
    methods: {}
}
</script>
