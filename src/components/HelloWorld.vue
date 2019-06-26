<template>

        <div id="map" class="map"></div>

</template>


<script>
    import L from 'leaflet'

    export default {
        name: 'geoMap',
        data() {
            return {
                map: null,
                tileLayer: null,
                layers: [
                    {
                        id: 0,
                        name: 'OnlineUsers',
                        active: true,
                        features: [
                            {
                                id: 0,
                                name: 'user1',
                                type: 'marker',
                                coords: [9.6109607, -1.2050322],
                            },
                            {
                                id: 1,
                                name: 'user2',
                                type: 'marker',
                                coords: [38.6350008, -90.2261532],
                            },
                            {
                                id: 2,
                                name: 'user3',
                                type: 'marker',
                                coords: [65.6188362, -90.1947098],
                            },
                            {
                                id: 3,
                                name: 'user4',
                                type: 'marker',
                                coords: [50.617972, -70.2756436],
                            },
                            {
                                id: 4,
                                name: 'user5',
                                type: 'marker',
                                coords: [65.6304077, -120.1916921],
                            },
                            {
                                id: 5,
                                name: 'user6',
                                type: 'marker',
                                coords: [30.6036282, 50.2381407],
                            },
                            {
                                id: 6,
                                name: 'user7',
                                type: 'marker',
                                coords: [38.6313642, -90.1961267],
                            },
                            {
                                id: 7,
                                name: 'user8',
                                type: 'marker',
                                coords: [38.6157376, -90.27716],
                            },
                            {
                                id: 8,
                                name: 'user9',
                                type: 'marker',
                                coords: [38.6143846, -90.280048],
                            },
                        ],
                    },
                ],
            }
        },
        mounted() { /* Code to run when app is mounted */
            this.initMap();
            this.initLayers();
        },
        methods: { /* Any app-specific functions go here */
            initMap() {
                var southWest = L.latLng( -70, -160),
                    northEast = L.latLng(70, 160),
                    bounds = L.latLngBounds(southWest, northEast);
                this.map = L.map('map',{
                    maxBounds: bounds,
                    minZoom:1,
                    maxZoom: 18,
                    attribution: 'Niomatic',
                }).setView([0, 0], 1);
                this.tileLayer = L.tileLayer(
                    'https://cartocdn_{s}.global.ssl.fastly.net/base-midnight/{z}/{x}/{y}.png',

                    this.map.fitBounds(bounds),
                );
                this.tileLayer.addTo(this.map);
            },
            initLayers() {
                var myIcon = L.icon({
                    iconUrl: require('D:/javaS/samin/projects/GeoMaps-vue/src/assets/iconfinder_Marker_66990.png'),
                    iconSize:     [38, 95], // size of the icon
                    iconAnchor:   [22, 94], // point of the icon which will correspond to marker's location
                    popupAnchor:  [-3, -76] // point from which the popup should open relative to the iconAnchor
                });
                L.marker([51.5, -0.09], {icon: myIcon}).addTo(this.map);
                this.layers.forEach((layer) => {
                    // Initialize the layer
                    const markerFeatures = layer.features.filter(feature => feature.type === 'marker');
                    markerFeatures.forEach((feature) => {
                        feature.leafletObject = L.marker(feature.coords,{
                            opacity: 0.5})
                            .bindPopup(feature.name);
                        feature.leafletObject.addTo(this.map);
                    });
                });
            },
        },
    }
</script>

<style>

    .map
    {
        background-color: #000000;
        width: 700px;
        height: 500px;
        display: inline-block;
        align-items: center;
    }

</style>