<template>
  <Navbar :pages="pages" :activePage="activePage" :isHamburgerActive="isHamburgerActive"
    @toggle-hamburger="toggleHamburger" :groups="groups"></Navbar>
</template>

<script>
import Navbar from './components/Navbar.vue';

export default {
  name: 'App',
  components: {
    Navbar,
  },
  methods: {
    toggleHamburger() {
      this.isHamburgerActive = !this.isHamburgerActive;
    }
  },
  data() {
    return {
      isHamburgerActive: false,
      activePage: 0,
      groups: [
        {
          imageUrl: require('@/assets/blind_to_death_1024.svg'),
        },
        {
          imageUrl: require('@/assets/kouett_pounk_white.svg'),
        },
      ],
      pages: [
        {
          link: {
            url: '#',
            target: 'Home'
          },
          pageTitle: 'Bienvenue à la Saint Patrick !',
          pageContent: [
            {
              imageUrl: require('@/assets/irish_darts_1024x1024.svg'),
              heading: 'Skull Darts vous propose',
              text: 'Une soirée inoubliable !',
            }
          ],
        },
        {
          link: {
            url: '#',
            target: 'Details'
          },
          pageTitle: 'Informations :',
          pageContent: [
            {
              imageUrl: '',
              heading: '',
              text: '',
            }
          ],
        }
      ]
    }
  }
}
</script>

<style>
body {
  background-color: rgba(0, 0, 0, 0.959) !important;
}

h1,
p {
  font-family: 'Irish Grover', system-ui;
  color: gold;
}

img {
  border-radius: 7px;
}

#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;

}

#details p {
  font-size: 24px;
}
</style>
