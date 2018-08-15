<template>
    <div class="w-full mb-8">
        <div class="flex items-center border-b border-b-2 border-teal py-2">
            <input class="appearance-none bg-transparent border-none w-full text-grey-darker mr-3 py-1 px-2 leading-tight focus:outline-none"
                   type="text"
                   placeholder="Movie Title"
                   aria-label="Full name"
                   v-model="query" @keypress.enter="handleSearch">
            <button class="flex-no-shrink bg-teal hover:bg-teal-dark border-teal hover:border-teal-dark text-sm border-4 text-white py-1 px-2 rounded"
                    type="button"
                    @click="handleSearch">
                Search
            </button>
        </div>
    </div>
</template>

<script>
    export default{
        data (){
            return{
                query: ''
            }
        },
        methods:{
            handleSearch(){
                this.$emit('SearchRequested', this.query);
            }
        }
    }
</script>

<style>

</style>