<template>
    <nav class="navbar navbar-expand-lg bg-body-transparent">
        <div class="container-fluid">
            <img src="#" alt="logo" srcset="">
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
        <h1 class="m-5">{{ pages[activePage].pageTitle }}</h1>
        <div id="details" v-for="(item, pageDetails) in pages[activePage].pageContent" :key="pageDetails">
            <img class="img-fluid" :src="item.imageUrl" :alt="'image d\'un logo'" id="irish_darts">
            <p class="m-5">{{ item.heading }}</p>
            <p>{{ item.text }}</p>
            <div id="groups" class="m-5">
                <ul id="list">
                    <li v-for="group in groups"><img class="img-fluid" :src="group.imageUrl" alt="" srcset=""></li>
                </ul>
            </div>
        </div>
    </div>
</template>

<script>
export default {
    emits: ['toggle-hamburger'],
    methods: {
        toggleHamburger() {
            this.$emit('toggle-hamburger');
        }
    },
    props: {
        activePage: Number,
        isHamburgerActive: Boolean,
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
.active {
    color: gold !important;
}

#irish_darts {
    box-shadow: 0 0 10px green;
}

#list {
    display: flex;
    flex-direction: row;
    justify-content: space-around;
    align-items: center;
}

#list li img {
    max-width: 200px;
    max-height: 100px;
}
</style>