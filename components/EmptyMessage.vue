<template>
    <div id="emptyMessage">
        <p>It's so empty here...</p>
        <small>Something isn't right, try again in a moment.</small>
    </div>
</template>

<script>
export default {
    name: 'EmptyMessage',
}
</script>

<style scoped>
#emptyMessage {
  text-align: center;
  color: rgb(135, 135, 135);
  font-size: 2.5em;
  position: absolute;
  top: 50%;
  left: 50%;
  transform: translate(-50%, -50%);
  user-select: none;
  pointer-events: none;
}

#emptyMessage > small {
  color: rgb(255, 2, 0);
  font-size: .5em;
}
</style>