<template>
  <div>
    <HeaderCont />
    <TitleCont name1="movie" name2="reference api" />
    <section class="cont__refer">
      <div class="container">
        <div class="movie__inner">
          <div class="movie__slider">
            <swiper
              :effect="'coverflow'"
              :grabCursor="true"
              :centeredSlides="true"
              :slidesPerView="'auto'"
              :coverflowEffect="{
                rotate: 50,
                stretch: 0,
                depth: 100,
                modifier: 1,
                slideShadows: false,
              }"
              :pagination="true"
              :autoplay="{
                delay: 2000,
                disableOnInteraction: false,
              }"
              :modules="modules"
              :initialSlide="2"
              class="mySwiper"
            >
              <swiper-slide v-for="(slider, index) in sliders" :key="slider.id">
                <a :href="`https://www.themoviedb.org/movie/${slider.id}`"></a>
                <span class="rank">{{ index + 1 }}</span>
                <img
                  :src="`https://image.tmdb.org/t/p/w500/${slider.poster_path}`"
                  :alt="slider.title"
                />
                <em>
                  <span class="title">{{ slider.title }}</span>
                </em>
              </swiper-slide>
            </swiper>
          </div>
          <div class="movie__search">
            <div class="movie_search">
              <div class="container">
                <form @submit.prevent="SearchMovies()">
                  <h3>검색하기</h3>
                  <input
                    type="search"
                    id="sarch"
                    placeholder="검색하세요!"
                    v-model="search"
                  />
                  <button type="submit" onClick="{onClick}">검색</button>
                </form>
              </div>
            </div>
          </div>
          <div class="movie__movies">
            <div class="container">
              <div class="movie__list">
                <ul>
                  <li v-for="movie in movies" :key="movie.id">
                    <a :href="`https://www.themoviedb.org/movie/${movie.id}`">
                      <img
                        :src="`https://image.tmdb.org/t/p/w500/${movie.poster_path}`"
                        :alt="movie.title"
                      />
                      <em>
                        <span class="title">{{ movie.title }}</span>
                        <span class="star">{{ movie.vote_average }}</span>
                      </em>
                    </a>
                  </li>
                </ul>
              </div>
            </div>
          </div>
          <!-- //movie__movies -->
        </div>
      </div>
    </section>
    <FooterCont />
    <ContactCont />
  </div>
</template>

<script>
import HeaderCont from "@/components/HeaderCont.vue";
import FooterCont from "@/components/FooterCont.vue";
import TitleCont from "@/components/TitleCont.vue";
import ContactCont from "@/components/ContactCont.vue";
import { ref } from "vue";
import { Swiper, SwiperSlide } from "swiper/vue";

// Import Swiper styles
import "swiper/css";

import "swiper/css/effect-coverflow";
import "swiper/css/pagination";

//import "./style.css";

// import required modules
import { EffectCoverflow, Pagination, Autoplay } from "swiper";

export default {
  components: {
    HeaderCont,
    FooterCont,
    TitleCont,
    ContactCont,
    Swiper,
    SwiperSlide,
  },

  setup() {
    const movies = ref([]);
    const sliders = ref([]);
    const search = ref("marvel");

    const SearchMovies = async () => {
      await fetch(
        `https://api.themoviedb.org/3/search/movie?api_key=f97a45e0661e5a39f4bebca0df9e45fe&language=ko-KOR&page=1&include_adult=false&query=${search.value}`
      )
        .then((response) => response.json())
        //.then((result) => console.log(result.cssRefer))

        .then((result) => {
          console.log(result.results);
          movies.value = result.results;
          search.value = "";
        })
        .catch((error) => console.log(error));
    };

    SearchMovies();

    const TopMovies = async () => {
      await fetch(
        `https://api.themoviedb.org/3/movie/popular?api_key=f97a45e0661e5a39f4bebca0df9e45fe`
      )
        .then((response) => response.json())
        //.then((result) => console.log(result.cssRefer))

        .then((result) => (sliders.value = result.results))
        .catch((error) => console.log("error", error));
    };

    TopMovies();

    return {
      movies,
      sliders,
      search,
      SearchMovies,
      modules: [EffectCoverflow, Pagination, Autoplay],
    };
  },
};
</script>

<style lang="scss">
.movie__slider {
  img {
    width: 100%;
    height: 100%;
  }
  .swiper-slide {
    width: 25%;
  }
  .swiper-wrapper {
    margin-bottom: 60px;
    .swiper-slide-active img {
      border: 4px solid var(--white);
      filter: brightness(140%);
    }
  }
  .rank {
    color: #000;
  }
  .title {
    color: #000;
  }
}

.movie__list {
  ul {
    display: flex;
    justify-content: space-between;
    flex-wrap: wrap;
    li {
      width: 19%;
      height: 40vh;
      margin-bottom: 5%;
      img {
        width: 100%;
        height: 100%;
      }
    }
  }
}

.movie__inner {
  ul {
    display: flex;
    justify-content: space-between;
    flex-wrap: wrap;
    li {
      position: relative;
      width: 23%;
      em {
        display: block;
        height: 80px;
        margin-bottom: 30px;
        font-family: var(--font-sub2);
      }
      .title {
        color: black;
        padding: 5px 0;
        display: inline-block;
      }
      .star {
        background: #fff;
        color: #000;
        position: absolute;
        left: 10px;
        top: 10px;
        width: 30px;
        height: 30px;
        border-radius: 100px;
        text-align: center;
        line-height: 30px;
        font-weight: bold;
      }
    }
  }
  a {
    color: var(--white);
  }
}

.movie_search {
  margin-bottom: 100px;
  .container {
    position: relative;
  }
  h3 {
    color: var(--white);
    font-size: 40px;
    text-indent: -9999px;
    height: 0;
  }
  input {
    background: rgb(204, 204, 204);
    border: 2px solid var(--white);
    border-radius: 50px;
    color: black;
    width: 100%;
    padding: 10px 30px;
    font-family: var(--font-main);
  }
  button {
    position: absolute;
    right: 3px;
    top: 3px;
    width: 40px;
    height: 40px;
    border-radius: 50%;
    border: 0;
    font-family: var(--font-sub1);
    cursor: pointer;
    z-index: 1000;
  }
}
</style>
