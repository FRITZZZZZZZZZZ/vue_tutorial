<template>
    <nav :style="{backgroundColor: theme}">
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
        @click.prevent="toggleBackground()">toggle nav bar</button>
    </form>
</template>

<script>
    import NavBarLink from './NavBarLink.vue';
    export default {
        components: {
            NavBarLink
        },
        created() {
            this.getThemeSetting();
        },
        props: ['pages', 'activePage', 'navLinkClick'],
        data () {
            return {
                theme: 'blue'
            };
        },
        methods: {
            toggleBackground () {
                if (this.theme == "blue") {
                        this.theme = "red";
                } else {
                    this.theme = "blue";
                }

                this.storeThemeSetting();
            },
            storeThemeSetting () {
                localStorage.setItem('theme' ,this.theme);
            },
            getThemeSetting () {
                let theme = localStorage.getItem('theme', this.theme);

                if (theme) {
                    this.theme = theme;
                }
            }
        }
    };
</script>