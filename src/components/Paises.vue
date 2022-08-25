<template>
    

    <div class="container">
        <h1 style="color:#4F4F4F;font-size:16px" class="unico-h1">Lista de paises</h1>
        <div class="row text-center">
            <div class="col titulos">
                Name      
            </div>
            <div class="col titulos">Capital</div>
            <div class="col titulos">Area</div>
            <div class="col titulos">currencies</div>
        </div>
        <div class="row" v-if="paises.length > 0" v-for="(pais,index) in paises">
            <div class="col coluna">
                
                <p class="titulo">{{pais.name.common}}</p>
            </div>
            <div class="col coluna">
                <p class="titulo" v-for="central in pais.capital">{{central}}</p>
            </div>
            <div class="col coluna">
                <p class="titulo">{{pais.area}}</p>
            </div>
            <div class="col coluna">
                <p class="titulo" v-for="moeda in pais.currencies">{{moeda.name}}</p>
            </div>
        </div>
    </div>
</template>

<script>
export default{
    name:'Paises',
    data() {
        return {
            title:'Lista de paises',
            paises:[],
            pais:[],
        }
    },
    methods:{
        fetchPaises(){
            let url = 'https://restcountries.com/v3.1/all'
            axios.get(url).then(res =>{
                this.paises = res.data
                console.log(this.paises)
            })
        }
    },
    mounted(){
        this.fetchPaises()
    }, 

}

</script>

<style scoped>
.titulo{
    
    text-align: center;
    font-size: 12px;
    margin: 0;
    

}
.coluna{
    border: 1px solid black;
    display: flex;
    align-items: center;
    justify-content: center;

    
}
.titulos{
    text-align: center;
    border: 1px solid black;
    font-size: 12px;
    color: #808080;
    font-weight: bold;
    text-transform: uppercase;
}
.unico-h1{
    border: 1px solid black;
    margin: 0 !important;
    padding: 0 !important;
    width: 100%;
}
*{
    box-sizing: border-box;
}
.row{
   --bs-gutter-x: 0;
}

</style>