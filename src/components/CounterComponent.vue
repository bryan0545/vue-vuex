<template>
  <h1>Counter - Vuex</h1>
  <h2>Direct Access: {{ $store.state.counter.count }}</h2>
  <h2>Computed: {{ countComputed }}</h2>
  <h2>MapState: {{ count }}</h2>
  <h2>Last Mutation: {{ lastMutation }}</h2>
  <h2>Direct Getter: {{ $store.getters["counter/squareCount"] }}</h2>
  <button @click="increment">+1</button>
  <button @click="incrementBy(5)">+5</button>
  <button @click="incrementRandomInt" :disabled="isLoading">Random</button>
</template>

<script>
import { mapState, mapActions } from "vuex";

export default {
  computed: {
    countComputed() {
      return this.$store.state.counter.count;
    },
    ...mapState("counter", ["count", "lastMutation", "isLoading"]),
  },
  methods: {
    increment() {
      this.$store.commit("counter/increment");
    },
    incrementBy(amount) {
      this.$store.commit("counter/incrementBy", amount);
    },
    ...mapActions("counter", ["incrementRandomInt"]),
    // ...mapActions({
    //   randomInt: "incrementRandomInt",
    // }),
  },
};
</script>

<style></style>
