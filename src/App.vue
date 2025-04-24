<script setup>
import { ref, computed } from 'vue'

const paginaAtual = ref('home')
const termoBusca = ref('')
const carrinho = ref([])

const livros = [
  {
    id: 1,
    imagem: 'https://deborahstrougo.com/wp-content/uploads/2021/12/ordem-de-leitura-da-serie-de-sangue-e-cinzas.jpg',
    titulo: 'De Sangue e Cinzas',
    autor: 'Jennifer L. Armentrout',
    preco: 52.90,
  },
  {
    id: 2,
    imagem: 'https://1.bp.blogspot.com/-8mPjh_CAa2g/Xfg6L1rv6XI/AAAAAAAAAHc/Rqt-KWQm8-EE6EA5SeL9DmFq4YbztoZcACLcBGAsYHQ/s1600/88325_gg.jpg',
    titulo: 'Os Sete Maridos de Evelyn Hugo',
    autor: 'Taylor Jenkins Reid',
    preco: 45.90,
  },
  {
    id: 3,
    imagem: 'https://101livros.com/wp-content/uploads/2022/11/Reino-das-Bruxas-scaled.jpg',
    titulo: 'Reino das Bruxas',
    autor: 'Kerri Maniscalco',
    preco: 48.50,
  },
  {
    id: 4,
    imagem: 'https://i0.wp.com/www.thenerddaily.com/wp-content/uploads/2019/01/Verity-by-Colleen-Hoover.jpg',
    titulo: 'Verity',
    autor: 'Colleen Hoover',
    preco: 55.90,
  },
  {
    id: 5,
    imagem: 'https://m.media-amazon.com/images/I/81w-GCfqtjL._SY425_.jpg',
    titulo: 'Eu E Esse Meu Coração',
    autor: 'C. C. Hunter',
    preco: 45.65,
  },
  {
    id: 6,
    imagem: 'https://m.media-amazon.com/images/I/81LTEfXYgcL._SY425_.jpg',
    titulo: 'A Hipótese do Amor',
    autor: 'Ali Hazelwood',
    preco: 45.03,
  },
  {
    id: 7,
    imagem: 'https://m.media-amazon.com/images/I/51kAYMwbQIL._SY445_SX342_.jpg',
    titulo: 'A Biblioteca da Meia-Noite',
    autor: 'Matt Haig',
    preco: 40.82,
  },
  {
    id: 8,
    imagem: 'https://irp-cdn.multiscreensite.com/174487e2/dms3rep/multi/clarice-lispector-agua-viva.jpg',
    titulo: 'Água Viva',
    autor: 'Clarice Lispector',
    preco: 33.94,
  },
]

function adicionarAoCarrinho(produto) {
  const existente = carrinho.value.find(item => item.id === produto.id)
  if (existente) {
    existente.quantidade += 1
  } else {
    carrinho.value.push({ ...produto, quantidade: 1 })
  }
}

function removerDoCarrinho(id) {
  carrinho.value = carrinho.value.filter(item => item.id !== id)
}

function aumentarQuantidade(item) {
  item.quantidade += 1
}

function diminuirQuantidade(item) {
  if (item.quantidade > 1) {
    item.quantidade -= 1
  } else {
    removerDoCarrinho(item)
  }
}

const totalCarrinho = computed(() =>
  carrinho.value.reduce((total, item) => total + item.preco * item.quantidade, 0).toFixed(2)
)
</script>

