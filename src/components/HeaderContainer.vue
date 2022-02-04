<template>
    <header>

        <img src="../assets/booley-plus.png" alt="logo">

        <ul>
            <li>
                <a href=""> 
                    <i class="fas fa-home"></i>
                    HOME
                </a>
            </li>
            <li>
                <a href="">
                    <i class="fas fa-search"></i> 
                    CERCA
                </a>
            </li>
            <li>
                <a href="">
                    <i class="fas fa-star"></i>
                    LA MIA LISTA
                </a>
            </li>
        </ul>
        <div class="search-box">
            <input
            type="text"
            placeholder="Search Movies"
            v-model="searchInput"
            @keyup.enter="$emit('searchApi', searchInput)"
            >
            <button
            @click="$emit('searchApi', searchInput)"
            >
                GO
            </button>
        </div>

    </header>
</template>

<script>
export default {
    props: {

    },
    data() {
        return {
            searchInput: '',

        }
    }
    
}
</script>

<style lang="scss" scoped>

    header {
        height: 80px;
        padding: 0 10px;
        display: flex;
        align-items: center;
        justify-content: space-between;

        img {
            height: 60px;
        }

        ul {
            list-style: none;
            display: flex;

            li {
                padding: 0 15px;

                a {
                    color: #f9f9f9;
                    text-decoration: none;
                    font-weight: bold;
                }
            }
            
        }
        
    }
</style>