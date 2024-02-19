<template>
  <Navbar :pages="pages" :activePage="activePage" :groups="groups" :logo="logo" :logoUrl="logoUrl" :index="index"
    :isPlaying="isPlaying" @toggle-play-pause="togglePlayPause">
  </Navbar>
  <!-- Toggle button once audio is playing -->
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
      index: 0,
      sound: null, // For storing the audio element
      isPlaying: false, // To track play/pause state
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
              // imageUrl: require('@/assets/irish_darts_bis_1024x1024.svg'),
              videoUrl: require('@/assets/irish_darts_bis_1024x1024_png_animation.mp4'),
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
              date: 'Samedi 16 mars',
              when: 'Dès 19h !',
              who: 'Skull Darts 71',
              price: '5 euros',
              activity: 'Jouez et gagnez une boisson gratuite !',
              bonus: 'Un kilt = une boisson offerte !',
            }
          ],
        }
      ],
      pageDetails: 0,
    }

  },
  created() {
    // Instantiate the audio object and autoplay
    this.sound = new Audio(require('@/assets/ev-chistr-Ta-Laou.mp3'));
    this.sound.addEventListener('ended', this.restartSong);
  },
  methods: {
    togglePlayPause() {
      if (this.isPlaying) {
        this.sound.pause();
      } else {
        this.sound.play().catch(error => console.error("Audio play failed", error));
      }
      this.isPlaying = !this.isPlaying;
    },
    restartSong() {
      this.sound.currentTime = 0;
      this.sound.play().catch(error => console.error("Une erreur est survenue", error));
    },
  },
  beforeDestroy() {
    if (this.sound) {
      this.sound.removeEventListener('ended', this.restartSong);
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

/* BOOTSTRAP CUSTOM MADE CLASS FLUID */
.video-fluid {
  max-width: 90%;
  height: auto;
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
  0% {
    left: -50%;
  }

  100% {
    left: 0;
  }
}

@keyframes moveRight {
  0% {
    right: -50%;
  }

  100% {
    right: 0;
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
