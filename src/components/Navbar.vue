<template>
    <nav class="navbar navbar-expand-lg bg-body-transparent">
        <div class="container-fluid">
            <img :src="logo" alt="logo skulldarts" id="logo-skulldarts" @click.prevent="openLogoUrl(logoUrl)">
            <button class="btn" @click="$emit('toggle-play-pause')">
                <span v-if="!isPlaying" class="btn btn-success">Jouer</span>
                <span v-else class="btn btn-danger">Pause</span>
            </button>
            <button id="hamburger" class="navbar-toggler" type="button" data-bs-toggle="collapse"
                data-bs-target="#navbarSupportedContent" aria-controls="navbarSupportedContent" aria-expanded="false"
                aria-label="Toggle navigation">
                <span class="navbar-toggler-icon"></span>
            </button>
            <div class="collapse navbar-collapse" id="navbarSupportedContent">
                <ul class="navbar-nav me-auto mb-2 mb-lg-0">
                    <li class="nav-item" v-for="(page, pageIndex) in pages" :key="pageIndex">
                        <a class="nav-link text-success" aria-current="page" href="#"
                            @click.prevent="activePage = pageIndex" :class="{ active: activePage === pageIndex }">{{
                                page.link.target }}</a>
                    </li>
                </ul>
            </div>
        </div>
    </nav>
    <div id="container-fluid">
        <h1 id="title" class="m-5">{{ pages[activePage].pageTitle }}</h1>
        <div v-if="activePage === 0" id="home" v-for="(item, pageIndex) in pages[0].pageContent" :key="pageIndex">
            <video autoplay loop muted playsinline class="video-fluid border-radius">
                <source :src="item.videoUrl" type="video/mp4">
                Votre navigateur ne supporte pas cette video.
            </video>
            <div class="catch-container">
                 <p class="m-5" id="first-p">{{ item.heading + ' ' + item.text }}</p>
            </div>
        </div>
        <div v-if="activePage === 1" id="details">
            <img src="../assets/clover.webp" alt="image d'un trèfle" id="clover-left">
            <img src="../assets/clover.webp" alt="image d'un trèfle" id="clover-right">
            <div class="container">
                <p v-for="(item, index) in pages[1].pageContent[index]" :key="index" :id="index">
                    {{ item }}
                </p>
            </div>
            <img class="img-fluid" :src="pages[1].link.url" :alt="'image d\'un logo'" id="leprechaun_playing">
        </div>
        <div v-if="activePage === 2" id="informations">
            <div class="container" v-for="(item, index) in pages[2].pageContent" :key="index" :id="index">
                <div id="title-container" class="appear-1">
                    <h2>{{ item.titleAlcohol }}</h2>
                </div>
                <div id="law">
                    <div id="paragraph-alcohol-one" class="my-3 appear-2">
                        <p class="justify">{{ item.paragraphAlcoholOne }}</p>
                    </div>
                    <div id="paragraph-alcohol-one-details" class="my-1 appear-3">
                        <p class="justify">{{ item.paragraphAlcoholTwo }}</p>
                    </div>
                    <div id="law-article" class="my-1 appear-4">
                        <p>{{ item.lawArticleOne }}</p>
                    </div>
                    <div id="paragraph-alcohol-three" class="my-3 appear-5">
                        <p class="justify"> {{ item.paragraphAlcoholThree }}</p>
                    </div>
                    <div id="law-article" class="my-1 appear-6">
                        <p>{{ item.lawArticleTwo }}</p>
                    </div>
                    <div id="paragraph-alcohol-four" class="my-3 appear-7">
                        <p>{{ item.paragraphAlcoholFour }}</p>
                    </div>
                    <div id="law-article" class="my-1 appear-8">
                        <p>{{ item.lawArticleThree }}</p>
                    </div>
                    <div id="danger" class="my-3 appear-9">
                        <p>{{ item.danger }}<span id="danger-span" class="appear-10">{{ item.dangerSpan }}</span></p>
                    </div>
                </div>
            </div>
        </div>
        <div v-if="activePage === 3" id="jeu">
            <div class="container" v-for="(item, index) in pages[3].pageContent" :key="index" :id="index">
                <div id="title-container" class="appear-1">
                    <h2>{{ item.titleGame }}</h2>
                </div>
                <div id="paragraph-game-one" class="my-5 appear-2">
                    <p class="justify">{{ item.paragraphGameOne }}</p>
                </div>
                <div id="paragraph-game-two" class="appear-3">
                    <p class="justify">{{ item.paragraphGameTwo }}</p>
                </div>
                </div>

            </div>
        <!-- UNOFFICIAL FOOTER -->
        <div id="groups" class="m-5">
            <ul id="list">
                <li v-for="group in groups" :key="group.url"><img class="img-fluid logo m-2" :src="group.imageUrl"
                        :alt="'image d\'un logo'" @click.prevent="openNewTab(group.url)">
                </li>
            </ul>
        </div>
    </div>
    
</template>

<script>
export default {
    methods: {
        openNewTab(url) {
            window.open(url, '_blank');
        },
        openLogoUrl(logoUrl) {
            window.open(logoUrl, '_blank');
        },
    },
    computed: {
        playUrl() {
            return this.isPlaying
                ? require('@/assets/pause.png')
                : require('@/assets/play.png');
        },
    },
    props: {
        activePage: Number,
        logoUrl: String,
        logo: String,
        tables: Object,
        pageDetails: Number,
        index: Number,
        videoUrl: String,
        isPlaying: Boolean,
        groups: {
            type: Object,
            default(rawProps) {
                return (() => [])
            }
        },
        pages: {
            type: Object,
            default(rawProps) {
                return (() => [

                ])
            }
        }
    },
    emits: ['toggle-play-pause']
}
</script>

