<template>
    <header>

        <img src="../assets/booley-plus.png" alt="logo">

        <ul>
            <li> 
                <i class="fas fa-home"></i>
                HOME
            </li>
            <li @click="$emit('activeSearch')">
                <i class="fas fa-search"></i> 
                CERCA 
            </li>
            <li>
                <i class="fas fa-star"></i>
                LA MIA LISTA    
            </li>
        </ul>
        

    </header>
</template>

<script>
export default {
    props: {

    },
    data() {
        return {
            

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
                margin: 0 15px;
                cursor: pointer;
                font-weight: bold;
                color: #f9f9f9;
                text-decoration: none;

               
            }
            
        }
        
    }
</style>