<template>
  <div class="black-bg" v-if="modalOpen === true">
    <div class="white-bg">
      <h2>{{ rooms[pressed].title }}</h2>
      <img :src="rooms[pressed].image" class="room-img" />
      <p>{{ rooms[pressed].content }}</p>
      <input type="text" @input="months = $event.target.value">
      <h4>{{ months }}개월, {{ rooms[pressed].price * months }} 원</h4>
      <button @click="$emit('modalClose')">닫기</button>
    </div>
  </div>
</template>

<script>
export default {
    name : 'ModalVue',
    props : {
        rooms : Array,
        pressed : Number,
        modalOpen : Boolean,
    },
    data(){
      return{
        months : 1,
      };
    },
}
</script>

<style></style>
