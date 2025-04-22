<script setup>
import { ref, computed } from 'vue'
/* lançamentos */
const livros = [
  {
    imagem:
      'https://deborahstrougo.com/wp-content/uploads/2021/12/ordem-de-leitura-da-serie-de-sangue-e-cinzas.jpg',
    titulo: 'De Sangue e Cinzas',
    autor: 'Jennifer L. Armentrout',
    preco: 'R$52,90',
  },
  {
    imagem:
      'https://1.bp.blogspot.com/-8mPjh_CAa2g/Xfg6L1rv6XI/AAAAAAAAAHc/Rqt-KWQm8-EE6EA5SeL9DmFq4YbztoZcACLcBGAsYHQ/s1600/88325_gg.jpg',
    titulo: 'Os Sete Maridos de Evelyn Hugo',
    autor: 'Taylor Jenkins Reid',
    preco: 'R$45,90',
  },
  {
    imagem: 'https://101livros.com/wp-content/uploads/2022/11/Reino-das-Bruxas-scaled.jpg',
    titulo: 'Reino das Bruxas',
    autor: 'Kerri Maniscalco',
    preco: 'R$48,50',
  },
  {
    imagem:
      'https://i0.wp.com/www.thenerddaily.com/wp-content/uploads/2019/01/Verity-by-Colleen-Hoover.jpg',
    titulo: 'Verity',
    autor: 'Colleen Hoover',
    preco: 'R$55,90',
  },
  {
    imagem: 'https://m.media-amazon.com/images/I/81w-GCfqtjL._SY425_.jpg',
    titulo: 'Eu e esse meu coração',
    autor: 'C. C. Hunter',
    preco: 'R$45,65',
  },
  {
    imagem: 'https://m.media-amazon.com/images/I/81LTEfXYgcL._SY425_.jpg',
    titulo: 'A hipótese do amor',
    autor: 'Ali Hazelwood',
    preco: 'R$45,03',
  },
  {
    imagem: 'https://m.media-amazon.com/images/I/51kAYMwbQIL._SY445_SX342_.jpg',
    titulo: 'A biblioteca da meia-noite',
    autor: 'Matt Haig',
    preco: 'R$40,82',
  },
  {
    imagem:
      'https://irp-cdn.multiscreensite.com/174487e2/dms3rep/multi/clarice-lispector-agua-viva.jpg',
    titulo: 'Água viva',
    autor: 'Clarice Lispector',
    preco: 'R$33,94',
  },
]
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
        <li class="icon-com-barra">
          <a href="#carrinho"><i class="fa-solid fa-cart-shopping"></i></a>
        </li>
        <li class="icon-com-barra">
          <a href="#favoritos"><i class="fa-solid fa-heart"></i></a>
        </li>
        <li>
          <a href="#perfil"><i class="fa-solid fa-user"></i></a>
        </li>
      </ul>
    </nav>
    <div class="linha-roxa"></div>
  </div>
  <!-- conteudo -->
  <section class="livros-section">
    <div class="botoes-informacoes">
      <div class="item-info">
        <i class="fas fa-truck"></i>
        <span>Frete grátis para SC</span>
      </div>
      <div class="item-info">
        <i class="fas fa-star"></i>
        <span>Livros recomendados</span>
      </div>
      <div class="item-info">
        <i class="fas fa-book"></i>
        <span>Mais vendidos</span>
      </div>
    </div>
    <!-- Lançamentos -->
    <div class="container">
      <h2 class="titulo-secao">Lançamentos</h2>
      <div class="livros-grid">
        <div v-for="(livro, v) in livros" :key="v" class="card-livro">
          <div class="livro-capa">
            <img :src="livro.imagem" alt="Capa do livro" />
          </div>
          <h3 class="livro-titulo">{{ livro.titulo }}</h3>
          <p class="livro-autor">{{ livro.autor }}</p>
          <div class="preco-favorito">
            <p class="livro-preco">{{ livro.preco }}</p>
            <span class="icone-coracao"><i class="far fa-heart"></i></span>
          </div>
          <div class="acoes">
            <button class="btn-comprar"><i class="fas fa-shopping-cart"></i> Comprar</button>
          </div>
        </div>
      </div>
    </div>
    <!-- Rodapé -->
    <footer class="rodape">
      <div class="container-rodape">
        <div class="redes-sociais">
          <p class="logo">IFbooks</p>
          <div class="icones">
            <i class="fab fa-facebook"></i>
            <i class="fab fa-instagram"></i>
            <i class="fab fa-twitter"></i>
          </div>
        </div>
        <div class="contatos">
          <p>Contatos</p>
          <p><i class="fas fa-phone-alt"></i> +55 47 99999-9999</p>
          <p><i class="fas fa-envelope"></i> contato@ebooks.com</p>
          <p><i class="fas fa-map-marker-alt"></i> Rua da Leitura, 123 - SC</p>
          <div class="pagamento">
            <img
              src="https://upload.wikimedia.org/wikipedia/commons/b/b5/PayPal.svg"
              alt="PayPal"
              class="icone-cartao"
            />
            <img
              src="https://upload.wikimedia.org/wikipedia/commons/0/04/Mastercard-logo.png"
              alt="Mastercard"
              class="icone-cartao"
            />
            <img
              src="https://upload.wikimedia.org/wikipedia/commons/4/41/Visa_Logo.png"
              alt="Visa"
              class="icone-cartao"
            />
          </div>
        </div>
      </div>
      <hr class="linha-divisoria" />
      <p class="copyright">© Alguns direitos reservados | IFBooks 2025</p>
    </footer>
  </section>
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
  content: '';
  position: absolute;
  top: 10px;
  right: 0;
  width: 1px;
  height: 22px;
  background-color: #4e1eb5;
}

