<template>
    <header>
    <div class="container">
        <h1>BOOLFIX</h1>
        <form action="" class="search_bar">
            <input type="text" v-model="searchText" placeholder="Cerca il tuo film o serie tv!">
            <button type="submit" @click.prevent="$emit('search', searchText)" >Ricerca</button>
        </form>   
    </div>

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

<style scoped lang="scss">
    @import "../assets/style/variabili.scss";
    header {
        background-color: $dark;
        height: 70px;
      
        .container {
            display: flex;
            justify-content: space-between;
            align-items: center;
        
            h1 {
                color: $boolfix;
                margin-bottom: 0px;
            }

            .search_bar{
                input {
                width: 200px;
                font-size: 13px;
                border-radius: 5px;
                border: 1px solid $light;
                background-color: $dark;
                color: $light;
                padding: 7px;
                cursor: pointer;
                height: 30px;
            }
        
            button {
            font-size: 20px;
            border: none;
            color: $light;
            background-color: $dark;
            margin: 0px 15px;
            line-height: 30px;
            vertical-align: middle;
            }
        }

    }
}
</style>