<template>
  <header class="menu">
    <nav>
      <ul class="antes-barra">
        <li><a href="index.html" class="logo">IFbooks</a></li>
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
          <a href="#" @click.prevent="paginaAtual = 'carrinho'">
            <i class="fa-solid fa-cart-shopping"></i>
          </a>
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
  </header>

  <main>
    <!-- HOME -->
    <section v-if="paginaAtual === 'home'">
      <section class="autor-abril">
        <div class="holly">
          <div>
            <p><span>Autora de Abril</span></p>
          </div>
          <h1>Holly Black</h1>
          <p>
            Holly Black é uma escritora e editora norte-americana mais conhecida por sua ficção infantil e juvenil. Seu trabalho inclui a série <span id="povo-do-ar">"O Povo do Ar"</span>, best-seller do The New York Times para jovens adultos.
          </p>
          <button @click="adicionarAoCarrinho(livros[0])">Acessar página do livro</button>
        </div>
        <div class="img">
          <img src="https://i.ibb.co/RTy0nbh0/image-removebg-preview.png" alt="principe-cruel">
          <p>*within the stock limit</p>
        </div>
      </section>

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

        <div class="container">
          <h2 class="titulo-secao">Lançamentos</h2>
          <div class="livros-grid">
            <div v-for="livro in livros" :key="livro.id" class="card-livro">
              <div class="livro-capa">
                <img :src="livro.imagem" alt="Capa do livro" />
              </div>
              <h3 class="livro-titulo">{{ livro.titulo }}</h3>
              <p class="livro-autor">{{ livro.autor }}</p>
              <div class="preco-favorito">
                <p class="livro-preco">R$ {{ livro.preco }}</p>
                <span class="icone-coracao"><i class="far fa-heart"></i></span>
              </div>
              <div class="acoes">
                <button class="btn-comprar" @click="adicionarAoCarrinho(livro)">
                  <i class="fas fa-shopping-cart"></i> Comprar
                </button>
              </div>
            </div>
          </div>
        </div>
      </section>
    </section>

    <!-- CARRINHO -->
  <section v-if="paginaAtual === 'carrinho'" class="pagina-carrinho">
    <h1>Carrinho</h1>

    <div v-if="carrinho.length === 0">
      <p>Seu carrinho está vazio.</p>
    </div>

    <div v-else>
      <!-- Cabeçalhos -->
        <div class="titulos">
          <h2>Título</h2>
          <h2>Quantidade</h2>
          <h2>Subtotal</h2>
        </div>
    <!-- Itens do carrinho -->
  <div v-for="item in carrinho" :key="item.id" class="item-carrinho">
    <!-- Coluna Título -->
      <div class="coluna">
        <img :src="item.imagem" alt="Capa do livro" class="imagem-livro-carrinho" />
        <div>
          <h3 class="titulo-livro">{{ item.titulo }}</h3>
          <p class="autor-livro">{{ item.autor }}</p>
          <p><span>R$ {{ item.preco.toFixed(2) }}</span></p>
        </div>
      </div>
    <!-- Coluna Quantidade -->
      <div class="coluna">
        <div class="quantidade-area">
          <button @click="diminuirQuantidade(item)" class="btn-quantidade">-</button>
          <span>{{ item.quantidade }}</span>
          <button @click="aumentarQuantidade(item)" class="btn-quantidade">+</button>
        </div>
        <button @click="removerDoCarrinho(item)" class="btn-remover">X</button>
      </div>
      <!-- Coluna Subtotal -->
      <div class="coluna">
        <p><strong>R$ {{ (item.preco * item.quantidade).toFixed(2) }}</strong></p>
      </div>
    </div>

      <div>
        <p class="total"><strong>Total da Compra</strong></p>
        <p>Produtos: R$ {{ totalCarrinho }}</p>
        <p>Frete: Grátis</p>
        <p>Total: </p>
        <button>Ir para o pagamento</button>
      </div>
  </div>

  <button @click="paginaAtual = 'home'" class="btn-voltar">Voltar para loja</button>
</section>
  </main>
    <!-- Rodapé -->
    <footer class="rodape">
      <div class="container-rodape">
        <div class="redes-sociais">
          <a href="index.html" class="logo">IFBooks</a>
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
              src="https://i.ibb.co/ccfhYRbJ/paipal-1.png"
              alt="PayPal"
              class="icone-cartao"
            />
            <img
              src="https://i.ibb.co/ybp3bbW/Master-Card-Logo-1979-1.png"
              alt="Mastercard"
              class="icone-cartao"
            />
            <img
              src="https://i.ibb.co/bgpdtpx0/VISA-card-logo-1.png"
              alt="Visa"
              class="icone-cartao"
            />
          </div>
        </div>
      </div>
      <hr class="linha-divisoria" />
      <p class="copyright">© Alguns direitos reservados | IFBooks 2025</p>
    </footer>
</template>

<style scoped>
.autor-abril {
  display: flex;
  justify-content: center;
  align-items: center;
  gap: 5rem;
  padding: 4rem 2rem;
  margin-bottom: 2px solid #4E1EB5;
  font-family: 'Poppins', sans-serif;
}
.autor-abril .holly,
.autor-abril .img {
  margin: 0; 
  width: 40%;
  max-width: 400px;
}

