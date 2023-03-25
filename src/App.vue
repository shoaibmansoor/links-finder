<template>
  <TheHeader></TheHeader>
  <TheSwitch
    v-on:show-resource="showResources = true"
    v-on:add-resource="showResources = !showResources"
  >
  </TheSwitch>

  <div v-show="showResources">
    <AppResource
      v-for="r of resources"
      :key="r.id"
      :id="r.id"
      :title="r.title"
      :description="r.description"
      :link="r.link"
      v-on:delete-resource="deleteResource"
    ></AppResource>
  </div>

  <div v-show="!showResources">
    <keep-alive>
      <AddResource v-on:add-resource="addResource"></AddResource>
    </keep-alive>
  </div>
</template>

<script>
import TheHeader from './components/TheHeader.vue'
import AppResource from './components/AppResource.vue'
import AddResource from './components/AddResource.vue'
import TheSwitch from './components/TheSwitch.vue'

export default {
  name: 'App',
  components: {
    TheHeader,
    AppResource,
    AddResource,
    TheSwitch,
  },
  data() {
    return {
      showResources: true,
      resources: [
        {
          id: 0,
          title: 'Offical Guide',
          description: 'The official Vue.js Documentation',
          link: 'https://vuejs.org/',
        },
        {
          id: 1,
          title: 'Google',
          description: 'Learn to google',
          link: 'https://google.com',
        }
      ]
    };
  },
  methods: {
    addResource(_data) {
      _data['id'] = this.resources.length;
      this.resources.push(_data);
    },
    deleteResource(resource) {
      const index = this.resources.findIndex((it) => it.id == resource.id);
      this.resources.splice(index, 1);
    },
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  /* -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50; */
}

body {
  margin: 0px;
}

.box-shadow {
  box-shadow: -2px 2px 5px 0px rgba(0, 0, 0, 0.5);
}
</style>
