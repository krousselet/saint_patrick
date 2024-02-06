<template>
  <Navbar :pages="pages" :activePage="activePage" :groups="groups" :logo="logo" :logoUrl="logoUrl"></Navbar>
</template>

<script>
import Navbar from './components/Navbar.vue';

export default {
  name: 'App',
  components: {
    Navbar,
  },
  data() {
    return {
      logo: require('@/assets/logo.svg'),
      logoUrl: 'https://www.facebook.com/p/Skull-Darts-71-100091328505582/?paipv=0&eav=AfbEQcnK0hrl5AlWq-9Fz-R8o1uA_m8gPtoaNvWGt4tS05H5GpBvBsKNRuX0Zbg9LJQ&_rdr',
      activePage: 0,
      groups: [
        {
          imageUrl: require('@/assets/blind_to_death_1024.svg'),
          url: 'https://www.facebook.com/BlindIIDeaf',
        },
        {
          imageUrl: require('@/assets/kouett_pounk_white.svg'),
          url: 'https://www.facebook.com/kouettnos',
        },
        {
          imageUrl: require('@/assets/zictag-vector.svg'),
          url: 'https://www.facebook.com/profile.php?id=100089758185054',
        },
      ],
      pages: [
        // HOME PAGE
        {
          link: {
            url: '#',
            target: 'Home'
          },
          pageTitle: 'Saint Patrick\'s night party',
          pageContent: [
            {
              imageUrl: require('@/assets/irish_darts_bis_1024x1024.svg'),
              heading: 'Skull Darts 71 vous propose',
              text: 'Une soirée inoubliable !',
            }
          ],
        },
        // DETAILS PAGE
        {
          link: {
            url: require('@/assets/leprechaun_playing.webp'),
            target: 'Details'
          },
          pageTitle: 'Informations :',
          pageContent: [
            {
              imageUrl: require('@/assets/leprechaun_playing.webp'),
              where: 'Salle des fêtes de BELLEVESVRE',
              who: 'Skull Darts 71',
              price: '5 euros',
              activity: 'Jouez et gagnez une boisson gratuite !'
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
  background-color: #060606 !important;
  background-color: black !important;
}

h1,
p {
  font-family: 'Irish Grover', system-ui;
  color: gold;
}

li {
  list-style: none;
}

img {
  border-radius: 7px;
  transition: .3s ease;
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
