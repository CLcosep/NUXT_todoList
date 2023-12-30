<template>
    <div>
        <header class="shadow-sm bg-white">
            <nav class="container mx-auto p-4 flex justify-between">
                <NuxtLink to="/" class="font-bold text-3xl text-[#beabed]">ToDoList</NuxtLink>
                <ul class="flex gap-5">
                    <li><NuxtLink to="/">Home</NuxtLink></li>
                    <li><NuxtLink to="/about">About</NuxtLink></li>
                    <li><NuxtLink to="/authentication/register" class="bg-[#beabed] text-white px-3 py-2 rounded-md text-white">Join now</NuxtLink></li>
                </ul>
            </nav>
        </header>

        <div class="container mx-auto p-4">
            <slot/>
        </div>
    </div>
</template>

<script setup>

</script>

<style lang="css" scoped>
    .router-link-exact-active {
        color: #beabed;
    }
</style>