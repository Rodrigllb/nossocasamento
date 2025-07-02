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
          <form id="formulário">
            <input type="text" id="digiteSeuNome" placeholder="Digite seu nome" required >
            <input type="text" id="digiteSeuTel" placeholder="Digite seu telefone" required>
    
            <select name="ativarLista" id="ativarLista" required>
              <option value="Presentei-nos">Escolha um presente!</option>
              <option value="R$50,00">R$50,00</option>
              <option value="R$100,00">R$100,00</option>
              <option value="R$150,00">R$150,00</option>
              <option value="R$200,00">R$200,00</option>
              <option value="Escorredor de pratos">Escorredor de pratos</option>
              <option value="Kits de potes de vidro">Kits de Potes de vidro</option>
              <option value="Açucareiro">Açucareiro</option>
              <option value="Jogo de panelas">Jogo de panelas</option>
              <option value="Tábua com espátula">Tábua com espátula</option>
              <option value="Batedeira">Batedeira</option>
              <option value="Kit de lixo para conzinha">Kit de lixo para cozinha</option>
              <option value="Baldes de plástico">Baldes de plástico</option>
              <option value="Kit banheiro">Kit banheiro</option>
              <option value="Tapetes">Tapetes</option>
              <option value="Jogos de copos">Jogo de copos</option>
              <option value="Concha + Porta-Tempêros">Concha + Porta-Tempêros</option>
              <option value="Forma de bola">Forma de bolo</option>
              
            </select>

            <button type="submit" id="enviarDados">Enviar</button>
          </form>
        </section>

        <section class="simOuNao"> <!--Apelo ao convidado-->
          <p id="SIM">Sim</p>
          <p id="NAO">Não</p>
        </section>

        <section class="agradecimento"> <!--Agradecimento pela escolha recusada.-->
          <p>Gratidão, Deus abençoe!</p>
        </section>

        <section class="copyright">
          <small>Developed by Rodrigo & Paula <br> Todos os direitos reservados 2025</small>
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

//INTERATIVIDADE DA PÁGINA INICIAL -> ACEITAR OU RECUSAR.

document.addEventListener('DOMContentLoaded', ()=> {

  let conviteAceito = document.getElementById('SIM');
  let apeloAoConvidado = document.getElementsByClassName("simOuNao");
  let preencherDados = document.getElementsByClassName("digiteOnome");
  let conviteRecusado = document.getElementById('NAO');
  let agradecerAoUsuario = document.getElementsByClassName("agradecimento");

  conviteAceito.addEventListener('click', function exec() { /*CASO O USUARIO TENHA ACEITO O CONVITE */
    
    preencherDados[0].style.display = "flex";
    apeloAoConvidado[0].style.display = "none";

  });

  conviteRecusado.addEventListener('click', function recusado() { /*CASO O USUARIO NÃO TENHA ACEITADO O CONVITE */
    apeloAoConvidado[0].style.display = 'none';
    agradecerAoUsuario[0].style.display = 'flex';
  })



  /*****ENVIAR DADOS PARA A PLANILHA******/
  const formularioInserir = document.getElementById('formulário');
  formularioInserir.addEventListener('submit', async (event) => {
  event.preventDefault();

  const nome = document.getElementById('digiteSeuNome').value;
  const telefone = document.getElementById('digiteSeuTel').value;
  const presentes = document.getElementById('ativarLista').value;

  try {
    const response = await fetch('https://script.google.com/macros/s/AKfycbwtk5q1JmFbq20gNheNXa6djSc1eP-ryF9NOT1AOjxtuPLm22w_y0C79bdp2r5yLBck6A/exec', {
      method: 'POST',
      mode: 'no-cors', // Ou 'no-cors' caso você queira apenas enviar sem ver resposta
      headers: {
        'Content-Type': 'application/json'
      },
      body: JSON.stringify({ nome, telefone, presentes })
    });

    // Verificar se a requisição foi bem-sucedida
    if (response.ok) {
      alert('Enviado com sucesso!');
    } else {
      //Mesmo que a requisição não seja bem-sucedida os dados mesmo assim são enviados para levantamento interno.
      alert('Dados enviados com sucesso: ' + response.statusText);
    }

    // Resetando o formulário
    formularioInserir.reset();

  } catch (error) {
    // Caso ocorra um erro na requisição
    console.error('Erro ao enviar os dados:', error);
    alert('Ocorreu um erro ao enviar os dados.');
  }
});

  
});

</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>

* { /*Estilizações globais*/
  padding: 0; 
  margin: 0;
  box-sizing: border-box;
}
  #containerPrincipal { /*Container principal da pagina inicial*/
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
 
  .containerFilho { /*Container filho*/
    border-radius: 25px;
    background-color: #f1f1f1da;
    padding: 45px;
  }

  header { /*Cabeçalho onde contém a logo */
    display: flex;
    align-items: center;
    justify-content: center;
    width: 100%;
    height: auto;
  }
  header img {
    width: 185px;
  }

  main article { /*Corpo do documento onde contém textos e o formulário para preenchimento */
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

  .contextualizaçao { /*Container onde contém a contextualização referente ao convite*/
    opacity: 80%;
  }

  .aceitaNossoConvite h2 { /*Container onde está a estilização do titulo de nível 2*/
    font-family: 'Alex Brush';
    font-size: 45px;
    font-weight: 200;
    padding: 0;
    margin: 0;
  }

  .simOuNao { /*Container de apelo ao convidado*/
    display: flex;
    flex-direction: row;
    align-items: center;
    justify-content: space-around;
    width: auto;
    height: 95px;

  }
  .simOuNao #SIM { /*Botão de aceitar */
    background-color: #6B8E23;
    color: #f1f1f1;
    padding: 12px;
    width: 75px;
    border-radius: 25px;
    cursor: pointer;
  }
  .simOuNao #NAO { /*Botão de recusar */
    background-color: #B22222;
    color: #f1f1f1;
    padding: 12px;
    width: 75px;
    border-radius: 25px;
    cursor: pointer;
  }
  #SIM:hover {
    opacity: 50%;
  }
  #NAO:hover {
    opacity: 50%;
  }

  /* CASO O CONVIDADO DIGA SIM */
  .digiteOnome { /*Estilização do container onde está o formulário e demais elementos*/
    display: none;
    flex-direction: column;
    width: 100%;
    height: auto;
  }
  .digiteOnome form {
    display: flex;
    flex-direction: column;
  }

  .digiteOnome input {
    padding: 12px;
    margin-top: 5px;
    border-radius: 25px;
    border: none;
  } 
  .digiteOnome button {
    background-color: #6B8E23;
    color: #f1f1f1;
    border: none;
    padding: 12px;
    margin-top: 5px;
    border-radius: 25px;
  }

  /* CASO O CONVIDADO RECUSE */
  .agradecimento {
    display: none;
    align-items: center;
    justify-content: center;
    background-color: #6a8e2373;
    height: 45px;
    width: auto;
    border-radius: 22px;
    
  }


  /*Direitos Autorais*/
  .copyright {
    padding-top: 22px;
    font-family: 'poppins';
    font-size: 12px;
  }

  /*Lista de presentes*/

  #ativarLista {
    background-color: #fff;
    padding: 12px;
    margin-top: 5px;
    border-radius: 25px;
    border: none;
  }



</style>  
