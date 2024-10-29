<script setup>
import { ref, onMounted } from 'vue';
import axios from 'axios';

import ChatBox from './components/ChatBox.vue';

let usuarios = ref([])
let leftUser = ref(null);
let rightUser = ref(null);

const inputText = ref('');
const inputText2 = ref('');
const chat = ref([]);

const colorBox = ref('#CCEAFF');
const colorBox2 = ref('#FFFEFA');

const getUsuarios = async () => {
  try {
    const url = "https://randomuser.me/api?results=2";
    const { data } = await axios.get(url);
    usuarios.value = data.results;

    if (usuarios.value.length >= 2) {
      leftUser.value = usuarios.value[0];
      rightUser.value = usuarios.value[1];
    }
  } catch (error) {
    console.log(error)
  }
}

const enviarMensaje = (user) => {
  if (user === 'left' && inputText.value.trim()) {
    chat.value.push({ user: 'left', text: inputText.value, name: `${leftUser.value.name.first} ${leftUser.value.name.last}`, color: colorBox.value });
    inputText.value = "";
  }
  if (user === 'right' && inputText2.value.trim()) {
    chat.value.push({ user: 'right', text: inputText2.value, name: `${rightUser.value.name.first} ${rightUser.value.name.last}`, color: colorBox2.value });
    inputText2.value = "";
  }
}


onMounted(getUsuarios());

// const fotosUsuariosLarge = computed(() => {
//   return usuarios.value.map((usuario) => usuario.picture.large);
// });

</script>

<template>
  <section class="container-fluid px-0">
    <div class="container main__container d-flex flex-column justify-content-center">
      <div class="row">
        <div class="col-12 col-md-6 offset-md-3">
          <div class="titulo my-5">
            <h1 class="text-center py-5">Chat API</h1>
          </div>
        </div>
      </div>

      <div class="row">
        <div class="col-12 col-md-3">
          <div v-if="leftUser" class="left__user d-flex flex-column justify-content-center align-items-center">
            <div class="card__header">
              <img :src="leftUser.picture.large" alt="">
            </div>
            <div class="card__body">
              <h4 class="text-center name__color py-2">{{ leftUser.name.first }} {{ leftUser.name.last }}</h4>
              <input class="inputColor p-0" type="color" id="" v-model="colorBox" @mouseenter="showTooltip"
                @mouseleave="hideTooltip">
              <div>
                <textarea class="inputText" v-model="inputText" name="" id=""></textarea>
              </div>
            </div>
            <div class="card__footer  w-100">
              <button class="w-100 btn__enviar" @click="enviarMensaje('left')">Enviar</button>
            </div>
          </div>
        </div>

        <div class="col-12 col-md-6">
          <ChatBox :chat="chat" />
        </div>

        <div class="col-12 col-md-3">
          <div v-if="rightUser" class="right__user  d-flex flex-column justify-content-center align-items-center">
            <div class="card__header">
              <img :src="rightUser.picture.large" alt="">
            </div>
            <div class="card__body">
              <h4 class="text-center name__color  py-2">{{ rightUser.name.first }} {{ rightUser.name.last }}</h4>
              <input class="inputColor p-0" type="color" id="" v-model="colorBox2">
              <textarea class="inputText" v-model="inputText2" name="" id=""></textarea>
            </div>
            <div class="card__footer w-100">
              <button class="w-100 btn__enviar" @click="enviarMensaje('right')">Enviar</button>
            </div>
          </div>
        </div>
      </div>
    </div>
  </section>

</template>

<style scoped>
.container-fluid {
  background-color: #202B38;
}

.main__container {
  background-color: #202B38;
  min-height: 100dvh;
  /* display: flex; */
}

:is(.inputColor, .inputText) {
  width: 100%;
  border: none;
  border-radius: 8px;
}

.inputText {
  min-height: 120px;
}

.card__header img {
  border-radius: 10px;
}

.card__body {
  width: 100%;
}

:is(.right__user, .left__user) {
  background: rgba(255, 255, 255, 0.2);
  border-radius: 16px;
  box-shadow: 0 4px 30px rgba(0, 0, 0, 0.1);
  backdrop-filter: blur(5px);
  -webkit-backdrop-filter: blur(5px);
  border: 1px solid rgba(255, 255, 255, 0.3);
  padding: 20px;
  min-height: 500px;
}

.name__color {
  color: #fafaf5;
}

.btn__enviar {
  background-color: gold;
  border: none;
  padding: 5px 10px;
  border-radius: 5px;
  transition: all 0.25s ease;

  &:hover {
    background-color: goldenrod;
    transform: scale(0.98);
  }
}

.titulo {
  color: goldenrod;
  border: 1px solid goldenrod;
  border-radius: 10px;
  background: rgba(255, 255, 255, 0.07);
  border-radius: 16px;
  box-shadow: 0 4px 30px rgba(0, 0, 0, 0.1);
  backdrop-filter: blur(5px);
  -webkit-backdrop-filter: blur(5px);
  border: 1px solid rgba(255, 255, 255, 0.3);
}
</style>
