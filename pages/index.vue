<template>
  <div class="container">
    <header>
      <div class="branding">
        <logo />
        <h1 class="title">
          Linuxserver.io <span>Nano Store</span>
        </h1>
      </div>
      <nav>
        <ul>
          <li><a href="">All</a></li>
          <li><a href="">Under 5,000</a></li>
          <li><a href="">Under 10,000</a></li>
          <li><a href="">Under 20,000</a></li>
        </ul>
      </nav>
    </header>
    <div class="product-items">
      <item
      v-for="item in items"
      :key="item.id"
      :item="item"
      ></item>
      </div>
    </div>
  </div>
</template>

<script>
import Logo from '~/components/Logo.vue'
import Item from '~/components/Item.vue'

export default {
  components: {
    Logo,
    Item
  },
  computed: {
    items: function() {
      return this.$store.state.items.list
    }
  }
}
</script>
<style lang="scss">

.container {
  margin: 0 auto;
  min-height: 100vh;
  display: flex;
  flex-direction: column;
  header {
    display: flex;
    width: 100%;
    .branding {
      display: flex;
      align-items: center;
      flex: 1;
      max-width: 500px;
      padding: 20px;
      h1 {
        font-size: 25px;
        font-weight: bold;
        text-transform: uppercase;
        display: flex;
        flex-direction: column;
        margin-left: 10px;
        span {
          font-size: 20px;
          font-weight: normal;
          letter-spacing: 9px;
        }
      }
    }
  }
}
.product-items {
  display: flex;
  flex-wrap: wrap;
  margin: 50px 20px;
}
nav {
  display: flex;
  flex: 1;
  align-items: center;
  ul {
    list-style: none;
    margin: 0;
    padding: 0;
    display: flex;
    li {
      a {
        padding: 25px;
        text-decoration: none;
        color: #35495e;
        font-weight: bold;
      }
    }
  }
}


.title {
  font-family: 'Quicksand', 'Source Sans Pro', -apple-system, BlinkMacSystemFont,
    'Segoe UI', Roboto, 'Helvetica Neue', Arial, sans-serif;
  display: block;
  font-weight: 300;
  font-size: 25px;
  color: #35495e;
  letter-spacing: 1px;
}

.subtitle {
  font-weight: 300;
  font-size: 42px;
  color: #526488;
  word-spacing: 5px;
  padding-bottom: 15px;
}

.links {
  padding-top: 15px;
}
</style>
