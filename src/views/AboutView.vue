<template>
  <div class="counter-app">
    <h1 class="counter-title">Count is: {{ count }}</h1>
    <div class="counter-controls" id="controller">
      <button class="counter-btn increment-btn" @click="increment">+</button>
      <button class="counter-btn decrement-btn" @click="decrement">-</button>
      <button class="counter-btn reset-btn" @click="reset">Reset</button>
    </div>

    <div class="counter-controls">
      <input type="number" v-model="value" class="counter-input">
      <button class="counter-btn set-btn" @click="setValue(value)">Set Value</button>
    </div>
  </div>
</template>

<script>
import { useStore } from 'vuex';
import useCounter from '@/useCounter';

export default {
  setup() {
    const store = useStore();
    const { count, increment, decrement, reset, setValue } = useCounter;

    function setCount() {
      store.dispatch('setValue', count.value);
    }

    return {
      count,
      increment,
      decrement,
      reset,
      setCount,
      setValue
    };
  }
};
</script>


<style>
.counter-app {
  display: flex;
  flex-direction: column;
  align-items: center;
  margin-top: 50px;
}

.counter-title {
  font-size: 3rem;
  font-weight: bold;
  margin-bottom: 30px;
}

.counter-controls {
  display: flex;
  flex-direction: row;
  align-items: center;
  justify-content: center;
  margin-bottom: 30px;
}

.counter-btn {
  font-size: 2rem;
  font-weight: bold;
  padding: 10px 20px;
  margin: 0 10px;
  border-radius: 5px;
  border: none;
  color: black;
  cursor: pointer;
  transition: all 0.2s ease-in-out;
}

.increment-btn {
  background-color: yellow;
  opacity: 0.5;
  border-radius: 50%;
  border: 2px solid gray;
}

.decrement-btn {
  background-color: blue;
  opacity: 0.5;
  border-radius: 50%;
  border: 2px solid gray;
}

.reset-btn {
  background-color: red;
  opacity: 0.5;
  border-radius: 10%;
  border: 2px solid gray;

}

.set-btn {
  background-color: lightslategrey;
}

.counter-btn:hover {
  transform: scale(1.1);
  opacity: 1;
}

.counter-input {
  font-size: 2rem;
  font-weight: bold;
  margin: 0 10px;
  padding: 5px;
  border-radius: 5px;
  border: none;
  text-align: center;
  width: 150px;
  border: 2px solid black;
}

@media (max-width: 768px) {
  /* Adjust styles for screens smaller than 768px */
  .counter-title {
    font-size: 2rem;
  }
  
  .counter-controls {
    flex-direction: column;
  }
  
  .counter-input {
    margin: 10px 0;
  }

  #controller {
    gap: 10px;
  }
}
</style>
