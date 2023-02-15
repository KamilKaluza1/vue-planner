<template>
    <nav>
        <router-link :to="{name: 'HomeView'}">Projects</router-link>
        <router-link :to="{name: 'AddProject'}">Add a New</router-link>
    </nav>
</template>

<style>
nav{
    text-align: center;
    margin: 40px auto;
}

nav a{
    display:inline-block;
    text-decoration: none;
    margin: 0 10px;
    font-size: 18px;

}

a.router-link-active{
    border-bottom: 2px solid green;
    padding-bottom:4px ;
}
</style>