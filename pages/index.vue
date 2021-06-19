<template> 
  <div class="ppi">
    <div class="ppi__container">
      <div class="ppi__calc-box">
        <div class="ppi__calc-title-box">
          <div class="ppi__calc-title">PPI Calculator</div>
        </div>
        <div class="ppi__calc">
          <div class="ppi__input-box">
            <input type="number" class="ppi__input ppi__input--wp" placeholder="resolution width in pixels" v-model="wp">
            <input type="number" class="ppi__input ppi__input--hp" placeholder="resolution height in pixels" v-model="hp">
            <input type="number" class="ppi__input ppi__input--di" placeholder="diagonal size in inches" v-model="di">
          </div>
          <div class="ppi__answer-box" v-show="answer !== 'NaN'">{{ answer }} ppi</div>
        </div>
      </div>
      <a class="link" href="https://github.com/MertvyeDushi/" target="_blank">designed by mark</a>
    </div>
  </div>
</template>

<script>
export default {
  name: 'PPICalculator',
  computed: {
    answer() {
      return (Math.sqrt( Math.pow(this.wp, 2) + Math.pow(this.hp, 2) ) / this.di).toFixed(2) || 0
    }
  },
  data() {
    return {
      wp: '',
      hp: '',
      di: ''
    }
  },
}
</script>

<style>
.ppi {
  background: #c6cde1;
}


.ppi__container {
  margin: 0 auto;
  min-height: 100vh;
  display: flex;
  justify-content: center;
  align-items: center;
  text-align: center;

  position: relative;
}


.ppi__calc-title, .ppi__answer-box, input, .link {
  font-family:
    'Quicksand',
    'Source Sans Pro',
    -apple-system,
    BlinkMacSystemFont,
    'Segoe UI',
    Roboto,
    'Helvetica Neue',
    Arial,
    sans-serif;
  display: block;
  font-weight: 300;
  font-size: 100px;
  color: #35495e;
  letter-spacing: 1px;
  line-height: 1;
}


.link {
  font-size: 14px;
  text-decoration: none;

  position: absolute;
  bottom: 20px;
}


.ppi__calc-title-box {
  width: 100%;
  text-align: center;
  margin-bottom: 40px;
}


.ppi__calc-box, .ppi__input-box, .ppi__calc {
  display: flex;  
  align-items: center;
}


.ppi__calc-box {
  flex-direction: column;
  align-items: flex-start;
  justify-content: flex-start;

  padding: 50px 60px 60px;

  border-radius: 50px;
  background: #c6cde1;
  box-shadow:  20px 20px 60px #a8aebf,
              -20px -20px 60px #e4ecff;
}


.ppi__calc {
  width: 100%;
  flex-direction: row;
  justify-content: space-between;
}


.ppi__input-box {
  justify-content: space-between;
  flex-direction: column;

  margin-right: 20px;
}


.ppi__input {
  border: 2px solid #35495e;
  border-radius: 5px;

  background: #d6dbeb;

  font-size: 18px;

  min-height: 40px;
  min-width: 270px;

  width: 100%;
  padding: 10px 15px;
}


.ppi__input:not(:last-child) {
  margin-bottom: 20px;
}
</style>
