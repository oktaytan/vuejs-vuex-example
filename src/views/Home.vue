<template>
  <div class="home">
    <BookmarkList/>
  </div>
</template>

<script>
// @ is an alias to /src
import BookmarkList from "@/components/BookmarkList.vue";

export default {
  name: "home",
  components: {
    BookmarkList
  }
};
</script>
