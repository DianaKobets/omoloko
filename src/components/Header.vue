<template>
    <div class="title-container"> 
        <h1 class="title">IceCream Store</h1>

    <div class="buttons">
        <button class="filter">Фильтровать по названию</button>
        <button onclick=""><img src="./icons/корзина.png" alt="storage"></button>
    </div>
</div>
</template>

<style scoped>
div{
    background-color: rgb(245, 245, 245);
}

.title-container{
    width: 100%;
    display: flex;
    flex-direction: column;
    align-items: center;
    text-align: center;
    justify-content: center;
    background-size: cover;
}

.title{
    color: rgb(32, 35, 41);
    font-weight: 900;
    font-size: 3em;
    border-bottom: 3px solid rgb(255, 204, 0);
    margin-bottom: 2rem;
}

.buttons{
    display: flex;
    gap: 48rem;
}

button{
    width: fit-content;
    height: fit-content;
    font-size: 1rem;
    padding: 0.8rem 1.5rem;
    background-color: rgb(255, 204, 0);
    border: 2px solid transparent;
    border-radius: 30px;
    color:rgb(32, 35, 41);
    font-weight: 600;
    transition: transform .3s ease;
}

button:hover{
    transform: translateY(-3px);
}

img{
    width: 18px;
    margin: 1px 0 0 -1px;
}

.filter{
    margin: auto 0px;
}
</style>