<template>
    <div class="row">
        <div class="col-xl-3 col-sm-6 mb-3">
            <div class="card text-white bg-primary o-hidden rounded-circle h-100">
                <div class="card-body">
                    <div class="card-body-icon"><i class="fa fa-fw fa-edit"></i></div>
                    <div class="mr-5"><h3>Pedido Comercial</h3></div>
                </div>
            </div>
        </div>
        <div class="col-xl-3 col-sm-6 mb-3">
            <div class="card text-white bg-warning o-hidden rounded-circle h-100">
                <div class="card-body">
                    <div class="card-body-icon"><i class="fa fa-fw fa-list"></i></div>
                    <div class="mr-5"><h3>Pronta Entrega</h3></div>
                </div>
            </div>
        </div>
        <div class="col-xl-3 col-sm-6 mb-3">
            <div class="card text-white bg-success o-hidden rounded-circle h-100">
                <div class="card-body">
                    <div class="card-body-icon"><i class="fa fa-fw fa-shopping-cart"></i></div>
                    <div class="mr-5"><h3>Expedição</h3></div>
                </div>
            </div>
        </div>
        <div class="col-xl-3 col-sm-6 mb-3">
            <div class="card text-white bg-danger o-hidden rounded-circle h-100">
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
@import "./../custom.css";
</style>