.autor-abril h1 {
  font-weight: bold;
  font-size: xxx-large;
  color: #382C2C;
}
.autor-abril p {
  color: #4D4C4C;
}
.autor-abril div.holly {
  margin: 0 5vw;
  width: 45%;
}
.autor-abril div.holly div {
  width: 130px;
  border: 2px solid #4E1EB5;
  padding: 7px 0 7px 0;
  margin: 2rem 0;
  border-radius: 8px;
  text-align: center;
  box-shadow: 0 4px 8px rgba(0, 0, 0, 0.1);
}
.autor-abril div.holly span {
  color: #4E1EB5;
}
#povo-do-ar {
  color: #4E1EB5;
  font-weight: bold;
}
.autor-abril div.holly p {
  max-width: 500px;
}
.autor-abril button {
  font-family: 'Poppins', sans-serif;
  background-color: #4E1EB5;
  color: white;
  border: none;
  border-radius: 4px;
  padding: 0.75rem 1.5rem;
  margin-top: 1.5rem;
  font-size: 1rem;
  cursor: pointer;
  transition: background-color 0.3s;
}
.autor-abril button:hover {
  background-color: #3b0ca0;
}
.autor-abril div.img {
  margin: 0 5vw;
  width: 45%;
}
.autor-abril div.img img {
  width: 440px;
  height: auto;
}
.autor-abril div.img p {
  font-size: 15px;
  color: #4D4C4C;
  margin-top: 8px;
  text-align: right;
}
/*MENU*/
header {
  font-family: 'Poppins', sans-serif;
}
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
  font-family: 'Poppins', sans-serif;
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
  row-gap: 75px;
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
  padding: 13px 80px;
  font-size: 16px;
  cursor: pointer;
  display: flex;
  align-items: center;
  gap: 8px;
}
.icone-coracao {
  font-size: 18px;
  color: #4e1eb5;
}
/* CARRINHO */
.pagina-carrinho {
  padding: 3rem;
  font-family: 'Poppins', sans-serif;
  max-width: 700px;
}
.pagina-carrinho h1 {
  color: #4E1EB5;
  font-size: xx-large;
}
.pagina-carrinho h2 {
  font-weight: bold;
  font-size: x-large;
}
.pagina-carrinho h3 {
  font-weight: bold;
  font-size: large;
}
.pagina-carrinho .titulos {
  display: flex;
  gap: 25vw;
}

.container-titulos {
  display: flex;
}

.item-carrinho {
  display: flex;
  justify-content: space-between;
  align-items: center;
  margin-bottom: 20px;
  border-bottom: 1px solid #ddd;
  padding-bottom: 1rem;
}
.item-carrinho p {
  margin: 0;
}
.coluna {
  display: flex;
}
.coluna span {
  font-weight: bold;
}
.info-livro-carrinho {
  display: flex;
}
.imagem-livro-carrinho {
  width: 100px; 
  height: auto; 
  border-radius: 8px; /* opcional: cantos arredondados */
  margin-right: 6px; 
}

.quantidade-area {
  display: flex;
  align-items: center;
}

.btn-quantidade {
  background-color: #4E1EB5;
  color: white;
  border: none;
  padding: 4px 10px;
  font-size: 1rem;
  font-weight: bold;
  cursor: pointer;
  border-radius: 4px;
  transition: background-color 0.2s ease;
}

.btn-quantidade:hover {
  background-color: #3a1694;
}

.quantidade-area span {
  min-width: 30px;
  text-align: center;
  display: inline-block;
  font-weight: bold;
  font-size: 1rem;
}

.btn-remover {
  background-color: transparent;
  color: #ff4d4d;
  border: none;
  font-size: 1rem;
  cursor: pointer;
  font-weight: bold;
}

.btn-remover:hover {
  color: #d10000;
}

.total {
  margin-top: 1rem;
  font-size: 1.2rem;
  text-align: right;
}

.btn-voltar {
  margin-top: 20px;
  padding: 10px 20px;
  background-color: white;
  color: black;
  border: 2px solid black;
  border-radius: 4px;
  cursor: pointer;
  font-weight: bold;
  display: block;
  margin-left: auto;
  margin-right: auto;
  transition: background-color 0.2s ease;
}

.btn-voltar:hover {
  background-color: #f7f4fd;
}

/* rodapé */
.rodape {
  margin: 10vw 0 0 0;
  background-color: #4e1eb5;
  color: white;
  font-size: 14px;
  font-family: 'Poppins', sans-serif;
}
.container-rodape {
  padding: 40px 10vw 20px;
  display: flex;
  justify-content: space-between;
  flex-wrap: wrap;
  align-items: flex-start;
}
.redes-sociais .logo {
  font-size: 15px;
  margin-bottom: 10px;
  color: white;
  text-decoration: none;
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
  width: 100%;
  height: 2px;
  background-color: rgba(218, 208, 224, 0.726);
  border: none;
  margin: 20px 0;
}
.copyright {
  text-align: center;
  padding: 10px;
  font-size: 12px;
  color: rgba(218, 208, 224, 0.726);
}
</style>