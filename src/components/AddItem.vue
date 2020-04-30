<template>
    <div class="input-group">
        <input placeholder="añadir a la lista" type="text" class="form-control" id="new-item" v-model="newItem" @keyup.enter="propagaNuevoItem">
        <span class="input-group-append">
      <button class="btn btn-outline-secondary" type="button" id="add-btn" v-on:click="propagaNuevoItem">Añade</button>
    </span>
    </div>
</template>

<script>
    export default { // ojo camel case
//    template: '#add-item-tmpl',
        data: () => ({
            newItem: ''
        }),
        methods: {
            propagaNuevoItem: function() {
                var nombre = this.newItem.trim();
                if (nombre) {
                    this.$emit("nuevoitem", nombre); // Ojo NO camel case
                    this.newItem = '';
                }
            }
        }
    }
</script>