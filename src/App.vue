<script>
export default {
  data () {
    return { 
    dinheiro: 0,
      
    mGlQt: 1,
    mGlPr: 5,
      
    mD1Qt: 1,
    mD1Va: 0.5,
    mD1Pr: 2,
    D1: 0.5,
    //TD1: 1,
    //CD1: 0,
      
    mD2Qt: 0,
    mD2Va: 2.5,
    mD2Pr: 5,
    D2: 0,
    //TD2: 0,
    //CD2: 0,
    }
  },

  methods: {
    
    ComprarUpgradeG() {
        if (this.dinheiro >= this.mGlPr){
        this.dinheiro -= this.mGlPr;
        this.mGlPr *= 2;
        this.mGlQt++;
      }
    },
    
    FazerDinheiro1() {
        //if(this.CD1 == 0){  
        this.dinheiro += this.mGlQt * this.mD1Qt * this.mD1Va;
        //}
    }, //fechar FazerDinheiro1
    
    ComprarUpgrade1() {
      if (this.dinheiro >= this.mD1Pr){
        this.dinheiro -= this.mD1Pr;
        this.mD1Pr *= 1.33;
        this.mD1Qt++;
        this.D1 = this.mD1Qt * this.mD1Va;
      }
    }, //fechar ComprarUpgrade1
    
        FazerDinheiro2() {
        this.dinheiro += this.mGlQt * this.mD2Qt * this.mD2Va;
    }, //fechar FazerDinheiro2
    
        ComprarUpgrade2() {
      if (this.dinheiro >= this.mD2Pr){
        this.dinheiro -= this.mD2Pr;
        this.mD2Pr *= 1.5;
        this.mD2Qt++;
        this.D2 = this.mD2Qt * this.mD2Va;
      }
    }, //fechar ComprarUpgrade2
    
  } //fechar methods
}


</script>

<template>
  <body>
    <div id="app">
      <br>
      <br>
      <br>
      <div class="cssdinheiro"><input type="text" v-model="dinheiro">
      $ {{dinheiro.toFixed(2)}}</div><br>
      
      <div class="boxouterG">
      <button type="button" @click="ComprarUpgradeG" class="btn btn-dark">Comprar gatos melhores ($ {{mGlPr.toFixed(2)}})</button>
      <br>
      Seus gatos tem {{mGlQt.toFixed(0)}} niveis de upgrade!
      </div> <br> <br> <br>
  
      <div class="boxouter">  
        <div class="boxinner">
            <div class="boxobj">
              <button type="button" @click="FazerDinheiro1" class="btn btn-primary">🐱 ({{(D1).toFixed(2)}})</button>
            </div>
            <div class="boxobj">
              <button type="button" @click="ComprarUpgrade1" class="btn btn-secondary">Comprar 🐱 ($ {{mD1Pr.toFixed(2)}})</button>
            </div>
          </div>

          <div class="boxinner">
            <div class="boxobj">
              <button type="button" @click="FazerDinheiro2" class="btn btn-primary">🐈 ({{(D2).toFixed(2)}})</button>
            </div>
            <div class="boxobj">
              <button type="button" @click="ComprarUpgrade2" class="btn btn-secondary">Comprar 🐈 ($ {{mD2Pr.toFixed(2)}})</button>
            </div>
        </div>
      </div>
    </div>
  </body>
</template>

<style scoped>
* {
  font-family: Comic Sans MS
}

.cssdinheiro {
  height:10%;
  width:300px;
  padding:3px;
  margin: auto;
}

.boxouterG {
  height: 10%;
  width: 50%;
  padding: 3px;
  margin: auto;
  border: 2px solid black;
  background-color: #00004d88;
  overflow: hidden;
  text-align:center;
}

.boxouter {
  height: 10%;
  width: 50%;
  padding: 3px;
  margin: auto;
  border: 2px solid black;
  background-color: #00004d88;
  overflow: hidden;
  display: grid;
  grid-template-columns: 1fr 1fr;
}

.boxinner {
  padding: 20px;
  margin: 15px;
  border: 1px solid black;
  background-color: teal;
  overflow: hidden;
  display: inline-block;
}

.boxobj {
  height: 50%;
  width: 100%;
  margin: auto;
  text-align: center;
}
</style>
