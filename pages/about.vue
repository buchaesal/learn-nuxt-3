<template>
  <q-page padding>
    <div class="q-my-xl text-center">
      <div class="text-h4">About</div>
      <p class="q-mt-sm text-grey-8">
        Vue & Nuxt Mastery Class 웹은 Nuxt3로 만들어졌습니다.
      </p>
      <div class="column">
        <RouterLink to="/">RouterLink Home</RouterLink>
        <RouterLink to="https://youtube.com/@gymcoding"
          >RouterLink Youtube</RouterLink
        >
        <br />
        <NuxtLink to="/">NuxtLink Home</NuxtLink>
        <NuxtLink to="https://youtube.com/@gymcoding"
          >NuxtLink Youtube</NuxtLink
        >
        <div class="q-gutter-y-sm q-mt-md">
          <div class="text-subtitle1 text-weight-bold">useState('counter')</div>
          <div>
            counter: {{ counter }}
            <q-btn
              label="counter"
              color="primary"
              dense
              no-caps
              @click="counter++"
            />
          </div>
          <div>
            sameCounter: {{ sameCounter }}
            <q-btn
              label="sameCounter"
              color="primary"
              dense
              no-caps
              @click="sameCounter++"
            />
          </div>
          <div>
            <q-btn label="clear" @click="clearNuxtState()" />
          </div>
        </div>
        <div class="q-gutter-y-sm q-mt-md">
          <div class="text-subtitle1 text-weight-bold">useCounterStore()</div>
          <div>count: {{ count }} doubleCount: {{ doubleCount }}</div>
          <div>
            <q-btn label="increment" @click="counterStore.increment" />
          </div>
        </div>

        <div class="q-gutter-y-sm q-mt-md">
          <div class="text-subtitle1 text-weight-bold">
            local vs session storage
          </div>
          <q-input v-model="localStorageColor" outlined />
          <q-input v-model="sessionStorageColor" outlined />
        </div>
      </div>
    </div>
  </q-page>
</template>

<script setup lang="ts">
import { useLocalStorage, useSessionStorage } from '@vueuse/core';

const counter = useState<number>('counter', () => 1);
const sameCounter = useState<number>('counter');

const counterStore = useCounterStore();
const { count, doubleCount } = storeToRefs(counterStore);

const localStorageColor = useLocalStorage('color-key', null);
const sessionStorageColor = useSessionStorage('color-key', null);

const config = useRuntimeConfig();
console.log('about config: ', config.public.clientConfigValue);
</script>
