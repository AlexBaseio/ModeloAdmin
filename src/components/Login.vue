<template>
    <div id="Login">
        <div class="container-fluid">
            <div class="card card-login mx-auto mt-5">
                <div class="card-header">Login</div>
                <div class="card-body">
                    <form>
                        <div class="form-group">
                            <label for="exampleInputEmail1">Usuário</label>
                            <input class="form-control" id="exampleInputEmail1" type="text" placeholder="Digite o seu código">
                        </div>
                        <div class="form-group">
                            <label for="exampleInputPassword1">Senha</label>
                            <input class="form-control" id="exampleInputPassword1" type="password" placeholder="Password">
                        </div>
                        <div class="form-group">
                            <div class="form-check">
                                <label class="form-check-label"><input class="form-check-input" type="checkbox"> Remember Password</label>
                            </div>
                        </div>
                        <a class="btn btn-primary btn-block" @click="chamarInicio">Login</a>
                    </form>
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
body {
    background-color: #343a40 !important;
}
</style>
