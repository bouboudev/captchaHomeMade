<template>
  <div>
    <h1>{{ msg }}</h1>
                
    <div class="tableau">
      <table v-if="!finish">
          <thead>
            <tr>
              <th :colspan="wordArray.length">
              Choose the right icon : <span class="icon" style=" font-size: 30px">{{getIconRandom}}</span>
              </th>
            </tr>
            <tr>
              <th :colspan="wordArray.length">
              <span>You have <span style="color: #42b983" > {{ compteur}} </span>chances.</span>
              </th>
            </tr>
          </thead>
          <tbody>
            <tr>
              <td v-for="word in wordArray" :key="word">
            

              <div @click="checkCaptcha(word)" class="hover">
                <mdicon class="icon" :name="word" size="64"/>
              </div>
  
              </td>
            </tr>
          </tbody>
      </table>
      <div v-else>
        <button class="button-3" role="button" @click="reset()">Reset</button>

      </div>

  </div>
      <div>
        <h1 v-if="captchaGood" :style="isColor">Captcha Good 😃</h1>
        <h1 v-if="captchaBad" :style="isColor">Captcha not Good 😡</h1>
      </div>
    
  </div>
</template>

<script>
export default {
  name: 'CaptchaHomeMade',
  props: {
    msg: String
  },
  data () {
    return {
      word:'',
      wordArray:['dog','cat','bird','fish','horse','cow','pig','sheep',],
      captchaGood:false,
      captchaBad:false,
      compteur:3,
      finish:false,
    }
  },
methods:{
    checkCaptcha(word){
      
      if(word === this.getIconRandom){
        this.compteur = 3;
        this.captchaGood = true;
        this.captchaBad = false;
        this.finish = true;
      }else{
        this.wordArray.splice(this.wordArray.indexOf(word),1);
        this.incCompteur();
        this.captchaGood = false;
        this.captchaBad = true;
        if(this.compteur === 0){
          this.finish = true;
        }
      }
    },
  incCompteur(){
    this.compteur--;
  },
  reset(){
    this.wordArray=['dog','cat','bird','fish','horse','cow','pig','sheep',];
    this.captchaGood = false;
    this.compteur = 3;
    this.finish = false;
    this.shuffle();
  },
  shuffle(){
    return this.wordArray.sort(() => Math.random() - 0.5);
  },
},
computed:{
  getNumberRandom(){
      return Math.floor(Math.random() * this.wordArray.length);
    },
    getIconRandom(){
      return this.wordArray[this.getNumberRandom];
    },
     isColor(){
      if(this.captchaGood){
        return 'color : #42b983';
      }
        return 'color : red';
    },
},
mounted(){
  this.shuffle();
},
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h3 {
  margin: 40px 0 0;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}

table {
color: gray;
border-collapse: collapse;
}
td,th {
text-align: left;
border: 1px solid black;
padding: 10px;
}
.tableau {
  display: flex;
  justify-content: center;
  align-items: center;
  
}
.icon {
 color: #42b983;
}
.hover :hover{
  cursor: pointer;
  background: #dcdcdc;
}

/* CSS */
.button-3 {
  appearance: none;
  background-color: #42b983;
  border: 1px solid rgba(27, 31, 35, .15);
  border-radius: 6px;
  box-shadow: rgba(27, 31, 35, .1) 0 1px 0;
  box-sizing: border-box;
  color: #fff;
  cursor: pointer;
  display: inline-block;
  font-family: -apple-system,system-ui,"Segoe UI",Helvetica,Arial,sans-serif,"Apple Color Emoji","Segoe UI Emoji";
  font-size: 14px;
  font-weight: 600;
  line-height: 20px;
  padding: 6px 16px;
  position: relative;
  text-align: center;
  text-decoration: none;
  user-select: none;
  -webkit-user-select: none;
  touch-action: manipulation;
  vertical-align: middle;
  white-space: nowrap;
}

.button-3:focus:not(:focus-visible):not(.focus-visible) {
  box-shadow: none;
  outline: none;
}

.button-3:hover {
  background-color: #399f71;
}

.button-3:focus {
  box-shadow: rgba(46, 164, 79, .4) 0 0 0 3px;
  outline: none;
}


.button-3:active {
  background-color: #42b983;
  box-shadow: rgba(20, 70, 32, .2) 0 1px 0 inset;
}
</style>