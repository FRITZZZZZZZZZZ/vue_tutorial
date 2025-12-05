<template >
    <h1>Programs</h1>
    <div 
        class="subprogram-selector">
        <div 
            class="subprogram" 
            v-for="(subprogram) in subprograms"
            >
            <span 
                :key="index" 
                title="Input API definition of this subprogram."
                class="signatur">
                <div 
                    class="signatur-element" 
                    :title="subprogram.input.parameterExplanation[index]"
                    v-for="(parameterLabel, index) in subprogram.input.parameterLabel" 
                    >
                    <h2 class="parameter-label">{{ subprogram.input.parameterLabel[index] }}</h2>
                    <h3 class="parameter-type">{{ subprogram.input.parameterType[index] }}</h3>
                </div>
            </span>
            <h1 class="subprogram-name">{{ subprogram.name }}</h1>
            <span v-for="(parameterLabel, index) in subprogram.output.parameterLabel" 
                :key="index" 
                title="Output API definition of this subprogram"
                class="signatur">
                <div class="signatur-element" :title="subprogram.output.parameterExplanation[index]">
                        <h2 class="parameter-label">{{ subprogram.output.parameterLabel[index] }}</h2>
                        <h3 class="parameter-type">{{ subprogram.output.parameterType[index] }}</h3>
                </div>
            </span>
        </div>
    </div>
</template>

<script>
    export default {    
        props: ['subprograms']
    }
</script>   

<style scoped>
*{
    box-sizing: border-box;
}
h1 {
    font-weight: bold;
    font-size: 35px;
}
.subprogram-selector {
    overflow-y: auto; 
}
.subprogram {
  border: 5px solid rgb(26, 26, 80);
  border-radius: 10px;     
  width: auto;
  padding: 3px;
  margin: 3px;
  display: flex;
  flex-direction: column;
}
.signatur {
    display: flex;
    flex-direction: column;
}
.signatur-element {
    border: 2px solid gray;
    border-radius: 5px;
    padding: 3px;
    margin: 1px;
    width: auto;
    display: inline-block;
}
.subprogram-name {
    font-size: 25px;
    text-align: center;
    font-weight: bold;
}
.parameter-label {
    font-size: 15px;
    font-weight: bold;
    border-radius: 5px;
    text-align: left;
    margin: 0px;
    padding: 3px;
    margin: 1px;
}
.parameter-type {    
    font-size: 10px;
    border-radius: 5px;
    text-align: left;
}

</style>