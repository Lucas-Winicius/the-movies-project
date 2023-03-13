<template>
    <div id="emptyMessage">
        <p>Tudo está tão vazio...</p>
        <small>Algo não esta certo tente novamente em instantes.</small>
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
  color: rgb(229, 229, 229);
  font-size: 2.5em;
  position: absolute;
  top: 50%;
  left: 50%;
  transform: translate(-50%, -50%);
  user-select: none;
  pointer-events: none;
}

#emptyMessage > small {
  color: yellow;
  font-size: .5em;
}
</style>