.icon-com-barra a i,
.apos-barra li a i {
  color: #4e1eb5;
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
  color: #7b7881;
}

.apos-barra li a:hover {
  color: #4e1eb5;
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
  color: #4e1eb5;
  font-size: 14px;
  padding: 5px 0 5px 0;
  flex-grow: 1;
}

.barra-pesquisa i {
  color: #4e1eb5;
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
  color: #231f2d;
}

.antes-barra {
  align-items: center;
  text-align: center;
}

.antes-barra li:first-child {
  position: relative;
}

.antes-barra li:first-child::after {
  content: '';
  position: absolute;
  top: 10px;
  right: 6px;
  width: 1px;
  height: 35px;
  background-color: #4e1eb5;
}

.slogan {
  color: #4e1eb5;
  font-size: 14px;
  line-height: 1;
  margin-left: -55px;
}

.apos-barra a {
  color: #4e1eb5;
}

.linha-roxa {
  width: 100%;
  height: 1px;
  background-color: #4e1eb5;
  margin-top: 15px;
}

/* css conteudo e lançamentos */
.livros-section {
  background-color: #fff;
}

.botoes-informacoes {
  display: flex;
  justify-content: space-around;
  padding: 32px 11vw;
  border-bottom: 1px solid #ccc;
  background: #fff;
  font-weight: 700;
}

.botoes-informacoes span {
  font-weight: 600;
}

.item-info {
  display: flex;
  align-items: center;
  gap: 10px;
  color: #4e1eb5;
  font-weight: 700;
  font-size: 16px;
}

.item-info i {
  font-size: 20px;
  font-weight: 700;
}

/* Lançamentos */
.container {
  max-width: 1200px;
  margin: 0 auto;
  padding: 40px 20px;
}

.titulo-secao {
  font-size: 28px;
  margin: 0 0 2vw 0;
  font-weight: 600;
}

.livros-grid {
  display: grid;
  grid-template-columns: repeat(4, 1fr);
  gap: 24px;
}

.card-livro {
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: space-between;
  height: 100%;
}

.livro-capa img {
  width: auto;
  height: 240px;
  object-fit: contain;
  margin-bottom: 10px;
}

.livro-titulo {
  font-size: 15px;
  font-weight: bold;
  margin-top: 10px;
  text-align: justify;
}

.livro-autor {
  color: #555;
  font-size: 13px;
  text-align: justify;
}

.livro-preco {
  margin: 8px 0;
  font-weight: bold;
  text-align: left;
}

.acoes {
  display: flex;
  justify-content: center;
  align-items: center;
  margin-top: 12px;
}

.preco-favorito {
  display: flex;
  justify-content: space-between;
  align-items: center;
  width: 87%;
}

.btn-comprar {
  background-color: #4e1eb5;
  color: white;
  border: none;
  padding: 7px 80px;
  font-size: 15px;
  cursor: pointer;
  display: flex;
  align-items: center;
  gap: 8px;
}

.icone-coracao {
  font-size: 18px;
  color: #4e1eb5;
}

/* rodapé */
.rodape {
  background-color: #4e1eb5;
  color: white;
  padding: 40px 10vw 20px;
  font-size: 14px;
}

.container-rodape {
  display: flex;
  justify-content: space-between;
  flex-wrap: wrap;
  align-items: flex-start;
}

.redes-sociais .logo {
  font-size: 15px;
  margin-bottom: 10px;
}

.icones {
  display: flex;
  gap: 10px;
}

.icones i {
  width: 20px;
  height: 20px;
  background-color: white;
  color: #4e1eb5;
  display: flex;
  justify-content: center;
  align-items: center;
  font-size: 16px;
  border-radius: 2px;
}

.contatos {
  text-align: left;
  display: flex;
  flex-direction: column;
  align-items: flex-start;
  gap: 5px;
}

.contatos p {
  margin: 4px 0;
  display: flex;
  align-items: center;
  gap: 8px;
}

.contatos i {
  font-size: 14px;
  color: white;
}

.titulo-contato {
  font-weight: bold;
  margin-bottom: 6px;
  font-size: 15px;
}

.pagamento {
  margin-top: 12px;
  display: flex;
  gap: 8px;
}

.icone-cartao {
  width: 38px;
  height: 25px;
}

.linha-divisoria {
  height: 3px;
  width: 100%;
  background-color: rgba(218, 208, 224, 0.301);
  margin: 30px 0 0 0;
}

.copyright {
  text-align: center;
  padding: 10px;
  font-size: 12px;
  color: rgba(218, 208, 224, 0.726);
}
</style>
