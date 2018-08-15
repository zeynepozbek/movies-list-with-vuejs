<template>
    <div class="flex flex-wrap mb-4">
        <div class="xl:w-1/3 lg:w-1/3 md:w-1/3 sm:w-full mb-5 px-4" v-for="gif in gifs">
            <div class="rounded overflow-hidden shadow-lg">
                <img class="w-full" :src="'https://image.tmdb.org/t/p/w200' + gif.poster_path" alt="Sunset in the mountains">
                <div class="px-6 py-4">
                    <div class="font-bold text-xl mb-2">
                        {{ gif.title }}
                        <small class="text-yellow-dark">{{ gif.vote_average }}</small>
                    </div>
                    <small class="text-grey text-base">
                        {{ gif.release_date }}
                    </small>
                    <p class="text-grey-darker text-base">
                        {{ gif.overview }}
                    </p>
                </div>
                <div class="px-6 py-4">
                    <span class="inline-block bg-purple-lighter rounded-full px-3 py-1 text-sm font-semibold text-purple-darkest mr-2">Language: {{ gif.original_language }}</span>
                    <span class="inline-block bg-purple-lighter rounded-full px-3 py-1 text-sm font-semibold text-purple-darkest mr-2">Popularity: {{ gif.popularity }}</span>
                </div>
            </div>
        </div>

    </div>
</template>

<script>
    export default {
        props: [ 'gifs' ]
    }
</script>

<style>
    ul{

    }
    li{
        list-style-type: none;
        float: left;
        margin: 20px;
    }
</style>