<script setup>
import HeaderBar from "@/components/HeaderBar.vue";
import axios from "axios";
import { defineProps, ref, watchEffect } from "vue";
import { useRouter } from "vue-router";

const router = useRouter()
const props = defineProps(["name"]);
const apiData = ref([]);
const apiKey = process.env.VUE_APP_API_KEY

const api = () => {
  axios
    .get(
      `https://api.themoviedb.org/3/search/multi?api_key=${apiKey}&query=${props.name}`
    )
    .then((res) => {
      apiData.value = res.data.results;
      apiData.value == '' ? router.push({ name: "HomePage"}) : null;
    })
    .catch((err) => {
      console.log(err);
    });
};
watchEffect(api);
</script>

<template>
 <!-- Header  -->
  <HeaderBar />

 <!-- Searching  List Movie -->
  <section class="search-list">
    <div class="container">
      <div class="movie_wrapper">
        <div class="movie-list" v-for="(data, index) in apiData" :key="data.id">
          <router-link :to="{ name: 'profile', params: { id: data.id } }">
            <img
              :src="`https://image.tmdb.org/t/p/w200${
                data.poster_path || data.backdrop_path || data.profile_path
              }`"
              :alt="data.title || data.name"
              class="movie_img"
              loading="lazy"
            />
            <span class="head-title"
              >{{ index + 1 }}. {{ data.title || data.name }}
            </span>
          </router-link>
        </div>
      </div>
    </div>
  </section>
</template>

<style lang="scss" scoped>
.search-list {
  background-color: #c2c2c2;
  min-height: 600px;
  .container {
    .movie_wrapper {
      display: flex;
      justify-content: center;
      flex-wrap: wrap;
      gap: 13px;
      padding-top: 20px;
      box-sizing: border-box;
      .movie-list {
        position: relative;
        display: flex;
        width: 200px;
        height: 300px;
        .movie_img {
          width: 200px;
          height: 300px;
        }
      }
      .head-title {
        position: absolute;
        top: 0;
        left: 0;
        margin: 0px auto;
        color: rgb(254, 254, 254);
        width: 100%;
        min-height: 20px;
        background: rgba(0, 0, 0, 0.4);
        text-align: center;
      }
    }
  }
}
@media screen and (max-width: 600px) {
 .movie-list {
  width: 150px !important;
  height: 200px !important;
        .movie_img {
          width: 150px !important;
          height: 200px !important;
        }
      }
}
</style>
