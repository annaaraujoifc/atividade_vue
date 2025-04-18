<script setup>

</script>

<template>
<body>
  <main>
    <section class="autor-abril">
      <div class="holly">
        <p id="autora">Autora de Abril</p>
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
  body main section.autor-abril {
    display: flex;
    border-top: 2px solid #4E1EB5;
    padding-top: 4vw;
    border-bottom: 2px solid #4E1EB5;
    padding-bottom: 4vw;
    /*margin: 0 6vw 0 6vw; */
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
  .autor-abril div.holly p {
    max-width: 500px;
  }
  .autor-abril #autora {
    border: 2px solid #4E1EB5;
    color: #4E1EB5;
  }
  .autor-abril button {
    background-color: #4E1EB5;
    color: white;
    border-color: #4E1EB5;
    border-radius: 2px;
    padding: 10px 15px 10px 15px;
    margin: 1.5vw 0 0 0;
  }
  .autor-abril div.img {
    margin: 0 8vw 0 8vw;
  }
  .autor-abril div.img p{
    padding: 0 12vw 0 12vw;
  }
</style>