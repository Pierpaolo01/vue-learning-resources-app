<template>
    <li id="id">

        <base-card>

        <header>
            <h2> {{ title }} </h2>
            <base-button mode="flat" @click="deleteResource(id)">delete</base-button>
        </header>
        <p>{{ descr }}</p>
        <nav>
            <a :href="link">View resource</a>
        </nav>

        </base-card>
        
    </li>    
</template>

<script>


export default {
  props: {
      id: {
          type: String,
          required: true,
      },
      title: {
          type: String,
          required: true,
      },
      descr: {
          type: String,
          required: true,
      },
      link: {
          type: String,
          required: true,
      }
  },
  inject: ['deleteResource'],
}
</script>

<style scoped>
li {
  margin: auto;
  max-width: 40rem;
}

header {
  display: flex;
  justify-content: space-between;
  align-items: center;
}

h3 {
  font-size: 1.25rem;
  margin: 0.5rem 0;
}

p {
  margin: 0.5rem 0;
}

a {
  text-decoration: none;
  color: #ce5c00;
}

a:hover,
a:active {
  color: #c89300;
}

</style>
