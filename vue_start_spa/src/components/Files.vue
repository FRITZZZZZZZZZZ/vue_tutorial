<template>
    <h1>Files</h1>
    <div
        class="file-selector">
        <div
            v-for="(file, index) in files"
            :key="index"
            class="file"
            title="file.path">
            <h2 class="file-name">{{ file.name }}</h2>
            <h2 class="file-type">{{ file.type }}</h2>
        </div>
    </div>
</template>

<script>
export default {
    props: ['files']
};
</script>

<style>
*{
    box-sizing: border-box;
}
h1 {
    font-weight: bold;
    font-size: 35px;
}
.file-selector {
    overflow-y: auto; 
}
.file {
  border: 5px solid rgb(26, 26, 80);
  border-radius: 10px;     
  width: auto;
  padding: 3px;
  margin: 3px;
  display: flex;
  flex-direction: column;
}
.file-name {
    font-size: 25px;
    text-align: center;
    font-weight: bold;
}
.file-type {    
    font-size: 10px;
    border-radius: 5px;
    text-align: left;
}
</style>