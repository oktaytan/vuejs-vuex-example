<template>
  <div class="stats">
    <h1>A different component</h1>
    <p>There are currently {{countLinks}} links</p>

    <button @click="removeAllLinks" class="rm">Remove All Bookmarks</button>
    <p v-if="countLinks === 0">{{msg}}</p>
  </div>
</template>

<script>
import { mapGetters, mapActions } from "vuex";
export default {
  name: "Stats",
  data() {
    return {
      msg: ""
    };
  },
  computed: {
    ...mapGetters(["countLinks"])
  },
  methods: {
    ...mapActions(["removeAll"]),
    removeAllLinks() {
      this.removeAll().then(() => (this.msg = "They have been removed"));
    }
  }
};
</script>

<style>
</style>
