<template>
  <!--单例模式，name相同则复用一个无界实例，改变url则子应用重新渲染实例到对应路由 -->
  <WujieVue width="100%" height="100%" :name="appName" :url="vue2Url" :alive="false" :sync="true"></WujieVue>
</template>

<script>
export default {
  computed: {
    appName() {
      // return 'subVue'
      return this.$route.path;
    },
    vue2Url() {
      // return hostMap("//localhost:7200/") + `#/${this.$route.params.path}`;
      const uri = "//cube.hfe.test.sankuai.com/" + `#${this.$route.path.replace("/vue2-sub", "")}`;
      console.log("uri", uri);
      return uri;

      // return hostMap("//cube.hfe.test.sankuai.com/") + `#/${this.$route.params.path}`;
    },
  },
  methods: {
    jump(name) {
      this.$router.push({ name });
    },
  },
};
</script>

<style lang="scss" scoped></style>
