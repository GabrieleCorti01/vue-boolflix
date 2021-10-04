<template>
    <header>
        <!-- Sezione searchbar -->
        <section class="row justify-content-center">
            <input v-model.trim="needle" type="text" class="col-2" placeholder="Inserisci il nome di un film">
            <button class="col-1 btn-primary" @click="$emit('searching',needle)" >Cerca</button>
        </section>
    </header>
</template>

<script>
export default {
    name: 'Header',
    data : function(){
        return{
            needle: '',
        }
    }

}
</script>

<style>

</style>