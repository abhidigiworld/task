<template>
    <div>
        <p>Task Manager</p>
        <span class="close"> <NuxtLink to="/">X</NuxtLink> </span>
    </div>
</template>
<style scoped>
    div{
        display: flex;
        align-items: center;
        color: rgb(15, 14, 14);
        background-color: rgba(72, 73, 75, 0.438);
        font-weight: bold;
        position: relative;
    }
    p{
        padding-left: 2rem;
    }
    
    a{
        text-decoration: none;
        color: grey;
    }

    a:hover{
        color: black;
    }

    .close{
        position: absolute;
        right: 3rem;
        font-size: 2rem;
    }
</style>