<template>
  <div class="home">
    <SignIn />
  </div>
</template>

<script>
// @ is an alias to /src
import SignIn from "@/views/sign/SignIn.vue";
export default {
  name: "Home",
  components: {
    SignIn,
  },
};
</script>
