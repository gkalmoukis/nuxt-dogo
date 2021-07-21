<template>
<div class="mt-3 content">

    <div class="d-flex justify-content-center">

      <b-form @reset="onReset" @submit="onSubmit">
                
        <input 
          type="number"
          step="1" 
          v-model="kg" 
          class="question" 
          id="input-kg" 
          required 
          autocomplete="off" />
        <label for="input-kg">
          <span>Βάρος του σκύλου σας (kg)</span>
        </label>

        <input 
          type="number"
          step="0.1" 
          v-model="percentange" 
          class="question" 
          id="input-percentange" 
          required 
          autocomplete="off" />
        <label for="input-percentange">
          <span>Ποσοστό σωματικού βάρους (%)</span>
        </label>
        
        
        <button type="submit" class="fill">Υπολογισμός</button>
        <button type="reset" class="fill">Απο την αρχή</button>
      </b-form>
    </div>

    <div class="d-flex justify-content-center" v-if="show">
      <div class="mt-3 mb-2 result-container" >
        <div class="row">{{result}} g ανα ημέρα</div>
      </div>
    </div>
</div>
</template>

<script>
  export default {
    layout: 'app',
     data() {
      return {
        kg: 32,
        percentange : 2.5 ,
        result : "",
        show: false
      }
    },
    methods: {
      onSubmit(event){
        event.preventDefault()
        this.show = true
        this.result =  ( this.kg * (this.percentange/100) ) * 10 * 10 * 10
      },
      onReset(event) {
        event.preventDefault()
        this.kg = 32;
        this.show = false;
        this.percentange = 2.5;
        this.result = "";
      }
    }
  }
</script>

<style>
.result-container {
  --color : #ffe54c;
  font-size: 2rem;
  color: var(--color);
  padding-top: 1rem;
}


button {
  margin: 50px;
  font-family: inherit;
}

/* Fill button styling */
.fill {
  font-size: 20px;
  font-weight: 200;
  letter-spacing: 1px;
  padding: 13px 50px 13px;
  outline: 0;
  border: 1px solid black;
  cursor: pointer;
  position: relative;
  background-color: rgba(0, 0, 0, 0);
}

.fill::after {
  content: "";
  background-color: #ffe54c;
  width: 100%;
  z-index: -1;
  position: absolute;
  height: 100%;
  top: 7px;
  left: 7px;
  transition: 0.2s;
}

.fill:hover::after {
  top: 0px;
  left: 0px;
}
/* End of Fill Button  */


input,
span,
label {
  font-family: inherit;
  display: block;
  margin: 10px;
  padding: 5px;
  border: none;
  font-size: 22px;
}

input:focus {
  outline: 0;
}
/* Question */

input.question {
  font-size: 48px;
  font-weight: 300;
  border-radius: 2px;
  margin: 0;
  border: none;
  width: 100%;
  background: rgba(0, 0, 0, 0);
  transition: padding-top 0.2s ease, margin-top 0.2s ease;
  overflow-x: hidden; /* Hack to make "rows" attribute apply in Firefox. */
}
/* Underline and Placeholder */

input.question + label {
  display: block;
  position: relative;
  white-space: nowrap;
  padding: 1;
  margin: 0;
  width: 25%;
  border-top: 1px solid #ffe54c;
  -webkit-transition: width 0.4s ease;
  transition: width 0.4s ease;
  height: 0px;
}

input.question:focus + label {
  width: 100%;
}

input.question:focus,
input.question:valid {
  padding-top: 35px;
}

input.question:focus + label > span,
input.question:valid + label > span {
  top: -100px;
  font-size: 22px;
  color: #333;
}

input.question:valid + label {
  border-color: #ffe54c;
}

input.question:invalid {
  box-shadow: none;
}

input.question + label > span {
  font-weight: 300;
  margin: 0;
  position: absolute;
  color: #8F8F8F;
  font-size: 48px;
  top: -66px;
  left: 0px;
  z-index: -1;
  -webkit-transition: top 0.2s ease, font-size 0.2s ease, color 0.2s ease;
  transition: top 0.2s ease, font-size 0.2s ease, color 0.2s ease;
}

@-webkit-keyframes appear {
  100% {
    opacity: 1;
  }
}

@keyframes appear {
  100% {
    opacity: 1;
  }
}

</style>