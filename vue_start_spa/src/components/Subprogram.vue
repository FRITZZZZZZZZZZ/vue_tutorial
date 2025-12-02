<template>
    <div class="color-coding" v-for="(subprogram) in subprograms">
        <ol class="horizontal-list">
            <li v-for="(parameterLabel, index) in subprogram.input.parameterLabel" :key="index">
                <div title="Input API definition of this subprogram.">
                    <h2>{{ subprogram.input.parameterLabel[index] }}</h2>
                    <h3>{{ subprogram.input.parameterType[index] }}</h3>
                </div>
            </li>
        </ol>
        <h1>{{ subprogram.name }}</h1>
        <ol>
            <li v-for="(parameterLabel, index) in subprogram.output.parameterLabel" :key="index">
                <div title="Output API definition of this subprogram">
                    <h2>{{ subprogram.output.parameterLabel[index] }}</h2>
                    <h3>{{ subprogram.output.parameterType[index] }}</h3>
                </div>
            </li>
        </ol>
    </div>
</template>

<script>
    export default {    
        props: ['subprograms']
    }
</script>   

<style scoped>
.color-coding {
  border: 4px solid blue;
  border-radius: 10px;
  padding: 10px;   /* innen Platz für Content */
  margin: 10px 0;  /* Abstand zu anderen Elementen */
  width: 30%;
}
h2 {
    margin: 5px;
    font-size: 30px;
    border: 5px solid grey;
    border-radius: 5px;
}
h3 {    
    margin: 5px;
    font-size: 20px;
    border: 5px solid grey;
    border-radius: 5px;
}

</style>