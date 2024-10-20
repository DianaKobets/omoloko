<template>
    <div class="products-list">
        <div class="product-card" v-for="product in products" :key="product.id">
            <img :src="product.image" :alt="product.title"/>
            <div class="product-info">
                <h2>{{ product.title }}</h2>
                <div class="cost-wrapper">
                    <div class="cost-not-card">
                        <span class="cost">{{ product.cost }}₽</span>
                        <span class="cost-info">без карты</span>
                    </div>
                    <div class="cost-card">
                        <span class="cost">{{ product.costByCard }}₽</span>
                        <span class="cost-info">по карте</span>
                    </div>                
                </div>
            </div>
            <button onclick="">Добавить в корзину</button>
        </div>
    </div>
</template>

<script>
export default{
    name: 'ProductsList',
    props:{
        products:{
            type: Array,
            required: true
        },
    },
};
</script>

<style scoped>
.products-list{
    display: flex;
    flex-wrap: wrap;
    justify-content: space-evenly;
    columns: 3;
    background-color: rgb(245, 245, 245);
}

.product-card{
    height: 30vw;
    width: 25vw;
    background-color: white;
    color: rgb(32, 35, 41);
    font-size: 0.8rem;
    border-radius: 30px;
    padding: 1rem 2rem;
    margin: 50px 0px 0px 0px;
}

img{
    width: 70%;
    margin: 0 15%;
}

h2{
    line-height: normal;
    font-weight: 600;
    height: 60px;
}

.cost-wrapper{
    display: flex;
    flex-direction: row;
    padding: 0 10%;
}

.cost-card{
    display: flex;
    flex-direction: column;
    padding: 5px 20px;
    align-items: center;
    color: gray;
}

.cost-not-card{
    display: flex;
    flex-direction: column;
    padding: 5px 20px;
    align-items: center;
    color: #1E90FF;
}

.cost{
    font-weight: 600;
    font-size: 1rem;
}

span{
    font-weight: 400;
    font-size: 0.9rem;
}

button{
    padding: 10px 15px;
    background-color: rgb(255, 204, 0);
    border: 2px solid transparent;
    border-radius: 30px;
    color:rgb(32, 35, 41);
    font-weight: 600;
    margin: 5% 15%;
    transition: background-color .2s ease-in, color .2s ease-in;
}

button:hover{
    background-color: rgb(32, 35, 41) ;
    color:rgb(255, 204, 0);
}

</style>