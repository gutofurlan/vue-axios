<template>
    <div>
        <form @submit.prevent="onSubmit">
            <input type="text" placeholder="Digite o CEP" v-model="cep">
            <button type="submit">Consultar</button>
        </form>
    </div>
</template>

<script>
import axios from 'axios'

export default {
    data() {
        return {
            cep: '',
            preloader: false
        }
    }, methods: {
        onSubmit() {
            this,preloader = true
            axios.get(`https://viacep.com.br/ws/${this.cep}/json`)
                .then(response => {
                    console.log(response)
                }). catch(error => {
                    
                }). finally(() => 
                    this.preloader = false
                )
        }
    }
}
</script>

<style scoped>

</style>
