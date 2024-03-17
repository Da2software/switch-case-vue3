# switch-case-vue3

Components are located over **src/components/SwitchCase**

You can use this example if you do not want to install an external library.
 It is better to add this on the main js/ts file:

```js
...
import Switch from '@/components/SwitchCase/Switch.vue';
import Case from '@/components/SwitchCase/Case.vue';

...
app.component("Switch", Switch);
app.component("Case", Case);
...

```

The sample of how to use it is in  **src/views/HomeView.vue** and looks like this:

```html
<Switch v-model:caseValue="switchValue">
        <Case :value="1">
          <span class="label"> This is the First case</span>
        </Case>
        <Case :value="'hello'">
          <span class="label"> This is the Second case</span>
        </Case>
        <Case defaultCase>
          <span class="label"> There is no value match </span>
        </Case>
</Switch>
```

The main properties to make work the Switch Case component are the *provider* and *injector*, you can learn more about this on [Vue Documentation](https://vuejs.org/guide/components/provide-inject#working-with-reactivity).

## Project Setup

```sh
npm install
```

### Run

```sh
npm run dev
```
