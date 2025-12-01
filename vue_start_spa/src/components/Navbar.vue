<template>
    <nav :style="{backgroundColor}">
        <div class="container-fluid">
            <a href="#" class="navbar-brand">my vue</a>
            <ul class="navbar-nav me-auto mb-2 mb-lg-0">
                <li v-for="(page, index) in pages" class="nav-item" :key="index">
                    <nav-bar-link 
                        :page="page"
                        :isActive="activePage == index"
                        @click.prevent="navLinkClick(index)"
                    ></nav-bar-link>
                </li>
            </ul>
        </div>
    </nav>
                    
    <form>
        <button
        @click.prevent="toggleBackground()">toggle navbar </button>
    </form>
</template>

<script>
    import NavBarLink from './NavBarLink.vue';
    export default {
        components: {
            NavBarLink
        },
        props: ['backgroundColor', 'pages', 'activePage', 'navLinkClick'],
        data () {
            return {
                backgroundColor: 'blue'
            };
        },
        methods: {
            toggleBackground () {
                if (this.backgroundColor == "blue") {
                        this.backgroundColor = "red";
                } else {
                    this.backgroundColor = "blue";
                }
            }
        }
    };
</script>