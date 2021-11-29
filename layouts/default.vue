<template>
  <div class = "container">
    <NuxtLink to="/">
      <h1>TV Show Search App!</h1>
    </NuxtLink>
    <slot></slot>
  </div>
</template>

<style>
.container {
  margin-top: 25px;
  display: flex;
  justify-content: center;
  align-items: center;
  flex-direction: column;
  gap: 5px;
}

.container a{
   text-decoration: none;
}

</style>