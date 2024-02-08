<template>
    <nav class="navbar navbar-expand-lg bg-body-transparent">
        <div class="container-fluid">
            <img :src="logo" alt="logo skulldarts" id="logo-skulldarts" @click.prevent="openLogoUrl(logoUrl)">
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
            <!-- <img class="img-fluid" :src="item.imageUrl" :alt="'image d\'un logo'" id="irish_darts"> -->
            <video autoplay loop muted playsinline class="video-fluid">
                <source :src="item.videoUrl" type="video/mp4">
                Votre navigateur ne supporte pas cette video.
            </video>
            <p class="m-5" id="first-p">{{ item.heading + ' ' + item.text }}</p>
            <div id="groups">
                <ul id="list">
                    <li v-for="group in groups" :key="group.url"><img class="img-fluid logo" :src="group.imageUrl"
                            :alt="'image d\'un logo'" @click.prevent="openNewTab(group.url)">
                    </li>
                </ul>
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
            <div id="groups" class="m-5">
                <ul id="list">
                    <li v-for="group in groups" :key="group.url"><img class="img-fluid logo m-2" :src="group.imageUrl"
                            :alt="'image d\'un logo'" @click.prevent="openNewTab(group.url)">
                    </li>
                </ul>
            </div>
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

    props: {
        activePage: Number,
        logoUrl: String,
        logo: String,
        tables: Object,
        pageDetails: Number,
        index: Number,
        videoUrl: String,
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
    }
}
</script>

<style scoped>
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