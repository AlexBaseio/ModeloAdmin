<template>
    <div id="Cadastro">
        <div class="card">
            <div class="card-header">
                <strong class="float-left">{{titulo}}</strong>
                <button class="float-right close" type="button"><span>×</span></button>
            </div>
            <form novalidate method="post">
            <div class="card-body">
                    <template v-for="(value, key, index) in registro">
                        <div class="form-group" :class="[cabecalho[index].visivel ? 'form-group-valid':'form-group-invalid']">
                            <label class="form-control-label"> {{cabecalho[index].descricao}} </label>
                            <input class="form-control" type="text" :value="value">
                            <small class="form-text text-muted">Corrigir os dados</small>
                        </div>
                    </template>
            </div>
            <div class="card-footer">
                <a class="btn btn-outline-success" @click="chamarTela">Salvar</a>
                <a class="btn btn-outline-danger" @click="chamarTela">Cancelar</a>

            </div>
        </form>
        </div>
    </div>
</template>

<script>
export default {
    components: {
    },
    props: ['titulo', 'cabecalho', 'registro'],
    methods: {
        chamarTela() {
          this.$emit('chamar',3);
        },
    }
}
</script>

<style>
.form-group-invalid input{
  border-color: #dc3545;
}
.form-group-invalid input:focus{
    border-color: #dc3545;
    box-shadow: 0 0 0 0.2rem rgba(220, 53, 69, 0.25);
}
.form-group-invalid small{
    color: #dc3545 !important;
}
.form-group-valid small{
    display: none;
}
</style>
