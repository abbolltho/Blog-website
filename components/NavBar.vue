<template>
    <div class="flex justify-center p-1 fixed top-1 w-full z-50">
        <div class="p-3 px-5 rounded text-gray-100 flex flex-row justify-between font-semibold navBar" >
            <NuxtLink to="/" class="hover:underline">Home</NuxtLink>
            <div></div>
            <div></div>
            <div></div>
            <NuxtLink to="/about-the-blog" class="hover:underline">About the blog</NuxtLink>
            <NuxtLink to="/about-me" class="hover:underline">About me</NuxtLink>
            <NuxtLink to="/contacts" class="hover:underline">Contacts</NuxtLink>
        </div>
    </div>
</template>

<style>
    .navBar{
        background-color: rgb(81, 58, 58);
        width: 70%;
        height: 50px;
    }
</style>