<template>
  <div class="hello">
    <div class="left">
      <h1 class="title">{{title}}</h1>

      <form @submit.prevent="addLink">
        <input type="text" class="link-input" placeholder="Add a link" v-model="newLink">
      </form>

      <ul>
        <li v-for="(link,index) in links" :key="index">
          {{link}}
          <button @click="removeLink(index)" class="rm">Remove</button>
        </li>
      </ul>
    </div>
    <div class="right">
      <Stats/>
    </div>
  </div>
</template>

<script>
import Stats from "@/components/Stats.vue";
import { mapState, mapMutations, mapActions } from "vuex";

export default {
  name: "BookmarkList",
  data() {
    return {
      newLink: ""
    };
  },
  components: {
    Stats
  },
  computed: {
    ...mapState(["title", "links"])
  },
  methods: {
    ...mapMutations(["ADD_LINK"]),
    ...mapActions(["remove"]),
    addLink() {
      this.ADD_LINK(this.newLink);
      this.newLink = "";
    },
    removeLink(link) {
      this.remove(link);
    }
  }
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
html,
.hello {
  display: grid;
  grid-template-columns: repeat(2, 50%);
  grid-template-rows: 100%;
  grid-template-areas: "left right";
  height: 100%;
  background-color: rgb(146, 184, 202);
}

.left,
.right {
  padding: 30px;
}

ul {
  list-style-type: none;
  padding: 0;
}
ul li {
  padding: 20px;
  background: white;
  margin-bottom: 8px;
  box-shadow: 3px 3px 10px rgba(0, 0, 0, 0.3);
  border-radius: 8px;
  cursor: pointer;
  display: flex;
  justify-content: space-between;
  align-items: center;
}

.right {
  grid-area: right;
  background-color: #e9e9e9;
}

input {
  border: none;
  padding: 20px;
  width: calc(100% - 40px);
  box-shadow: 0 5px 5px lightgrey;
  margin-bottom: 50px;
  outline: none;
}

.rm {
  float: right;
  background: none;
  cursor: pointer;
  background-color: #f03d3d;
  border: none;
  padding: 10px 15px;
  border-radius: 5px;
  color: #fff;
  transition: background-color 0.25s ease;
}

.rm:hover {
  background-color: #ac2c2c;
}
</style>