<style scoped>
/* ***** LAW DIV *****/

.appear-1 {
    opacity: 0;
    animation: appear .5s .5s linear forwards;
}

.appear-2 {
    opacity: 0;
    animation: appear .5s .8s linear forwards;
}

.appear-3 {
    opacity: 0;
    animation: appear .5s 1.1s linear forwards;
}

.appear-4 {
    opacity: 0;
    animation: appear .5s 1.4s linear forwards;
}

.appear-5 {
    opacity: 0;
    animation: appear .5s 1.7s linear forwards;
}

.appear-6 {
    opacity: 0;
    animation: appear .5s 2s linear forwards;
}

.appear-7 {
    opacity: 0;
    animation: appear .5s 2.3s linear forwards;
}

.appear-8 {
    opacity: 0;
    animation: appear .5s 2.5s linear forwards;
}

.appear-9 {
    opacity: 0;
    animation: appear .5s 2.8s linear forwards;
}

.appear-10 {
    opacity: 0;
    animation: appear .5s 3.1s linear forwards;
}

.catch-container {
    overflow-x: hidden;
}

h2 {
    animation: appear .5s .5s forwards, colorize .5s .5s ease forwards appear .5s .5s linear forwards;
}

#law {
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;
    text-align: justify;
    animation: appear .5s .5s forwards;
}

#paragraph-one-alcohol {
    animation: left .5s 1s forwards;
}

.law-article {
    text-align: right !important;
    display: flex !important;
    justify-content: right !important;
    align-items: center !important;
}

#danger-span {
    color: red;
}




.btn,
.btn-success,
.btn-danger {
    transition: .5s ease !important;
}

#play-music {
    width: 50px;
    height: 50px;
    background-color: white;
}

#clover-left {
    position: absolute;
    left: 20px;
    top: 10%;
    width: 50px;
    height: 50px;
    animation: cloverLeft 10s .5s infinite alternate;
    z-index: 10;
    opacity: 1;
}

#clover-right {
    position: absolute;
    right: 20px;
    top: 10%;
    width: 50px;
    height: 50px;
    animation: cloverRight 10s .5s infinite alternate;
    z-index: 10;
    opacity: 1;
}

.border-radius {
    border-radius: 7px;
}

.justify {
    text-align: justify;
}

/* MEDIAS QUERIES */
@media (min-width: 993px) {
    a {
        transition: .5s ease !important;
    }

    .logo:hover {
        transform: scale(1.5);
        transition: .3s ease;
    }



    #leprechaun_playing:hover {
        transform: scale(.8) rotate(15deg);

        transition: .3s ease;
    }
}

/* HEADER */

.navbar-toggler-icon {
    background-image: url("data:image/svg+xml,%3Csvg xmlns='http://www.w3.org/2000/svg' width='30' height='30' viewBox='0 0 30 30'%3E%3Cpath stroke='rgba(25, 135, 84, 1)' stroke-linecap='round' stroke-miterlimit='10' stroke-width='2' d='M4 7h22M4 15h22M4 23h22'/%3E%3C/svg%3E");

}

#logo-skulldarts {
    height: 75px;
    width: 75px;
    border-radius: 50%;
    cursor: pointer;
}



.active {
    color: gold !important;
    transition: .5s ease !important;
    border: 0 !important;
    border-bottom: 2px solid gold !important;
}

#list {
    display: flex;
    flex-direction: row;
    justify-content: space-around;
    align-items: center;
    cursor: default;
}

#list li img {
    max-width: 200px;
    max-height: 100px;
}

#title {
    position: relative;
    left: -100%;
    display: flex;
    justify-content: center;
    align-items: center;
    overflow-x: hidden;
    animation: appear .3s .3s forwards ease, colorize 1.2s .7s forwards ease, moveLeft .7s .5s forwards ease;
}



p {
    font-size: 24px;
}

#first-p {
    position: relative;
    right: 100%;
    animation: appear .3s .3s forwards ease, colorize 1.2s .7s forwards ease, moveRight .5s .8s forwards ease;
}

#second-p {
    position: relative;
    bottom: 500px;
    animation: appear .3s .3s forwards ease, colorize 1.2s .7s forwards ease, moveleft .5s .9s forwards ease;
}

#details {
    cursor: default;
    overflow-x: hidden;

}


.logo {
    cursor: pointer;
}

/* // RIGHT NOW ADD THE CLASS THE ITEM VALUE IN THE ARRAY */

#where {

    animation: appear .3s .3s forwards, moveLeft .5s .3s forwards ease, colorize .5s .3s forwards ease;
}

#date {
    animation: appear .3s 1.3s forwards, moveRight .5s 1.3s forwards ease, colorize .5s 1.3s forwards ease;
}

#when {

    animation: appear .3s 2.3s forwards, moveLeft .5s 2.3s forwards ease, colorize .5s 2.3s forwards ease;
}

#who {

    animation: appear .3s 3.3s forwards, moveRight .5s 3.3s forwards ease, colorize .5s 3.3s forwards ease;
}

#price {
    animation: appear .3s 4.3s forwards, moveLeft .5s 4.3s forwards ease, colorize .5s 4.3s forwards ease;
}

#activity {
    animation: appear .3s 5.3s forwards, moveRight .5s 5.3s forwards ease, colorize .5s 5.3s forwards ease;
}

#bonus {
    animation: appear .3s 6.3s forwards, moveLeft .5s 6.3s forwards ease, colorize .5s 6.3s forwards ease;
}



#where,
#date,
#when,
#who,
#price,
#activity,
#bonus {
    overflow-x: hidden;
    position: relative;
    opacity: 0;
    transition: .3s ease;
}

#leprechaun_playing {
    animation: appear .5s 7.3s forwards;
}
</style>