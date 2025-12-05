<template>
    <!--<navbar
    :pages="pages"
    :active-page="activePage"
    :nav-link-click="(index) => activePage = index"
    ></navbar>
    
    <page-viewer 
    v-show="pages.length > 0"
    :page="pages[activePage]">
    </page-viewer> 

    <create-page>
        :page-created="pageCreated" 
    </create-page> -->
    <body>
        <header>
            <span>
                <div>
                    <h1>EDG 2</h1>
                    <h5>ENSIMA Data Generator</h5>
                </div>
    
            </span>
        </header>
        <main>
        <div
            class="element-selector">
            <div
                class="subprograms">
                <subprogram
                    :subprograms="subprograms">
                </subprogram>
            </div>
            <div
                class="files">        
                <files
                    :files="files">
                </files>
            </div>
        </div>
        </main>
    </body>
</template>

<script>
import NavBarLink from './components/NavBarLink.vue'

import Subprogram from './components/Subprogram.vue';
import Files from './components/Files.vue';

import Navbar from './components/Navbar.vue';
import PageViewer from './components/PageViewer.vue';
import CreatePage from './components/CreatePage.vue';
export default {
    components: {
        Navbar,
        PageViewer,
        CreatePage,
        Subprogram,
        Files
    },
    created() {
        this.getPages();
        this.getSubprograms();
        this.getFiles();
    },
    data() {
        return {
            activePage: 0,
            pages: [],
            subprograms: [],
            files: []
        };
    },
    methods: {
        async getPages() {
            let res = await fetch('pages.json');
            let data = await res.json();
            this.pages = data;
        },
        async getSubprograms() {
                let res = await fetch('subprogram_description.json');
                let subprogramData = await res.json();
                console.log(subprogramData)
                this.subprograms = subprogramData;
            },
        async getFiles() {
            let res = await fetch('files.json');
            let fileData = await res.json();
            this.files = fileData;
        }
    },
    pageCreated(pageObj) {
        console.log(pageObj);
    }
}
</script>
<style>
.body{
    height: 100%;
    width: 100%;
    margin: 0px;
    padding: 0px;
    box-sizing: border-box;
}
.header{
    height: 10vh;
}
.element-selector {
    flex: 1;           
    display: flex;
    flex-direction: column;
    justify-content: space-around;
}
.subprograms {
    width: min-content;
    height: 400px;
    min-width: 250px;
    min-height: 250px;
}
.files {
    width: min-content;
    height: 400px;
    min-width: 250px;
    min-height: 250px;   
    overflow-y: auto; 
}
</style>