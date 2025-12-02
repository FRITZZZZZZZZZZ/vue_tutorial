<template>
    <div id="color-coding">
        <ol>
            <li>
                <h2>Input parameter</h2>
                <h3>Type</h3>
            </li>
        </ol>
            <h1>Subprogram name</h1>
        <ol>
            <li>
                <h2>Output parameter</h2>
                <h3>Output parameter type</h3>
            </li>
        </ol>
    </div>
</template>

<script>
    export default {    
        data() {
            return {
                subprograms: [],
                files: []
            };
        },
        methods: {
            async getSubprograms() {
                let res = await fetch('subprogram_description.json');
                let subprogramData = await res.json();
                this.subprograms = subprogramData;
            },
            async getFiles() {
                let res = await fetch('files_description.json');
                let fileData = await res.json();
                this.files = fileData;
            }
        },

    }
</script>   