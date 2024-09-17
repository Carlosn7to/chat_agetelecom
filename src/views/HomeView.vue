<script setup>

import {onBeforeMount, ref} from 'vue';

import {useRoute} from "vue-router";

const route = useRoute();

import logo from '@/assets/img/age_color_full.png';

const username = ref('');
const identify = ref('');

const url = ref('');

const iframe = ref(false);

const sendPayload = () => {
  if(username.value === '' || identify.value === '') {
    alert('Preencha todos os campos!');
  } else {

    if(route.path === '/ReclameAqui' || route.path === '/reclameaqui') {

      url.value = `https://agetelecom.digitro.cloud/chatclient/chat.php?ci=${username.value}-${identify.value}-ReclameAqui&servico=Servico37.chat&aplicacao=interact`
    } else {
      url.value = `https://agetelecom.digitro.cloud/chatclient/chat.php?ci=${username.value}-${identify.value}-Portal&servico=Servico3.chat&aplicacao=interact`
    }

    iframe.value = true;

  }
}

</script>

<template>

<div class="container" v-if="!iframe">
  <div class="form">
    <div class="logo">
      <img :src="logo" alt="">
    </div>
    <div class="title">
      <h1>Bem-vindo(a) a Age Fibra!</h1>
      <p>Estamos prontos para te atender! Por favor, <br> insira suas informações</p>
    </div>
    <br>
    <div class="input">
      <label for="name">Nome</label>
      <input v-model="username" name="name" type="text" placeholder="Como gostaria de ser chamado?" autocomplete="off">
    </div>
    <div class="input">
      <label for="identify">CPF ou CNPJ do titular</label>
      <input v-model="identify" name="identify" type="text" placeholder="Apenas números, por favor." autocomplete="off">
    </div>
    <button @click="sendPayload">Iniciar chat</button>
  </div>

</div>

  <iframe v-if="iframe" :src="url" frameborder="0"></iframe>

</template>

<style scoped>


.container {
  background-image: url("../assets/img/bg-main.png");
  width: 100vw;
  height: 100vh;
  background-size: cover;
  background-repeat: no-repeat;
  display: flex;
  justify-content: center;
  align-items: center;

  .form {
    background-color: #fff;
    padding: 4vh 2vw 6vh 2vw;
    border-radius: 10px;
    box-shadow: 0 0 10px rgba(0, 0, 0, 0.1);
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: center;
    position: relative;
    overflow: hidden;

    .logo {
      img {
        width: 9vw;
        height: auto;
        display: block;
        margin: 0 auto 2vh auto;
      }
    }

    &:before {
      content: '';
      position: absolute;
      bottom: -120px; /* Ajuste esse valor para descer a imagem ainda mais */
      left: -100px;
      width: 100%;
      height: 100%;
      background-image: url("../assets/img/logo_grey.png");
      background-size: 80%;
      background-repeat: no-repeat;
      background-position: bottom left;
      opacity: 0.08; /* Ajuste a opacidade aqui */
      z-index: 1; /* Coloque a imagem atrás do conteúdo */
    }

    .title {
      text-align: center;
      h1 {
        font-size: 1.5rem;
        color: #333333;
        font-weight: 500;
        margin-bottom: 1vh;
      }
      p {
        font-size: 1rem;
        margin: 0;
        color: #333333;
        font-weight: 400;
      }
    }

    .input {
      width: 80%;
      margin-bottom: 2vh;
      text-align: left;
      z-index: 99;

      label {
        font-size: .9rem;
        padding-left: 5px;
        font-weight: 500;
        color: #333333;
      }
      input {
        padding: 15px 10px;
        font-size: 1rem;
        outline: none;
        border-radius: 15px;
        width: 100%;
        background-color: #F9FAFB;
        font-weight: 500;
        color: #333333;
        border: 1px solid #f2f2f2;
        transition: border-color .3s ease-in-out;

        &:focus {
          border: 1px solid #f97316;
        }

        &::placeholder {
          color: #B1B1B1;
        }
      }


    }

    button {
      padding: 10px 80px;
      background-color: #f97316;
      color: #fff;
      border: none;
      border-radius: 20px;
      cursor: pointer;
      transition: 0.3s;
      font-weight: 500;
      font-size: 1.2rem;
      margin-top: 1vh;
      z-index: 99;

      &:hover {
        background-color: #c2410c;
      }
    }
  }
}

iframe {
  width: 100vw;
  height: 100vh;
  border: none;
  position: absolute;
  top: 0;
  left: 0;
}

@media {
  .container {
    .form {
      padding: 3vh 0vw 5vh 0vw;

      .title {
        h1 {
          font-size: 1.2rem;
        }

        p {
          font-size: .9rem;
        }
      }

      .input {
        width: 80%;
        label {
          font-size: .9rem;
        }

        input {
          font-size: 1rem;
        }
      }
      .logo {
        img {
          width: 35vw;
        }
      }
    }
  }
}

</style>

