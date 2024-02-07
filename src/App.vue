<template>
  <Navbar :pages="pages" :activePage="activePage" :groups="groups" :logo="logo" :logoUrl="logoUrl" :tables="tables">
  </Navbar>
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
      tables: {
        0: '0',
        1: '1',
        2: '2',
        3: '3',
        4: '4',
        5: '',
      },
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
              text: 'une soirée inoubliable !',
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
              // imageUrl: require('@/assets/leprechaun_playing.webp'),
              where: 'Salle des fêtes de BELLEVESVRE',
              when: 'Dès 19h !',
              who: 'Skull Darts 71',
              price: '5 euros',
              activity: 'Jouez et gagnez une boisson gratuite !'
            }
          ],
        }
      ],
      pageDetails: 0,
    }
  }
}
</script>

<style>
body {
  background-color: #060606 !important;
  background-color: black !important;
  height: 100vh;
}

h1,
p {
  font-family: 'Irish Grover', system-ui;
  color: gold;
  opacity: 0;
  animation: appear .3s .6s forwards ease;
  cursor: default;
}

li {
  list-style: none;
}

img {
  border-radius: 7px;
  transition: .3s ease;
  opacity: 0;
  animation: appear .3s .3s forwards ease;
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

/* SCROLLBAR Y */

/* Customizes the whole scrollbar */
::-webkit-scrollbar {
  width: 8px;
  /* Scrollbar width */
}

/* Customizes the scrollbar track (the part the thumb slides along) */
::-webkit-scrollbar-track {
  background: rgba(0, 128, 0, 0.452);
  /* Track color */
}

/* Customizes the scrollbar thumb (the part you drag) */
::-webkit-scrollbar-thumb {
  background: green;
  /* Thumb color */
}

/* Changes the thumb color on hover */
::-webkit-scrollbar-thumb:hover {
  background: gold;
}


/* ANIMATIONS */

@keyframes appear {
  0% {
    opacity: 0;
  }

  100% {
    opacity: 1;
  }
}

@keyframes colorize {
  0% {
    color: gold;
  }

  50% {
    color: green;
  }

  100% {
    color: gold;
  }
}

@keyframes moveLeft {

  100% {
    left: 0;
  }
}

@keyframes moveRight {
  0% {
    position: relative;
    right: -100%;
  }

  100% {
    right: 0;
  }
}

@keyframes moveTop {
  0% {
    position: relative;
    bottom: 500px;
  }

  100% {
    top: 0;
  }
}

@keyframes cloverLeft {
  25% {
    left: 20%;
  }

  50% {
    left: 5%;
  }

  75% {
    left: 15%;
  }

  100% {
    top: 100%;
    transform: rotate(360deg);
  }
}

@keyframes cloverRight {
  25% {
    right: 20%;
  }

  50% {
    right: 5%;
  }

  75% {
    right: 15%;
  }

  100% {
    top: 75%;
    transform: rotate(360deg);
  }
}
</style>
