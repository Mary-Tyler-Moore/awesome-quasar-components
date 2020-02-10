<template>
<div id="app">
  <div class="container">
    <article>
      <header>
        <div class="progress">
          <div class="progress-step"
               :class="{'active': index === activeStep}"
               v-for="(step, index) in formSteps"
               :key="'step'+index">
            {{ index + 1 }}
          </div>
        </div>
      </header>
      <section :class="animation">
        <h2>{{ formSteps[activeStep].title }}</h2>
        <div class="input-fields">
          <div class="input-container"
               v-for="(field, index) in formSteps[activeStep].fields" :key="'field'+index">
            <input type="text" :class="{'wrong-input': !field.valid}" v-model="field.value" required />
            <label class="input-label">{{ field.label }}</label>
          </div>
        </div>
        <div class="actions">
          <button v-if="activeStep + 1 < formSteps.length -1" @click="checkFields">next</button>
          <button v-if="activeStep + 1 === formSteps.length -1" @click="checkFields">done</button>
        </div>
      </section>
    </article>
  </div>
  </div>
</template>

<script>
  export default {
	name: "stepper",
    data() {
    return {
        activeStep: 0,
    animation: 'animate-in',
    formSteps: [
      {
        title: '"Interests" Quiz',
        fields: [
          { label: "What the things you like more?", value: '', valid: true, pattern: /.+/ },
          { label: "Which the language you like more?", value: '', valid: true, pattern: /.+/ },
          { label: "Do you like programming?", value: '', valid: true, pattern: /.+/ }
        ]
      },
      {
        title: '"Dwelling" Quiz',
        fields: [
          { label: "Where is the most beautiful for you?", value: '', valid: true, pattern: /.+/ },
          { label: "Where do you live?", value: '', valid: true, pattern: /.+/ },
          { label: "Does your home is as you think?", value: '', valid: true, pattern: /.+/ }
        ]
      },
      {
        title: "Your data",
        fields: [
          { label: "Your first name?", value: '', valid: true, pattern: /.+/ },
          { label: "Your last name?", value: '', valid: true, pattern: /.+/ },
          { label: "Your email?", value: '', valid: true, pattern: /^[^\s@]+@[^\s@]+\.[^\s@]+$/ }
        ]
      },
      {
        title: "Thank you for your responses!",
      }
    ],
    }
  },
  methods: {
    nextStep() {
      this.animation = 'animate-out';
      setTimeout(() => {
        this.animation = 'animate-in';
        this.activeStep += 1;
      }, 600);
    },
    checkFields() {
      let valid = true;
      this.formSteps[this.activeStep].fields.forEach(field => {
        if (!field.pattern.test(field.value)) {
          valid = false;
          field.valid = false;
        }
        else {
          field.valid = true;
        }
      });

      if(valid) {
        this.nextStep();
      }
      else {
        this.animation = 'animate-wrong';
        setTimeout(() => {
          this.animation = '';
        }, 400);
      }
    }
  }
  }
</script>

