<template>
<div>
    <div class="rounded p-3 h-full" style="background-color: rgb(81, 58, 58)">
          
        <img :src="item.image" class="rounded object-cover h-28 w-full"/>
        
        <p class="text-gray-200 text-lg">{{item.title}}</p>
        <p class="text-gray-300 text-sm">{{item.description}}</p>
    </div>
</div>
</template>

<script>
export default {
    props:['item'],
    data() {
        return {
        }
    }
}
</script>