<template>
  <div>
  <Header></Header>
    <div>
        <ul>
            <li v-for="list in lists">
            <router-link :to="'/content/' + list.id">{{ list.title }}</router-link>
            </li>
        </ul>
    </div>
  <Footer></Footer>
  </div>
</template>

<script>
import Header from '../components/header.vue'
import Footer from '../components/footer.vue'
export default {
  components: { Header, Footer },
  data () {
    return {
      lists: []
    }
  },
  created () {
    this.getData()
  },
  methods: {
    getData () {
      this.$api.get('main?name=dcg&type=news', null, r => {
        console.log(r.data)
        this.lists = r.data
      })
    }
  }
}
</script>