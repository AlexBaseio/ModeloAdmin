<template>
    <div class="h-100">
        <img id="fundo-logo" src="./../assets/download-fake.png" class="center-block">
        <div class="container-fluid h-100">
            <div class="row justify-content-center align-items-center h-100">
                <div class="col-12 col-sm-8 col-md-6 col-lg-5 col-xl-4">
                    <font face="arial">
                        <h2><center><b> Tlabla Analysis System </b></center></h2>
                    </font>
                    <div class="card">
                        <div class="card-header"><span>Controle de Acesso</span></div>
                        <div class="card-body">
                            <form>
                                <div class="form-group">
                                    <label for="exampleInputEmail1">Usuário</label>
                                    <input class="form-control" id="exampleInputEmail1" type="text" placeholder="Digite o seu código">
                                </div>
                                <div class="form-group">
                                    <label for="exampleInputPassword1">Senha</label>
                                    <input class="form-control" id="exampleInputPassword1" type="password" placeholder="Senha">
                                </div>
                                <div class="form-group">
                                    <div class="form-check">
                                        <label class="form-check-label"><input class="form-check-input" type="checkbox"> Lembrar a senha</label>
                                    </div>
                                </div>
                                <div class="row justify-content-center">
                                    <a class="btn login tas-primary" @click="chamarInicio">Login</a>
                                </div>
                            </form>
                            <div class="row justify-content-center">
                                <a class="small" href="#">Esqueceu a senha?</a>
                            </div>
                        </div>
                    </div>
                </div>
            </div>
        </div>
    </div>
</div>
</template>

<script>
export default {
    components: {
    },
    props: [],
    methods: {
        chamarInicio() {
            this.$emit('chamar',2);
        },
    }
}
</script>

<style>
@import "./../custom.css";

#fundo-logo {
    width: 80%;
    height: auto;
    position: fixed;

    opacity: 0.3;

    -webkit-transform: rotate(-15deg);
    -moz-transform: rotate(-15deg);
    -o-transform: rotate(-15deg);
    -ms-transform: rotate(-15deg);
    transform: rotate(-15deg);

    -webkit-filter: blur(5px); /* Safari 6.0 - 9.0 */
    filter: blur(5px);
}

</style>
