<template>
  <div class="single-song mb-2 d-flex flex-column justify-content-around align-items-center text-center">
        <div class="image">
            <img :src="singleSong.poster" class="img-fluid" :alt="singleSong.title">
        </div>
        <h3 class="title">
            {{singleSong.title}}
        </h3>
        <div class="text">
            <span class="otherText d-block">
                {{singleSong.author}}
            </span>
            <span style="font-size:80%;" class="otherText d-block">
                {{singleSong.year}}
            </span>
        </div>
    </div>
</template>

<script>
export default {
    name: 'SongCard',
    props: ['singleSong']
}
</script>

<style lang="scss" scoped>
@import '@/styles/general.scss';

.single-song{
    background: $thirdcolor;
    min-height: 300px;
    flex-basis: 200px;
    flex-wrap: wrap;
    .image{
        width: 150px;
        img{
            width: 100%;
        }
    }
    .title{
        text-transform: uppercase;
        color: white;
        font-weight: 600;
        font-size: 1rem;
    }
    .otherText{
        color: $secondcolor;
    }
}
</style>
