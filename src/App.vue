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

const totalCarrinho = computed(() =>
  carrinho.value.reduce((total, item) => total + item.preco * item.quantidade, 0).toFixed(2)
)
</script>

<template>
  <div class="menu">
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
  </div>

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
        <div v-for="item in carrinho" :key="item.id" class="item-carrinho">
          <p><strong>{{ item.titulo }}</strong></p>
          <input type="number" v-model.number="item.quantidade" min="1" />
          <p>Subtotal: R$ {{ (item.preco * item.quantidade).toFixed(2) }}</p>
        </div>
        <hr>
        <p class="total"><strong>Total: R$ {{ totalCarrinho }}</strong></p>
      </div>
      <button @click="paginaAtual = 'home'" class="btn-voltar">Voltar para loja</button>
    </section>
  </main>
</template>


<style scoped>
body {
  font-family: 'Poppins', sans-serif;
}

.autor-abril {
  display: flex;
  justify-content: center;
  align-items: center;
  gap: 5rem;
  padding: 4rem 2rem;
  margin-bottom: 2px solid #4E1EB5;
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