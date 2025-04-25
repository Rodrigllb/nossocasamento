<template>
  <div id="containerPrincipal">
    <div class="containerFilho">
      <header>
      <img src="./../assets/logo/logoCasamento.png" alt="logo dos noivos">
    </header>
    <main>
      <article>
        <section class="contextualizaçao">
          <p>Deus faz tudo perfeito em Seu tempo.
            E somos gratos por vivermos esse momento com pessoas tão especiais como você, que fazem parte da nossa história.</p>
        </section>
        <section class="aceitaNossoConvite">
          <h2>Aceita o nosso convite?</h2>
        </section>

        <section class="digiteOnome"> <!--Caso o convidado aceite o convite-->
          <input type="text" id="digiteSeuNome" placeholder="Digite seu nome" >
          <input type="tel" id="digiteSeuTel" placeholder="Digite seu telefone">
          <button type="submit" id="enviarDados">Enviar</button>
        </section>

        <section class="simOuNao"> <!--Apelo ao convidado-->
          <p id="SIM">Sim</p>
          <p id="NAO">Não</p>
        </section>

        <section class="agradecimento"> <!--Agradecimento pela escolha recusada.-->
          <p>Gratidão, Deus abençoe!</p>
        </section>

      </article>
    </main>
    </div>
    
  </div>
</template>

<script>
export default {
  name: 'homePage',
}
document.addEventListener('DOMContentLoaded', ()=> {
  let conviteAceito = document.getElementById('SIM');
  let apeloAoConvidado = document.getElementsByClassName("simOuNao");
  let preencherDados = document.getElementsByClassName("digiteOnome");


  conviteAceito.addEventListener('click', function exec() {
    
    preencherDados[0].style.display = "flex";
    apeloAoConvidado[0].style.display = "none";

  });
});

</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
* {
  padding: 0;
  margin: 0;
  box-sizing: border-box;
}
  #containerPrincipal {
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: center;
    width: 100%;
    height: 100vh;
    background-image: url('./../assets/fundo/fundoCasamento.png');
    background-position: center;
    background-repeat: no-repeat;
    background-size: cover;
    background-color: #f3f3f396;
  }

  .containerFilho {
    border-radius: 25px;
    background-color: #f1f1f1da;
    padding: 45px;
  }

  header {
    display: flex;
    align-items: center;
    justify-content: center;
    width: 100%;
    height: auto;
  }
  header img {
    width: 185px;
  }

  main article {
    display: flex;
    flex-direction: column;
    width: 100%;
    height: auto;
  }

  main article section {
    width: 220px;
    height: auto;
    text-align: center;
  }

  .contextualizaçao {
    opacity: 80%;
  }

  .aceitaNossoConvite h2 {
    font-family: 'Alex Brush';
    font-size: 45px;
    font-weight: 200;
    padding: 0;
    margin: 0;
  }

  .simOuNao {
    display: flex;
    flex-direction: row;
    align-items: center;
    justify-content: space-around;
    width: auto;
    height: 95px;

  }
  .simOuNao #SIM {
    background-color: #6B8E23;
    color: #f1f1f1;
    padding: 12px;
    width: 75px;
    border-radius: 5px;
    cursor: pointer;
  }
  .simOuNao #NAO {
    background-color: #B22222;
    color: #f1f1f1;
    padding: 12px;
    width: 75px;
    border-radius: 5px;
    cursor: pointer;
  }
  #SIM:hover {
    opacity: 50%;
  }
  #NAO:hover {
    opacity: 50%;
  }

  /* CASO O CONVIDADO DIGA SIM */
  .digiteOnome {
    display: none;
    flex-direction: column;
    width: 100%;
    height: auto;

  } 
  .digiteOnome input {
    padding: 12px;
    margin-top: 5px;

  } 
  .digiteOnome button {
    background-color: #6B8E23;
    color: #f1f1f1;
    border: none;
    padding: 12px;
    margin-top: 5px;
  }

  /* CASO O CONVIDADO RECUSE */
  .agradecimento {
    display: none;
  }
</style>  
