<template>
    <nav class="navbar navbar-expand-lg bg-body-transparent">
        <div class="container-fluid">
            <img :src="logo" alt="logo skulldarts" id="logo-skulldarts" @click.prevent="openLogoUrl(logoUrl)">
            <button class="navbar-toggler" type="button" data-bs-toggle="collapse" data-bs-target="#navbarSupportedContent"
                aria-controls="navbarSupportedContent" aria-expanded="false" aria-label="Toggle navigation">
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
    <div id="container">
        <h1 id="title" class="m-5">{{ pages[activePage].pageTitle }}</h1>
        <div v-if="activePage === 0" id="home" v-for="(item, pageIndex) in pages[0].pageContent" :key="pageIndex">
            <img class="img-fluid" :src="item.imageUrl" :alt="'image d\'un logo'" id="irish_darts">
            <p class="m-5" id="first-p">{{ item.heading + ' ' + item.text }}</p>
            <div id="groups">
                <ul id="list">
                    <li v-for="group in groups" :key="group.url"><img class="img-fluid logo" :src="group.imageUrl"
                            :alt="'image d\'un logo'" @click.prevent="openNewTab(group.url)">
                    </li>
                </ul>
            </div>
        </div>
        <div v-if="activePage === 1" id="details" v-for="(item, pageDetails) in pages[1].pageContent" :key="pageDetails">
            <img src="../assets/clover.webp" alt="image d'un trèfle" id="clover-left">
            <img src="../assets/clover.webp" alt="image d'un trèfle" id="clover-right">
            <p id="p0">{{ item.where }}</p>
            <p id="p1">{{ item.who }}</p>
            <p id="p2">{{ item.price + ' l\'entrée' }}</p>
            <p id="p3">{{ item.activity }}</p>
            <img class="img-fluid" :src="item.imageUrl" :alt="'image d\'un logo'" id="leprechaun_playing">
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
        }
    },
    props: {
        activePage: Number,
        logoUrl: String,
        logo: String,
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
    left: 5%;
    top: 10%;
    width: 50px;
    height: 50px;
    animation: cloverLeft 10s .5s infinite;
    z-index: 10;
    opacity: 1;
}

#clover-right {
    position: absolute;
    right: 5%;
    top: 10%;
    width: 50px;
    height: 50px;
    animation: cloverRight 10s .5s infinite;
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

#logo-skulldarts {
    max-height: 50px;
    max-width: 50px;
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

}

.logo {
    cursor: pointer;
}

#p0 {
    position: relative;
    left: -8%;
    opacity: 0;
    animation: appear .3s .3s forwards;
}

#p1 {
    position: relative;
    left: 8%;
    opacity: 0;
    animation: appear .3s 1.3s forwards;
}

#p2 {
    position: relative;
    left: -5%;
    opacity: 0;
    animation: appear .3s 2.3s forwards;
}

#p3 {
    position: relative;
    left: 5%;
    opacity: 0;
    animation: appear .3s 3.3s forwards;
}
</style>