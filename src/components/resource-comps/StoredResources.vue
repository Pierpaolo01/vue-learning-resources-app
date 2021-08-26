<template>
    <ul>
        <resources-li v-for="resource in resources" :key="resource.id" 
        :id="resource.id"
        :title="resource.title"
        :descr="resource.description"
        :link="resource.link"></resources-li>
    </ul>
</template>

<script>

import ResourcesLi from "./ResourcesLi.vue"

export default {
    components: {ResourcesLi},
    inject: ['resources'],
    
}
</script>

<style scoped>
 ul {
  list-style: none;
  margin: 0;
  padding: 0;
  margin: auto;
  max-width: 40rem;
}
</style>