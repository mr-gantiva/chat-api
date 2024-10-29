<script setup>
import { defineProps } from 'vue'

const props = defineProps({
    chat: Array
});
</script>
<template>
    <div class="box__chat">
        <div class="chat__content" v-for="(mensaje, i) in chat" :key="i"
            :class="{ 'left__user--chat': mensaje.user === 'left', 'right__user--chat': mensaje.user === 'right' }">
            <span class="user__name">{{ mensaje.name }}</span>
            <div class="py-3">
                <p :style="{ backgroundColor: mensaje.color }">{{ mensaje.text }}</p>
            </div>
        </div>
        <!-- <div v-for="(mensaje2, i) in mensajes2" :key="i" class="right__user--chat">
      <p>{{ mensaje2 }}</p>
    </div> -->
    </div>
</template>

<style>
.box__chat {
    width: 100%;
    height: 500px;
    overflow: auto;
    background-image: url(../img/fondo-pantalla.jpg);
    background-size: cover;
    padding: 20px;
    border-radius: 10px;
    box-shadow: 0 4px 30px rgba(0, 0, 0, 0.1);
    border: 1px solid goldenrod;
}



.left__user--chat {
    text-align: left;
}

.left__user--chat p,
.right__user--chat p {
    width: 100%;
    display: inline;
    padding: 10px 20px;
    border-radius: 50px;
}

.right__user--chat {
    text-align: right;
}

.user__name {
    color: #fff;
}
</style>