<style scoped>
/* These styles were firstly created with scss,
but for many request of users converted into general CSS*/
body {
	 margin: 0;
	 padding: 0;
}
 #app {
	 width: 100%;
	 height: 100vh;
	 overflow: hidden;
}
 .container {
	 display: flex;
	 justify-content: center;
	 align-items: center;
	 width: 100%;
	 min-height: 100vh;
	 font-family: 'Noto Sans', sans-serif;
	 background: radial-gradient(#2e95df, #8527a4);
}
 article {
	 display: flex;
	 flex-direction: column;
	 margin: 10px;
	 width: calc(100% - 20px);
	 max-width: 720px;
	 min-height: 480px;
	 perspective: 1000px;
}
 article header {
	 display: flex;
	 justify-content: center;
	 align-items: center;
	 width: 100%;
	 height: 60px;
	 background-color: #fff;
	 border-bottom: 2px dotted #b90202;
	 box-shadow: 0 15px 30px rgba(0, 0, 0, 0.2), 0 10px 10px rgba(0, 0, 0, 0.2);
}
 article .progress {
	 display: flex;
	 justify-content: center;
	 align-items: center;
}
 article .progress-step {
	 display: flex;
	 justify-content: center;
	 align-items: center;
	 position: relative;
	 width: 30px;
	 height: 30px;
	 border-radius: 50%;
	 margin: 0 10px;
	 color: #fff;
	 background-color: #b90202;
	 font-weight: bold;
}
 article .progress-step.active {
	 background-color: #b90202#b90202
     ;
}
 article .progress-step.active ~ .progress-step {
	 color: #555;
	 background-color: #ccc;
}
 article .progress-step.active ~ .progress-step::before {
	 background-color: #ccc;
}
 article .progress-step:before {
	 content: '';
	 position: absolute;
	 left: -20px;
	 width: 20px;
	 height: 2px;
	 background: #b90202;
	 z-index: 10;
}
 article .progress-step:first-child::before {
	 display: none;
}
 article section {
	 display: flex;
	 justify-content: center;
	 align-items: center;
	 flex-direction: column;
	 width: 100%;
	 background-color: #fff;
	 box-shadow: 0 15px 30px rgba(0, 0, 0, 0.2), 0 10px 10px rgba(0, 0, 0, 0.2);
}
 article section h2 {
	 font-size: 1.6rem;
	 color: #b90202;
	 margin: 0;
	 padding: 20px;
}
 article section .input-fields {
	 display: flex;
	 justify-content: center;
	 align-items: center;
	 flex-direction: column;
	 width: 100%;
}
 article section .input-container {
	 position: relative;
	 padding: 30px 20px 20px 20px;
	 width: calc(100% - 40px);
	 max-width: 400px;
}
 article section .input-container input {
	 position: relative;
	 width: 100%;
	 font-family: 'Noto Sans', sans-serif;
	 font-size: 1.35rem;
	 outline: 0;
	 background: transparent;
	 box-shadow: none;
	 border: none;
	 border-bottom: 2px dashed #b90202;
}
 article section .input-container input:valid + .input-label {
	 top: 10px;
	 left: 20px;
	 font-size: 0.7rem;
	 font-weight: normal;
	 color: #999;
}
 article section .input-container input.wrong-input + .input-label {
	 color: #b92938;
}
 article section .input-label {
	 position: absolute;
	 top: 32px;
	 left: 20px;
	 font-size: 1.35rem;
	 pointer-events: none;
	 transition: 0.2s ease-in-out;
}
 article section .actions {
	 margin: 30px 0 30px 0;
}
 article section .actions button {
	 font-family: 'Noto Sans', sans-serif;
	 outline: none;
	 border: none;
	 color: #fff;
	 background-color: #b90202;
	 font-size: 1.35rem;
	 padding: 5px 20px;
	 margin: 0 10px;
	 text-transform: uppercase;
	 border-radius: 3px;
	 cursor: pointer;
}
 .animate-out {
	 transform-origin: bottom left;
	 animation: out 0.6s ease-in-out;
}
 .animate-in {
	 transform-origin: top;
	 animation: in 0.6s ease-in-out;
}
 .animate-wrong {
	 animation: wrong 0.4s ease-in-out;
}
 @keyframes out {
	 0% {
		 transform: translateY(0px) rotate(0deg);
	}
	 60% {
		 transform: rotate(10deg);
	}
	 100% {
		 transform: translateY(1000px);
	}
}
 @keyframes in {
	 0% {
		 opacity: 0;
		 transform: rotateX(-90deg);
	}
	 100% {
		 opacity: 1;
		 transform: rotateX(0deg);
	}
}
 @keyframes wrong {
	 0% {
		 transform: translateX(0);
	}
	 20% {
		 transform: translateX(40px);
	}
	 40% {
		 transform: translateX(20px);
	}
	 60% {
		 transform: translateX(40px);
	}
	 80% {
		 transform: translateX(20px);
	}
	 100% {
		 transform: translateX(0);
	}
}
</style>
