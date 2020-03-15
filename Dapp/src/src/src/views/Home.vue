<template>
  <div class="home-page" style="box-shadow:0px;" >
    <div class="banner" style="background-color:white;box-shadow:0px;">
      <div class="container" style="">
        <h1 class="logo-font" style="color:green;">Xperience</h1>
        <h1> </h1>
      </div>
 
    <img src="./Paradise.png" style="width:1455px;border-radius:38px;margin-top:10px ">
  </div>
  </div>
</template>

<script>
import { mapGetters } from "vuex";
import RwvTag from "@/components/VTag";
import { FETCH_TAGS } from "@/store/actions.type";

export default {
  name: "home",
  components: {
    RwvTag
  },
  mounted() {
    this.$store.dispatch(FETCH_TAGS);
  },
  computed: {
    ...mapGetters(["isAuthenticated", "tags"]),
    tag() {
      return this.$route.params.tag;
    }
  }
};
</script>
