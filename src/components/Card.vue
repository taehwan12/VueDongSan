<template>
  <div>
    <img :src="room.image" class="room-img" />
    <h3 @click="$emit('modalOpen', room.id)">{{ room.title }}</h3>
    <p>{{ room.price }} 원</p>
  </div>
</template>

<script>
export default {
  name: "CardVue",
  props: {
    room: Object,
  },
};
</script>

<style></style>