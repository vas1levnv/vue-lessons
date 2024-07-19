<template>
  <swiper
      @swiper="onSwiperInstance"
      :mousewheel="false"
      :keyboard="false"
      :allowTouchMove="false"
      :navigation="true"
      class="words-swiper">
    <swiper-slide v-for="(item, index) in words"  :key="index">
      <div class="words-swiper__item">
        <h2>{{item.word}}</h2>
        <div class="buttons">
          <button @click="slideToIndex(index)">
            знаю
          </button>
          <button @click="addSlide(item.word, item.id,)">
            не знаю
          </button>
        </div>
      </div>
    </swiper-slide>
  </swiper>
</template>
<script setup>
import { Swiper, SwiperSlide } from "swiper/vue";
import "swiper/css";
import {onMounted, ref, watch} from "vue";


const words = ref([
  {
    word: 'hello1',
    id: 1,
  },
  {
    word: 'hello2',
    id: 2,
  },
  {
    word: 'hello3',
    id: 3,
  },
  {
    word: 'hello4',
    id: 4,
  },
  {
    word: 'hello5',
    id: 5,
  },
]);

const swiperRef = ref(null);
const clikedIndex = ref(null);
const selectedSlide =ref(null);


const onSwiperInstance = (v) => {
  swiperRef.value = v;
};

const slideToIndex = (index) => {
  let nextSlide = Number(index  + 1)
  swiperRef.value.slideTo(nextSlide);
}

const addSlide = (word, id,index) => {
  clikedIndex.value = swiperRef.value.clickedIndex;
  let newSlides = words.value.filter(item => words.value.indexOf(item) !== clikedIndex.value);
  selectedSlide.value = {word: word, id: id};
  newSlides.push(selectedSlide.value)
  words.value = newSlides
};

</script>
<style>
* {
  box-sizing: border-box;
}
.words-swiper {
  width: 50dvh;
  margin: 0 auto;
}

.swiper-slide {
  background-color: darkslategray;
  padding: 2rem 2rem;
  display: flex;
  align-items: center;
  height: 50dvh;
}

.words-swiper__item {
  display: block;
  width: 100%;
  height: 100%;
}
</style>