<template functional>
  <div>
    <form class="container--searchbar"
          @submit.prevent="listeners['submit']">
      <div class="searchbar--button button--u">
        <span class="u--content">/u/</span>
      </div>
      <input autofocus
             class="searchbar--input">
      <button :class="`searchbar--button 
                       button--send 
                       ${props.pulse ? 'pulse': ''}`">
        🔍
      </button>
    </form>
  </div>
</template>

<style lang="scss" scoped>
$radius: 5px;

@mixin format {
  padding: 0.25rem 1rem;
  border: none;
  transition: background-color 0.25s;

  &:focus {
    outline: none;
  }
}

.container--searchbar {
  display: flex;
  justify-content: center;
  padding: 1rem;
  height: 30%;
  filter: drop-shadow(0 3px 1.5px rgba(0, 0, 0, 0.5));
}

.searchbar--input {
  width: 50%;
  background-color: rgb(235, 235, 235);
  font-size: 2rem;

  @include format;

  &:focus {
    background-color: rgb(230, 230, 230);
  }
}

.searchbar--button {
  background-color: rgb(255, 120, 60);
  color: rgb(255, 255, 255);
  font-size: 1.5rem;

  user-select: none;
  @include format;
}

.u--content {
  font-weight: 200;
  filter: drop-shadow(0 2px 1.5px rgba(0, 0, 0, 0.25));
}

.button--u {
  display: flex;
  align-items: center;
  border-top-left-radius: $radius;
  border-bottom-left-radius: $radius;
}

.button--send {
  border-top-right-radius: $radius;
  border-bottom-right-radius: $radius;
  cursor: pointer;
  transition: background-color 0.125s ease-in-out;

  &:hover {
    background-color: rgb(255, 77, 0);
  }
}

.pulse {
  animation: pulse 0.75s;
  pointer-events: none;
}

@keyframes pulse {
  0% {
    box-shadow: 0 0 0 0px rgb(255, 120, 60);
  }
  100% {
    box-shadow: 0 0 0 30px rgba(0, 0, 0, 0);
  }
}

@media screen and (min-width: 375px) {
  .container--searchbar {
    height: 30%;
  }
}

@media screen and (min-width: 768px) {
  .container--searchbar {
    height: 50%;
  }
}
</style>
