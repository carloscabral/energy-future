<template>
  <div class="tint-2"> 
    <div class="container">
      <div class="layout">
        <!-- <Header /> -->
            <main>
                <slot />
            </main>
        <!-- <Footer /> -->
      </div>
    </div>
  </div>
</template>

<script>
import Header from "~/components/Header.vue";
import Footer from "~/components/Footer.vue";

export default {
  components: { Header, Footer },
  data: () => ({
    scroll: 0
  }),
};
</script>

<static-query>
query {
  metadata {
    siteName
  }
}
</static-query>

<style lang="scss">



</style>
