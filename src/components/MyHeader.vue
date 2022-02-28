<template>
    <header>
        <form action="">
            <input type="text" v-model="searchText">
            <button type="submit" @click.prevent="$emit('search', searchText)" >Ricerca</button>
        </form>   
    </header>

  
</template>

<script>
export default {
    name: 'MyHeader',
    data() {
        return {
            searchText:''
        }
    }
}
</script>

<style>

</style>