<template>
    <v-container>
        <v-btn @click.native="(e:any) => { storeFavorite.clearFaves()}">CLEAR</v-btn>
        <h1>Favorite Rockets</h1>
        <v-spacer></v-spacer>
        <div>
            <div v-for="fave in storeFavorite.favArray">
                <h2>{{ fave }}</h2>
            </div>
        </div>
    </v-container>
</template>

<script setup lang="ts">

import { useFavorite } from '@/stores/useFavorite'
const storeFavorite  = useFavorite();

</script>