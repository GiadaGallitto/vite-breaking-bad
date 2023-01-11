<script>
export default{
    props: {
        imagePath: String,
        nameEl: String,
    }
}
</script>

<template>
    <div class="card">
        <!-- <p>{{imagePath}}</p> -->
        <div class="image-box">
            <img :src="imagePath" alt="">
        </div>
        <div class="text-box">
            <p>{{ nameEl }}</p>
        </div>
    </div>
</template>

<style scoped>
</style>
