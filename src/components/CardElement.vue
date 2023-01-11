<script>
export default{
    props: {
        imagePath: String,
        nameEl: String,
        archetype: String
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
            <h3>{{ nameEl }}</h3>
            <p>{{ archetype }}</p>
        </div>
    </div>
</template>

<style lang="scss" scoped>

    .card{
        width: calc((100% / 5) - 2rem);
        display: flex;
        flex-direction: column;
        margin: 1.5rem 1rem;
        background-color: #e5af6c;
        text-align: center;
        .image-box{
            width: 100%;
            height: 100%;
            object-fit: cover;

            img{
                width: 100%;
            }
        }
        .text-box{
            padding: 1rem;

            h3{
                color: white;
                text-transform: uppercase;
                margin-bottom: 1rem;
            }
        }
    }
</style>
