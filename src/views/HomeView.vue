<script setup lang="ts">
/* You can put these components over main.ts/main.js and use the app.use(Switch and Case components instance)  */
import Switch from '@/components/SwitchCase/Switch.vue';
import Case from '@/components/SwitchCase/Case.vue';
import { ref } from 'vue';

const switchValue = ref(undefined)
const setValue = (value: any) => {
  // console.log(value);
  switchValue.value = value;
}
</script>

<template>
  <header>
    <h1 class="title">Custom "Switch Case" component Vue 3</h1>
  </header>
  <main>
    <div class="container">
      <div class="options">
        <button class="btn-option" @click="setValue(1)">Set Number 1</button>
        <button class="btn-option" @click="setValue(2)">Set Number 2</button>
        <button class="btn-option" @click="setValue('text')">Set String text</button>
        <button class="btn-option" @click="setValue(true)">Set Number true</button>
        <button class="btn-option" @click="setValue(false)">Set Number false</button>
      </div>
    </div>
    <div class="content-display">
      <Switch v-model:caseValue="switchValue">
        <Case :value="1">
          <span class="label"> This is the First case</span>
        </Case>
        <Case :value="2">
          <span class="label"> This is the Second case</span>
        </Case>
        <Case :value="'text'">
          <span class="label"> This is the text case</span>
        </Case>
        <Case :value="true">
          <span class="label"> This is the TRUE case</span>
        </Case>
        <Case :value="false">
          <span class="label"> This is the FALSE case</span>
        </Case>
        <Case defaultCase>
          <span class="label"> There is no value match </span>
        </Case>
      </Switch>
    </div>
  </main>
</template>
<style scoped>
.title {
  text-align: center;
  margin-bottom: 24px;
}
main {
  display: flex;
  width: 720px;
}

.container {
  display: grid;
  grid-template-columns: auto auto;
  width: 100%;
  margin: auto;
}

.options {
  width: fit-content;
  display: grid;
}

.options .btn-option {
  margin: 16px;
  width: fit-content;
  display: inline-block;
  outline: none;
  cursor: pointer;
  font-weight: 600;
  border-radius: 3px;
  padding: 12px 24px;
  border: 0;
  color: #000021;
  background: #1de9b6;
  line-height: 1.15;
  font-size: 16px;

  :hover {
    transition: all .1s ease;
    box-shadow: 0 0 0 0 #fff, 0 0 0 3px #1de9b6;
  }

}

.content-display {
  border: 1px solid #1de9b6;
  min-width: 300px;
}

.label {
  margin: 16px;
  color: #fff;
  font-size: 24px;
  font-family: Arial, Helvetica, sans-serif;
}
</style>
