<script setup>

import { ref, computed } from 'vue'

</script>
<template>
  <div class="menu">
    <!-- menu de navegação -->
    <nav>
      <ul class="antes-barra">
        <li><a href="#ifbooks" class="logo">IFbooks</a></li>
        <li class="barrinha"></li>
        <li class="slogan">
          Aprecie a <br />
          Leitura
        </li>
      </ul>
      <div class="barra-pesquisa">
        <input type="text" v-model="termoBusca" placeholder="Pesquisar" />
        <i class="fa-solid fa-magnifying-glass"></i>
      </div>
      <ul class="apos-barra">
        <li><a href="#termo">Termo</a></li>
        <li><a href="#equipe">Equipe</a></li>
        <li><a href="#envio">Envio</a></li>
        <li><a href="#devolucoes">Devoluções</a></li>
        <li class="icon-com-barra"><a href="#carrinho"><i class="fa-solid fa-cart-shopping"></i></a></li>
        <li class="icon-com-barra"><a href="#favoritos"><i class="fa-solid fa-heart"></i></a></li>
        <li><a href="#perfil"><i class="fa-solid fa-user"></i></a></li>
      </ul>

    </nav>
    <div class="linha-roxa"></div>
  </div>

</template>
<style scoped>

/* css menu */

.icon-com-barra {
  position: relative;
  display: flex;
  align-items: center;
  height: 100%;
  padding-right: 5px;
  margin-right: -10px;
}

.icon-com-barra::after {
  content: "";
  position: absolute;
  top: 10px;
  right: 0;
  width: 1px;
  height: 22px;
  background-color: #4E1EB5;
}

/* Mudar a cor dos ícones para roxo */
.icon-com-barra a i,
.apos-barra li a i {
  color: #4E1EB5;
}

.apos-barra li {
  display: flex;
  align-items: center;
  justify-content: center;
}

.apos-barra li a {
  display: flex;
  align-items: center;
  text-decoration: none;
  font-size: 15px;
  padding: 0 10px;
  color: #7B7881;
}

.apos-barra li a:hover {
  color: #4E1EB5; 
}

.barra-pesquisa {
  display: flex;
  align-items: center;
  background-color: #f0f0f0;
  padding: 3px 15px;
  margin: 0.7vw 5vw 0 5vw;
}

.barra-pesquisa input {
  border: none;
  outline: none;
  background: transparent;
  color: #4E1EB5;
  font-size: 14px;
  padding: 5px 0 5px 0;
  flex-grow: 1;
}

.barra-pesquisa i {
  color: #4E1EB5;
  font-size: 18px;
  margin-left: 70px;
  cursor: pointer;
}

nav {
  display: flex;
  justify-content: center;
  align-items: flex-start;
  flex-wrap: wrap;
  margin: 0.5vw 0 0 0;
}

nav ul {
  list-style: none;
  display: flex;
  gap: 20px;
  align-items: center;
  padding: 0;
  margin: 0;
}

nav ul li {
  padding: 1rem 1rem 0 0;
}

nav ul li a {
  text-decoration: none;
}

.logo {
  font-size: 18px;
  color: #231F2D;
}

.antes-barra {
  align-items: center;
  text-align: center;
}

.antes-barra li:first-child {
  position: relative;
}

.antes-barra li:first-child::after {
  content: "";
  position: absolute;
  top: 10px;
  right: 6px;
  width: 1px;
  height: 35px;
  background-color: #4E1EB5;
}

.slogan {
  color: #4E1EB5;
  font-size: 14px;
  line-height: 1;
  margin-left: -55px;
}

.apos-barra a {
  color: #4E1EB5;
}

.linha-roxa {
  width: 100%;
  height: 1px; 
  background-color: #4E1EB5; 
  margin-top: 15px; 
}
</style>
