<template>
  <div>
    <div class="greeting">Hello {{name}}{{exclamationMarks}}</div>
    <button @click="decrement">-</button>
    <button @click="increment">+</button>
  </div>
</template>

<script lang="ts">

import Vue from 'vue';
import Component from 'vue-class-component';

@Component({
  props: {
    name: String,
    initialEnthusiasm: Number
  }
})

export default class HelloComponent extends Vue {
  readonly name: string;
  readonly initialEnthusiasm: number;
  private enthusiasm = this.initialEnthusiasm;

  increment() {
    this.enthusiasm++;
  }

  decrement() {
    if (this.enthusiasm > 1) {
      this.enthusiasm--;
    }
  }

  get exclamationMarks(): string {
    return Array(this.enthusiasm + 1).join('!');
  }
}

</script>

<style>
.greeting {
  font-size: 20px;
}
</style>
