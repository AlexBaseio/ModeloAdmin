<template>
    <div id="app">
        <div class="fixed-nav sticky-footer bg-dark" id="page-top">
            <!-- Navigation-->
            <nav class="navbar navbar-expand-lg navbar-dark bg-dark" id="mainNav">
                <a class="navbar-brand" href="#" @click="chamarInicio">Turion Analisys System</a>
                <button class="navbar-toggler navbar-toggler-right" type="button" data-toggle="collapse" data-target="#navbarResponsive">
                    <span class="navbar-toggler-icon"></span>
                </button>
                <div class="collapse navbar-collapse" id="navbarResponsive">
                    <ul class="navbar-nav navbar-sidenav" id="exampleAccordion">
                        <li class="nav-item" data-toggle="tooltip" data-placement="right" title="Dashboard">
                            <a class="nav-link" href="#" @click="chamarConsulta">
                                <i class="fa fa-fw fa-dashboard"></i>
                                <span class="nav-link-text">Cadastros</span>
                            </a>
                        </li>
                        <li class="nav-item" data-toggle="tooltip" data-placement="right" title="Charts">
                            <a class="nav-link" href="#">
                                <i class="fa fa-fw fa-area-chart"></i>
                                <span class="nav-link-text">Comercial</span>
                            </a>
                        </li>
                        <li class="nav-item" data-toggle="tooltip" data-placement="right" title="Tables">
                            <a class="nav-link" href="#">
                                <i class="fa fa-fw fa-table"></i>
                                <span class="nav-link-text">Expedição</span>
                            </a>
                        </li>
                        <li class="nav-item" data-toggle="tooltip" data-placement="right" title="Components">
                            <a class="nav-link nav-link-collapse collapsed" data-toggle="collapse" href="#collapseComponents" data-parent="#exampleAccordion">
                                <i class="fa fa-fw fa-wrench"></i>
                                <span class="nav-link-text">Relatórios</span>
                            </a>
                            <ul class="sidenav-second-level collapse" id="collapseComponents">
                                <li>
                                    <a href="#">Comercial</a>
                                </li>
                                <li>
                                    <a href="#">Estoques</a>
                                </li>
                            </ul>
                        </li>
                        <li>
                            <div class="dropdown-divider"></div>
                        </li>
                        <li class="nav-item" data-toggle="tooltip" data-placement="right" title="Example Pages">
                            <a class="nav-link nav-link-collapse collapsed" data-toggle="collapse" href="#collapseExamplePages" data-parent="#exampleAccordion">
                                <i class="fa fa-fw fa-file"></i>
                                <span class="nav-link-text">Administração</span>
                            </a>
                            <ul class="sidenav-second-level collapse" id="collapseExamplePages">
                                <li>
                                    <a href="">Manutenção de usuários</a>
                                </li>
                                <li>
                                    <a href="">Permissões</a>
                                </li>
                                <li>
                                    <a href="">Relatório de Acessos</a>
                                </li>
                            </ul>
                        </li>
                    </ul>

                    <ul class="navbar-nav sidenav-toggler">
                        <li class="nav-item">
                            <a class="nav-link text-center" id="sidenavToggler">
                                <i class="fa fa-fw fa-angle-left"></i>
                            </a>
                        </li>
                    </ul>
                    <ul class="navbar-nav ml-auto">
                        <li class="nav-item dropdown">
                            <a class="nav-link dropdown-toggle mr-lg-2" id="alertsDropdown" href="#" data-toggle="dropdown" aria-haspopup="true" aria-expanded="false">
                                <i class="fa fa-fw fa-user"></i>
                                <span class="d-lg-none">Alexandre Baseio</span>
                            </a>
                            <div class="dropdown-menu dropdown-menu-right">
                                <h6 class="dropdown-header">Alexandre Baseio</h6>
                                <div class="dropdown-divider"></div>
                                <a class="dropdown-item" href="#">
                                    <span>Personalização</span>
                                </a>
                                <a class="dropdown-item" href="#">
                                    <span>Trocar senha</span>
                                </a>
                                <div class="dropdown-divider"></div>
                                <a class="dropdown-item" href="#" data-toggle="modal" data-target="#exampleModal">
                                    <i class="fa fa-fw fa-sign-out"></i>Logout</a>
                                </a>
                            </div>
                        </li>
                    </ul>
                </div>
            </nav>

            <div class="content-wrapper">
                <div class="container-fluid">
                    <!-- Breadcrumbs-->
                    <ol class="breadcrumb">
                        <li v-if="tela === 1" class="breadcrumb-item active">Inicio</li>
                        <li v-if="tela === 2" class="breadcrumb-item"><a href="#" @click="chamarInicio">Inicio</a></li>
                        <li v-if="tela === 2" class="breadcrumb-item active">Cadastro</li>
                    </ol>
                    <inicio v-if="tela === 1"></inicio>
                    <consulta v-if="tela === 2" :titulo="dados.titulo" :mensagem="dados.mensagem" :avancado="dados.avancado" :cabecalho="dados.cabecalho" :registros="dados.registros"></consulta>

                </div>
                <!-- /.content-wrapper-->
                <footer class="sticky-footer">
                    <div class="container">
                        <div class="text-center">
                            <small>HIT TO TARGET</small>
                        </div>
                    </div>
                </footer>
                <!-- Scroll to Top Button-->
                <a class="scroll-to-top rounded" href="#page-top">
                    <i class="fa fa-angle-up"></i>
                </a>

                <!-- Logout Modal-->
                <div class="modal fade" id="exampleModal" tabindex="-1" role="dialog" aria-labelledby="exampleModalLabel" aria-hidden="true">
                    <div class="modal-dialog" role="document">
                        <div class="modal-content">
                            <div class="modal-header">
                                <h5 class="modal-title" id="exampleModalLabel">Ready to Leave?</h5>
                                <button class="close" type="button" data-dismiss="modal" aria-label="Close">
                                    <span aria-hidden="true">×</span>
                                </button>
                            </div>
                            <div class="modal-body">Select "Logout" below if you are ready to end your current session.</div>
                            <div class="modal-footer">
                                <button class="btn btn-secondary" type="button" data-dismiss="modal">Cancel</button>
                                <a class="btn btn-primary" href="login.html">Logout</a>
                            </div>
                        </div>
                    </div>
                </div>
            </div>
        </div>
    </div>
