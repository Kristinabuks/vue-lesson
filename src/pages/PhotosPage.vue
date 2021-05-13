<template>
    <v-container>
        <PhotoForm  @addPhoto="addPhoto"/>
        <v-row>
            <Photo
            v-bind:key="photo.id" v-for="photo in $store.getters.getAllPhoto"
            v-bind:photo="photo"
            />
        </v-row>
        <PhotoDialog/>
    </v-container>   
</template>

<script>

import Photo from "@/components/photo/Photo";
import PhotoForm from "@/components/photo/PhotoForm";
import PhotoDialog from "@/components/photo/PhotoDialog";
import {mapActions} from "vuex";

export default {
    components: {
        Photo, PhotoForm, PhotoDialog
    },
    data: () => ({
        photos: [],
       // currentPhoto: {},
       // dialogVisible: false
    }),

    mounted() {
        //this.fetchTodo()
        this.fetchPhotos()
    },

    methods: {
        //fetchTodo() {
        //    this.axios.get('http://jsonplaceholder.typicode.com/photos?_limit=10')
        //        .then(res => { this.photos = res.data })
//
        //},
        ...mapActions(['fetchPhotos']),
        addPhoto(photo) {
            this.photos.push(photo)
        },
        openPhoto(photo) {
            this.currentPhoto = photo,
            this.dialogVisible = true
        }
    }

}
</script>

<style scoped>

</style>
