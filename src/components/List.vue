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
    <ul class="words__list">
      <li class="words__item" v-for="item in words" :key="item.id">
        <div class="words__original">
          {{item.word}}
        </div>
        <div class="words__translation" :class="item.hideTranslation ? 'hide' : ''">
          <p>
            {{item.translation}}
          </p>
          <button @click="onHideWord(item.id)">
            Скрыть перевод
          </button>
          <button v-show="item.hideTranslation" class="words__show" @click="onShowWord(item.id)">
            Показать перевод
          </button>
        </div>
      </li>
    </ul>
  </div>
</template>

<script setup>

import {ref} from "vue";

const words = ref([
  {
    word: 'hello',
    translation : 'привет',
    id: 1,
    hideTranslation : true,
  },
  {
    word: 'hello',
    translation : 'привет',
    id: 2,
    hideTranslation : true,
  },
  {
    word: 'hello',
    translation : 'привет',
    id: 3,
    hideTranslation : true,
  },
  {
    word: 'hello',
    translation : 'привет',
    id: 4,
    hideTranslation : true,
  },
  {
    word: 'hello',
    translation : 'привет',
    id: 5,
    hideTranslation : true,
  },
]);

const onShowWordAll = () => {
  words.value.forEach((item) => {
    item.hideTranslation = false
  })
}

const onHideWordAll = () => {
  words.value.forEach((item) => {
    item.hideTranslation = true
  })
}

const onShowWord = (id) => {
  words.value.forEach((item) => {
    if(item.id === id) {
      item.hideTranslation = false
    }
  })
}

const onHideWord = (id) => {
  words.value.forEach((item) => {
    if(item.id === id) {
      item.hideTranslation = true
    }
  })
}

</script>

<style lang="scss">
</style>
