<template>
    <div class="counter-app-container">
        <h1 class="counter-heading">Counter</h1>
        <p id="counter">{{ count }}</p>
        <div class="button-container">
            <button
                id="decrease"
                aria-label="decrease button"
                @click="decreaseCount"
                :style="[this.count<=0 ? {'background': '#6ca5b6'} : {'background': '#44b3d7'}]"
            >
                {{ decrease }}
            </button>
            <button
                id="increase"
                aria-label="increase button"
                @click="increaseCount"
            >
                {{ increase }}
            </button>
        </div>
    </div>
</template>

<script>
export default {
    name: "Vue Counter App",
    data() {
        return {
            count: 0,
            increase: "UP ",
            decrease: "DOWN",
        };
    },
    methods: {
        increaseCount() {
            this.count++;
        },
        decreaseCount() {
            if (this.count <= 0) {
                this.count = 0;

                
            } else {
                this.count--;
            }
        },
    },
};
</script>

<style>


.counter-app-container {
  width: 100%;
  height: 100vh;
  background-color: #52a125;
  background-image: linear-gradient(160deg, #6f0cf1 0%, #f5f4f7 100%);
  display: flex;
  align-items: center;
  justify-content: center;
  color: #fff;
  font-family: "Poppins", sans-serif;
  flex-direction: column;
}

.counter-heading {
  font-size: 40px;
  letter-spacing: 1px;
  background-color: rgb(175, 128, 238);
  border-radius: 10px;

}

#counter {
  font-size: 75px;
  margin: 35px 0;
}

.button-container {
  width: 100%;
  display: flex;
  flex-direction: row;
  flex-wrap: wrap;
}

button {
  font-size: 30px;
  padding: 20px 40px;
  color: #fff;
  border: 1px solid #fff;
  cursor: pointer;
  background: #44b3d7;
  position: relative;
  border-radius: 8px;
  overflow: hidden;
  margin: auto;
}

button::before {
  content: "";
  width: 200px;
  height: 40px;
  background-color: rgba(255, 255, 255, 0.2);
  position: absolute;
  top: 0;
  left: -180px;
  transform: rotate(45deg);
  transition: 0.3s;
}

#increase {
  margin-left: 0;
}

button:not(:last-child) {
  margin-right: 25px;
}

button:hover {
  background-color: rgba(215, 68, 124, 0.4);
}

button:hover::before {
  left: 250px;
}

/* Media Queries */
@media (max-width: 684px) {
  .button-container {
    flex-direction: column;
  }
  button:not(:last-child) {
    margin: 25px auto;
  }
  #increase {
    margin-left: auto;
  }
}

@media (max-width: 364px) {
  button {
    font-size: 20px;
    padding: 15px 30px;
  }
  .counter-heading {
    font-size: 40px;
  }
  #counter {
    font-size: 65px;
  }
}

</style>