<template>
    <div class="row">
        <div class="col-xl-3 col-sm-6 mb-3">
            <div class="card text-white bg-primary o-hidden h-100">
                <div class="card-body">
                    <div class="card-body-icon"><i class="fa fa-fw fa-edit"></i></div>
                    <div class="mr-5"><h3>Pedido Comercial</h3></div>
                </div>
                <div class="card-footer text-white clearfix small z-1">
                    <span class="float-left">Total de pedidos: 25</span>
                </div>
            </div>
        </div>
        <div class="col-xl-3 col-sm-6 mb-3">
            <div class="card text-white bg-warning o-hidden h-100">
                <div class="card-body">
                    <div class="card-body-icon"><i class="fa fa-fw fa-list"></i></div>
                    <div class="mr-5"><h3>Pronta Entrega</h3></div>
                </div>
                <div class="card-footer text-white clearfix small z-1">
                    <span class="float-left">Estoque: 154,23 kg</span>
                </div>
            </div>
        </div>
        <div class="col-xl-3 col-sm-6 mb-3">
            <div class="card text-white bg-success o-hidden h-100">
                <div class="card-body">
                    <div class="card-body-icon"><i class="fa fa-fw fa-shopping-cart"></i></div>
                    <div class="mr-5"><h3>Expedição</h3></div>
                </div>
            </div>
        </div>
        <div class="col-xl-3 col-sm-6 mb-3">
            <div class="card text-white bg-danger o-hidden h-100">
                <div class="card-body">
                    <div class="card-body-icon"><i class="fa fa-fw fa-archive"></i></div>
                    <div class="mr-5"><h3>Romaneios</h3></div>
                </div>
            </div>
        </div>
    </div>
</template>

<script>
export default {
    name: 'inicio',
    data () {
        return {
            msg: 'Turion Analisys System'
        }
    }
}
</script>

<style>
</style>
