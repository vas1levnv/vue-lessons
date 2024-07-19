<template>
  <div class="words">
    <div class="words__header">
      <h1>Список слов</h1>
      <button class="words__show--all" @click="onShowWordAll">
        Показать все
      </button>
      <button class="words__hide--all" @click="onHideWordAll">
        Скрыть все
      </button>
    </div>
    <ul>
      <WordItem v-for="item in words"
                v-model="hideTranslate"
                @onMiddleHide="onMiddleHide"
                :key="item.id"
                :middleHide="newHide"
                :item="item"/>
    </ul>
  </div>
</template>

<script setup>
import {ref, watch} from "vue";
import WordItem from "@/components/WordItem.vue";

const words = ref([
  {
    word: 'hello',
    translation : 'привет',
    id: 1,
  },
  {
    word: 'hello',
    translation : 'привет',
    id: 2,
  },
  {
    word: 'hello',
    translation : 'привет',
    id: 3,
  },
  {
    word: 'hello',
    translation : 'привет',
    id: 4,
  },
  {
    word: 'hello',
    translation : 'привет',
    id: 5,
  },
]);

const hideTranslate = ref(true);
const newHide = ref('hide');
const onShowWordAll = () =>  {
  hideTranslate.value = false;
  newHide.value = 'show';
}
const onHideWordAll = () =>  {
  hideTranslate.value = true;
  newHide.value = 'hide';
}
const onMiddleHide = () => {
  newHide.value = 'middle';
}

watch(
    () => newHide.value,
    () => {
      console.log(newHide.value)
    }
)

</script>

<style scoped>

</style>