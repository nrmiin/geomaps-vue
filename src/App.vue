<template>
    <div class="map-container">
        <geoMap></geoMap>
    </div>
</template>


<script>
    import geoMap from './components/HelloWorld'

    export default {
        name: 'App',
        components: {
            geoMap
        },
        data(){
            return{

            }
        }

    }
</script>

<style>
    .map-container {
        -webkit-font-smoothing: antialiased;
        -moz-osx-font-smoothing: grayscale;
        text-align: center;
        color: #2c3e50;
        margin-top: 30px;
        background: #ffffff;
    }


</style>