<template>
    <div id="Consulta">
        <!-- Apresentação das mensagem de alerta e confirmações -->
        <div class="row">
            <div class="col-md-12">
                <div class="alert tas-success" role="alert">
                    <button type="button" class="close" data-dismiss="alert" aria-label="Close">×</button>
                    <p class="mb-0">Mensagem de sucesso: {{ mensagem }}</p>
                </div>
            </div>
            <div class="col-md-12">
                <div class="alert tas-warning" role="alert">
                    <button type="button" class="close" data-dismiss="alert" aria-label="Close">×</button>
                    <p class="mb-0">Mensagem de atenção: {{ mensagem }}</p>
                </div>
            </div>
            <div class="col-md-12">
                <div class="alert tas-danger" role="alert">
                    <button type="button" class="close" data-dismiss="alert" aria-label="Close">×</button>
                    <p class="mb-0">Mensagem de erro: {{ mensagem }}</p>
                </div>
            </div>
        </div>

        <!-- Titulo e opções de pesquisa -->
        <div class="row">
            <div class="col-md-7">
                <h1 class="">{{titulo}}</h1>
            </div>
            <div class="col-md-5">
                <form class="form-inline d-flex justify-content-end my-1">
                    <div class="input-group w-100">
                        <input type="text" class="form-control border border-primary" id="inlineFormInputGroup" placeholder="Texto para localizar">
                        <div class="input-group-append">
                            <button class="btn btn-outline-primary" type="button">
                                <i class="fa fa-fw fa-search"></i>
                            </button>
                        </div>
                        <template v-if="avancado.length > 0">
                            <div class="input-group-append">
                                <button class="btn btn-outline-primary" type="button" data-toggle="collapse" href="#collapseAdvanced">
                                    <i class="fa fa-fw fa-cogs"></i>
                                </button>
                            </div>
                        </template>
                        <div class="input-group-append">
                            <button id="btn-divider" type="button" class="btn btn-link" disabled></button>
                        </div>
                        <div class="input-group-append">
                            <button type="button" class="btn btn-outline-primary btn-sm">Novo Item </button>
                        </div>

                    </div>
                </form>
            </div>
        </div>

        <!-- Painel de pesquisa avançada -->
        <div class="row">
            <div class="col-md-12 collapse" id="collapseAdvanced">
                <div class="card">
                    <div class="card-body">

                        <div class="form-group" v-for="value in avancado">
                            <label>{{ value.descricao }}</label>
                            <input type="text" class="form-control" :id="value.id">
                        </div>
                    </div>

                    <div class="card-footer m-0 p-0">
                        <div class="btn-group btn-group-sm p-1 m-0">
                            <button type="button" class="btn btn-outline-primary">Procurar</button>
                        </div>
                    </div>
                </div>
            </div>
        </div>

        <!-- Grade de dados -->
        <div class="row">
            <div class="col-md-12">
                <div class="table-responsive">
                    <table class="table table-hover table-sm table-bordered" id="dataTable" width="100%" cellspacing="0">
                        <thead>
                            <tr>
                                <th v-for="(cab) in cabecalho" v-if="cab.visivel" :class="setClassificacao(cab.classificacao)">{{ cab.descricao }}</th>
                            </tr>
                        </thead>
                        <tbody>
                            <template v-for="(reg, index) in registros">
                                <tr>
                                    <template v-for="(value, key, cindex) in reg" v-if="cabecalho[cindex].visivel">
                                        <td v-if="cabecalho[cindex].key">
                                            <button type="button" class="btn btn-outline-primary btn-sm" data-toggle="collapse" :data-target="'#info' + index"> {{value}} </button>
                                        </td>
                                        <td v-else>{{value}}</td>
                                    </template>
                                </tr>
                                <tr class="collapse" :id="'info' + index">
                                    <td colspan="4">
                                        <div class="card">
                                            <div class="card-body">
                                                <div class="form-group" v-for="(value, key, cindex) in reg" v-if="!cabecalho[cindex].visivel">
                                                    <b>{{cabecalho[cindex].descricao}}:</b> {{value}}
                                                </div>
                                            </div>
                                            <div class="card-footer m-0 p-0">
                                                <div class="btn-group btn-group-sm p-1 m-0">
                                                    <a href="#" class="btn btn-outline-danger">Excluir</a>
                                                    <a class="btn btn-outline-success" @click="chamarCadastro(index)">Alterar</a>
                                                </div>
                                            </div>
                                        </div>
                                    </td>
                                </tr>
                            </template>
                        </tbody>
                        <tfoot>
                            <tr>
                                <td colspan="99">
                                    <strong class="float-left">{{informacoes}}</strong>
                                    <ul class="pagination pagination-sm justify-content-end">
                                        <li class="page-item disabled"><a class="page-link" href="#"><<</a></li>
                                        <li class="page-item disabled"><a class="page-link" href="#"><</a></li>
                                        <li class="page-item active"><a class="page-link" href="#">1</a></li>
                                        <li class="page-item"><a class="page-link" href="#">2</a></li>
                                        <li class="page-item"><a class="page-link" href="#">3</a></li>
                                        <li class="page-item"><a class="page-link" href="#">></a></li>
                                        <li class="page-item"><a class="page-link" href="#">>></a></li>
                                    </ul>
                                </td>
                            </tr>
                        </tfoot>
                    </table>
                </div>
            </div>
        </div>
    </div>
</template>

<script>

export default {
    components: {
    },
    props: ['titulo', 'mensagem', 'avancado', 'cabecalho', 'registros', 'informacoes'],
    methods: {
        setClassificacao(value) {
            let val = 't-ordenacao '
            if (value === '<>'){
                val = val + 't-natural'
            } else if (value === '<'){
                val = val + 't-desc'
            } else if (value === '>'){
                val = val + 't-asc'
            } else {
                val = ''
            }
            return val
        },
        chamarCadastro(index) {
            this.$emit('chamar',4, index);
        }
    }
}
</script>

<style>
@import "./../custom.css";

#btn-divider {
    padding: 2px
}
.t-ordenacao {
    cursor: pointer;
}
.t-natural::after {
    content: "\f0dc";
    float: right;
    font-family: fontawesome;
    color: rgba(50, 50, 50, 0.5);
}
.t-asc::after {
    content: "\f0de";
    float: right;
    font-family: fontawesome;
}
.t-desc::after {
    content: "\f0dd";
    float: right;
    font-family: fontawesome;
}

.alert {
    border-radius: 10px;
}
.card {
    box-shadow: inherit;
}

</style>
