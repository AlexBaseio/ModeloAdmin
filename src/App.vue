<template>
    <div id="app">
        <login v-if="tela === 1" @chamar="chamarTela"></login>
        <div v-if="tela !== 1" class="fixed-nav sticky-footer" id="page-top">
            <!-- Navigation-->
            <nav class="navbar navbar-expand-lg fixed-top" id="mainNav">
                <a class="navbar-brand" href="#" @click="chamarTela(2)">Blabla Analisys System</a>
                <button class="navbar-toggler navbar-toggler-right" type="button" data-toggle="collapse" data-target="#navbarResponsive">
                    <span class="navbar-toggler-icon"></span>
                </button>
                <div class="collapse navbar-collapse" id="navbarResponsive">
                    <ul class="navbar-nav navbar-sidenav" id="exampleAccordion">
                        <li class="nav-item" data-toggle="tooltip" data-placement="right" title="Dashboard">
                            <a class="nav-link" href="#" @click="tela = 3" data-toggle="collapse" data-target=".navbar-collapse.show">
                                <i class="fa fa-fw fa-dashboard"></i>
                                <span class="nav-link-text">Cadastros</span>
                            </a>
                        </li>
                        <li class="nav-item" data-toggle="tooltip" data-placement="right" title="Charts">
                            <a class="nav-link" href="#" data-toggle="collapse" data-target=".navbar-collapse.show">
                                <i class="fa fa-fw fa-area-chart"></i>
                                <span class="nav-link-text">Comercial</span>
                            </a>
                        </li>
                        <li class="nav-item" data-toggle="tooltip" data-placement="right" title="Tables">
                            <a class="nav-link" href="#" data-toggle="collapse" data-target=".navbar-collapse.show">
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
                                    <a href="#" data-toggle="collapse" data-target=".navbar-collapse.show">Comercial</a>
                                </li>
                                <li>
                                    <a href="#" data-toggle="collapse" data-target=".navbar-collapse.show">Estoques</a>
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
                            <a class="nav-link text-center" id="sidenavToggler" @click="fecharPainel()">
                                <i class="fa fa-fw fa-angle-left"></i>
                            </a>
                        </li>
                    </ul>

                    <ul class="navbar-nav mr-auto">
                        <li class="nav-item">
                            <!-- Breadcrumbs-->
                            <ol class="breadcrumb d-none d-xl-block">
                                <li v-if="tela === 2" class="breadcrumb-item active">Inicio</li>

                                <li v-if="tela === 3" class="breadcrumb-item"><a href="#" @click="chamarTela(2)">Inicio</a></li>
                                <li v-if="tela === 3" class="breadcrumb-item active">Cadastro</li>

                                <li v-if="tela === 4" class="breadcrumb-item"><a href="#" @click="chamarTela(2)">Inicio</a></li>
                                <li v-if="tela === 4" class="breadcrumb-item"><a href="#" @click="chamarTela(3)">Cadastro</a></li>
                                <li v-if="tela === 4" class="breadcrumb-item active">Alterando</li>
                            </ol>
                        </li>
                    </ul>

                    <ul class="navbar-nav ml-auto">
                        <li class="nav-item dropdown">
                            <a class="nav-link dropdown-toggle mr-lg-2" id="usuarioDropdown" href="#" data-toggle="dropdown">
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
                    <inicio v-if="tela === 2"></inicio>
                    <consulta v-if="tela === 3" @chamar="chamarTelaReg" :titulo="dados.titulo" :mensagem="dados.mensagem" :avancado="dados.avancado" :cabecalho="dados.cabecalho" :registros="dados.registros" :informacoes="dados.informacoes"></consulta>
                    <cadastro v-if="tela === 4" @chamar="chamarTela" :titulo="dados.titulo" :cabecalho="dados.cabecalho" :registro="dados.registros[reg_index]"></cadastro>
                </div>
                <!-- /.content-wrapper-->

                <!-- Scroll to Top Button-->
                <a class="scroll-to-top rounded" href="#page-top">
                    <i class="fa fa-angle-up"></i>
                </a>

                <footer class="sticky-footer">
                  <div class="container">
                    <div class="text-center">
                      <small>Hit to target</small>
                    </div>
                  </div>
                </footer>

                <!-- Logout Modal-->
                <div class="modal fade" id="exampleModal" tabindex="-1" role="dialog">
                    <div class="modal-dialog" role="document">
                        <div class="modal-content">
                            <div class="modal-header">
                                <h5 class="modal-title" id="exampleModalLabel">Você realmente deseja sair?</h5>
                                <button class="close" type="button" data-dismiss="modal"><span>×</span></button>
                            </div>
                            <div class="modal-body">
                                Selecione "Logout" para encerrar esta sessão.
                            </div>
                            <div class="modal-footer">
                                <button class="btn btn-secondary" type="button" data-dismiss="modal">Cancelar</button>
                                <a class="btn btn-primary" data-dismiss="modal" @click="tela = 1">Logout</a>
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
import Login from './components/Login'
import Cadastro from './components/Cadastro'

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
  informacoes: "Total de Registro: 10",
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
    Consulta,
    Login,
    Cadastro
  },
  data () {
      return {
          tela: 1,
          reg_index: 0,
          dados: dados
      }
  },
  methods: {
    chamarTela(x) {
      this.tela = x;
    },
    chamarTelaReg(x, index) {
      this.tela = x;
      this.reg_index = index;
    },
    fecharPainel() {
      $("body").toggleClass("sidenav-toggled");
      $(".navbar-sidenav .nav-link-collapse").addClass("collapsed");
      $(".navbar-sidenav .sidenav-second-level, .navbar-sidenav .sidenav-third-level").removeClass("show");
    }
  }
}
</script>

<style>
@import "./../custom.css";

.breadcrumb {
    padding: 0;
    margin: 0;
    background-color: var(--cor-base-verde);
}

.breadcrumb-item {
  display: inline;
}

div.sticky-footer {
  margin-bottom: 56px;
}

div.sticky-footer .content-wrapper {
  min-height: calc(100vh - 56px - 56px);
}

div.fixed-nav {
  padding-top: 56px;
}
</style>
