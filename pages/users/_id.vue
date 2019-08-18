<template>
  <section class="container">
    <div>
      <h3>{{user.id}}</h3>
      <img :src="user.profile_image_url" width="120" alt="">
      <p>{{user.description || 'No description'}}</p>
      <p>
        <nuxt-link to="/">
          <small><b>トップへ戻る</b></small>
        </nuxt-link>
      </p>
      <h3>{{user.id}}さんの投稿一覧</h3>
      <ul>
        <li v-for="item in items" :key="item.id">
          <h4>
            <span>{{item.title}}</span>
          </h4>
          <div>{{item.body.slice(0,130)}}      </div>
          <p><a target="_blank" :href="item.url">{{item.url}}</a></p>
        </li>
      </ul>
    </div>
  </section>
</template>
<script>
import { mapGetters } from 'vuex'

export default {
  head(){
    return {
      title: this.user.id
    }
  },
  async asyncData({ route, store, redirect }){
    if(store.getters['users'][route.params.id]){
      return
    }
    try {
      await store.dispatch('fetchUserInfo', { id: route.params.id })
    } catch(e) {
      console.log("Redirect to '/'")
      console.log( e.message )
      redirect('/')
    }
  },
  computed: {
    user() {
      return this.$store.state.users[this.$route.params.id]
      //dataではなくVuexのstateを参照している サンプルコードと異なる
      // userid of undefined を参照した旨のエラー回避
    },
    items() {
    return this.$store.state.userItems[this.$route.params.id] || []
      //dataではなくVuexのstateを参照している サンプルコードと異なる
      // userid of undefined を参照した旨のエラー回避
  }
},

  ...mapGetters(['users','userItems'])
}
</script>
<style>
.container{
  min-height: 100vh;
  padding: 16px;
}
h3{
  margin: 16px 0;
  padding: 8px 0;
  border-bottom: solid 1px #e5e5e5;
}
li + li{
  margin: 16px 0;
}
p{
  margin: 8px 0;
}
</style>