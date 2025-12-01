<template>
    <div>
        <h1 class="emphasize">{{page.pageTitle}}</h1>
        <p>{{page.content}}</p>
    </div>  
</template>

<script>
export default {
        props: ['page']
    };
</script>

<style scoped>
    .emphasize {
        color: blue;
    }
</style>