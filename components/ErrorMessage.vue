<template>
  <div id="emptyMessage">
    <p>{{ errorCode }}</p>
    <small>
      {{ textMessage }}
    </small>
  </div>
</template>

<script>
export default {
  name: 'ErrorMessage',
  props: {
    errorCode: { type: String, default: "It's so empty here..." },
    textMessage: {
      type: String,
      default: "Something isn't right, try again in a moment.",
    },
  },
}
</script>

<style scoped>
#emptyMessage {
  text-align: center;
  color: rgb(135, 135, 135);
  font-size: 2.5em;
  pointer-events: none;

  position: absolute;
  top: 50%;
  left: 50%;
  transform: translate(-50%, -50%);
}

#emptyMessage > small {
  color: rgb(255, 2, 0);
  font-size: 0.5em;
}
</style>