</template>

<script>
import Inicio from './components/Inicio'
import Consulta from './components/Consulta'

var dados = {
  titulo: "Cadastro de Produtos",
  mensagem: "Bem vindo ao teste de cadastro. Utilize com consicencia.",
  cabecalho: [
    {descricao: "Código", visivel: true, key: true, classificacao: "<>"},
    {descricao: "Descrição", visivel: true, key: false, classificacao: ">"},
    {descricao: "Preço", visivel: true, key: false, classificacao: "<"},
    {descricao: "Quantidade", visivel: true, key: false, classificacao: ""},
    {descricao: "Fornecedor", visivel: false, key: false, classificacao: ""},
    {descricao: "Deposito", visivel: false, key: false, classificacao: ""},
    {descricao: "Última Compra", visivel: false, key: false, classificacao: ""}
  ],
  registros: [
    {codigo: "005.003.003", descricao: "Celular Mega Amarelo", preco: "35.91", quantidade: "238", fornecedor: "LG", deposito: "Consignado", ultimacompra: "08/11/2017"},
    {codigo: "002.002.005", descricao: "Mouse Mini Laranja", preco: "35.12", quantidade: "237", fornecedor: "Medicina Sorocaba", deposito: "Consignado", ultimacompra: "23/02/2017"},
    {codigo: "000.001.004", descricao: "Caneta Pequeno Verde", preco: "33.19", quantidade: "214", fornecedor: "LG", deposito: "Interno", ultimacompra: "14/05/2017"},
    {codigo: "006.000.002", descricao: "Suporte Grande Azul", preco: "41.02", quantidade: "175", fornecedor: "Tilibra", deposito: "Externo", ultimacompra: "21/01/2017"},
    {codigo: "005.001.001", descricao: "Celular Pequeno Preto", preco: "27.94", quantidade: "73", fornecedor: "QSS", deposito: "Interno", ultimacompra: "00/06/2017"},
    {codigo: "001.002.004", descricao: "Caneca Mini Verde", preco: "29.47", quantidade: "211", fornecedor: "Samsung", deposito: "Externo", ultimacompra: "11/09/2017"},
    {codigo: "005.001.006", descricao: "Celular Pequeno Vermelho", preco: "23.83", quantidade: "138", fornecedor: "Tilibra", deposito: "Interno", ultimacompra: "21/08/2017"},
    {codigo: "000.002.005", descricao: "Caneta Mini Laranja", preco: "29.65", quantidade: "199", fornecedor: "Medicina Sorocaba", deposito: "Externo", ultimacompra: "00/06/2017"},
    {codigo: "006.003.002", descricao: "Suporte Mega Azul", preco: "29.31", quantidade: "146", fornecedor: "QSS", deposito: "Consignado", ultimacompra: "16/10/2017"},
    {codigo: "009.001.005", descricao: "Cordão Pequeno Laranja", preco: "29.43", quantidade: "130", fornecedor: "Tilibra", deposito: "Externo", ultimacompra: "07/10/2017"},
  ],
  informacoes: "",
  avancado: [
    {descricao: "Fornecedor", id:"fornecedor"},
    {descricao: "Deposito", id:"deposito"}
  ],
  paginas: 5
}

export default {
  name: 'app',
  components: {
    Inicio,
    Consulta
  },
  data () {
      return {
          tela: 1,
          dados: dados
      }
  },
  methods: {
    chamarInicio() {
      this.tela = 1;
    },
    chamarConsulta() {
        this.tela = 2;
    }
  }
}
</script>

<style>
.breadcrumb {
    padding: 2px 15px !important;
}
</style>
