<template>
  <div id="emptyMessage">
    <p>
      {{ errorCode ? `Error: ${errorCode}` : "It's so empty here..." }}
    </p>
    <small>
      {{
        textMessage
          ? textMessage
          : "Something isn't right, try again in a moment."
      }}
    </small>
  </div>
</template>

<script>
export default {
  name: 'ErrorMessage',
  props: {
    errorCode: { type: Number },
    textMessage: { type: String }
  },
}
</script>

<style scoped>
#emptyMessage {
  text-align: center;
  color: rgb(135, 135, 135);
  font-size: 2.5em;
  pointer-events: none;
}

#emptyMessage > small {
  color: rgb(255, 2, 0);
  font-size: 0.5em;
}
</style>