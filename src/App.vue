<template>
  <div id="app">
    <section v-for="(sample, index) in samples" :key="`sample-${index}`">
      <pre>{{ htmlCode(sample) }}</pre>
      <avatar
        :fullname="sample.fullname"
        :size="sample.size"
        :image="sample.image"
        :radius="sample.radius"
        :color="sample.color"
      />
    </section>
  </div>
</template>

<script>
import Avatar from './components/Avatar.vue'

export default {
  name: 'App',
  components: { Avatar },
  data: () => ({
    samples: [
      { fullname: 'My Fabulous Component' },
      { fullname: 'Foo Bar', size: 60 },
      { image: 'https://placekitten.com/200/200', size: 96 },
      { image: 'https://placekitten.com/250/250', size: 96, radius: 0 },
      { fullname: 'Foo Bar', radius: 25, color: 'red' }
    ]
  }),
  methods: {
    htmlCode (sample) {
      let html = '<avatar '
      html += sample.fullname ? ` fullname="${sample.fullname}"` : ''
      html += sample.size ? ` :size="${sample.size}"` : ''
      html += sample.image ? ` image="${sample.image}"` : ''
      html += sample.radius ? ` radius="${sample.radius}"` : ''
      html += sample.color ? ` color="${sample.color}"` : ''
      html += ' />'
      return html
    }
  }
}
</script>

<style>
  #app {
    font-family: sans-serif;
    width: 50%;
    min-width: 50rem;
    margin: 2rem auto;
  }
  section {
    display: flex;
    flex-flow: row nowrap;
    justify-content: space-between;
    align-items: center;
    padding: 1rem 0;
    border-bottom: 1px solid black;
  }
  section:last-child {
    border-bottom: none;
  }
</style>
