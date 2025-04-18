<script setup>
</script>

<template>
<body>
  <main>
    <section class="autor-abril">
      <div class="holly">
        <div>
          <p><span>Autora de Abril</span></p>
        </div>
        <h1>Holly Black</h1>
        <p>Holly Black é uma escritora e editora norte-americana mais conhecida por sua ficção infantil e juvenil. Seu trabalho a série O Povo do Ar, best-seller do The New York Times para jovens adultos.</p>
        <button @click=''>Acessar página do livro</button>
      </div>
      <div class="img">
        <img src="https://i.ibb.co/RTy0nbh0/image-removebg-preview.png" alt="principe-cruel">
        <p>*within the stock limit</p>
      </div>
    </section>
  </main>
</body>
</template>

<style scoped>
body {
  font-family: 'Poppins', sans-serif;
}
body main section.autor-abril {
  display: flex;
  border-top: 2px solid #4E1EB5;
  padding-top: 4vw;
  border-bottom: 2px solid #4E1EB5;
  padding-bottom: 4vw;
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
  margin: 0 8vw 0 8vw;
}
.autor-abril div.holly div {
  width: 130px;
  border: 2px solid #4E1EB5; /*borda*/
  padding: 7px 0 7px 0;
  margin: 2rem 0;
  border-radius: 8px;
  text-align: center;
  box-shadow: 0 4px 8px rgba(0, 0, 0, 0.1); /*sombra*/
}
.autor-abril div.holly span {
  color: #4E1EB5;
}
.autor-abril div.holly p {
  max-width: 500px;
}
.autor-abril button {
  font-family: 'Poppins', sans-serif;;
  background-color: #4E1EB5;
  color: white;
  border: none; /*tirar a borda visível*/
  border-radius: 4px;
  padding: 0.75rem 1.5rem;
  margin-top: 1.5rem;
  font-size: 1rem;
  cursor: pointer;
  transition: background-color 0.3s;
}
.autor-abril button:hover {
  background-color: #3b0ca0; /*roxo mais escuro quando passa o mouse*/
}
.autor-abril div.img {
  display: flex;
  flex-direction: column;
  align-items: flex-end; 
  margin: 0 8vw;
}
.autor-abril div.img img {
  width: 440px;
  height: auto;
}
.autor-abril div.img p {
  font-size: 16px;
  color: #4D4C4C;
  margin-top: 8px; 
  text-align: right;
}
</style>