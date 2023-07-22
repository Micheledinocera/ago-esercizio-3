<script>
export default {
  data() {
    return {
      array: [], 
      pirata: "",
      indice: 0
    }
  },

  methods: {
    aggiungiVettore() {
      this.array.push(this.pirata);
      this.pirata="";
    },
    cancellaPirata() {
      this.array.splice(this.indice, 1);
  },
  },
  computed: {
    numeroMassimo () {
      if (this.arrayMaggioreTre) return "add-button"
      else return "add-button-red"
    },
    arrayMaggioreTre () {
      return this.array.length<3
    },
    arrayPieno () {
      return this.array.length!=0
    },
    arrayMaiuscolo() { 
      const arrayMaiuscolo = this.array.map(function(pirata) {
         return pirata.toUpperCase();
      });
      return arrayMaiuscolo;
  } 
    /* 
    FUNZIONE FRECCIA (equivalente)
    arrayMaiuscolo() { 
      return this.array.map(pirata => pirata.toUpperCase());
    } 
    */ 
 },
}
</script>

<template>
  <body>
    <header>
        <h1>⚓Arrembaggio: crea la tua ciurma!⚓</h1>
    </header>
    <div class="main-container">
        <h2>Prendi nota dei componenti del tuo equipaggio.</h2>
        <div class="nomi">
            <input type="text" v-model="pirata" placeholder="Inserisci nome membro dell'equipaggio">
            <button class="add-button" @click="aggiungiVettore" :class="numeroMassimo">Aggiungi</button>
            <select v-model="indice" v-if="arrayPieno">
                <option v-for="(pirata, index) in array" :value="index" :key="index">{{pirata}}</option>
            </select>
            <button class="delete-button" v-if="arrayPieno" @click="cancellaPirata">Cancella</button>
        </div>
        <div class="crew-list">
            <h3>Membri dell'equipaggio:</h3>
            <div class="crew-list-item" v-for="pirata in arrayMaiuscolo">{{pirata}}</div>
        </div>
    </div>
    <div class="contenitore-sass">
      <div class="test">
        <div class="sotto-classe sotto-classe-1">test1</div>
      </div>
      <div class="test">
        <div class="sotto-classe sotto-classe-2">test2</div>
      </div>
    </div>
    <footer>
        <p><a href="https://it.freepik.com/vettori-gratuito/nave-pirata-o-galeone-con-teschio-umano-e-ossa-incrociate-su-vele-nere_4393923.htm#query=disegno%20pirati%20notte&position=0&from_view=search&track=ais">Immagine di vectorpouch</a> su Freepik</p>
    </footer>
  </body>
</template>

<style scoped lang="scss">
body {
  background-image: url('sfondo.jpg');
  background-size: cover;
  margin: 0;
  padding: 0;
  font-family: 'Arial', sans-serif;
}
header, footer {
  background-color: #111;
  color: #fff;
  text-align: center;
  padding: 10px;
  border-radius: 10%;
  margin: 0px auto;
}
.main-container {
  position: relative;
  background-color: rgba(0, 0, 0, 0.7);
  border-radius: 20px;
  padding: 20px;
  max-width: 800px;
  margin: 0px auto;
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: center;
}
.nomi {
  display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: center;
}
h1, h2, h3, p {
  font-family: 'Pirata One', cursive;
  text-align: center;
  color: #eedd82;
}
h1 {
  font-size: 28px;
}
h2 {
  font-size: 36px;
}
input[type="text"], select {
  font-family: 'Pirata One', cursive;
  font-size: 24px;
  padding: 10px;
  margin-bottom: 10px;
  border: none;
  border-radius: 5px;
}
input[type="text"] {
  width: 90%;
}
select {
  width: 00%;
}
.add-button {
  font-family: 'Pirata One', cursive;
  font-size: 28px;
  background-color: #22724d;
  color: #fff;
  border: none;
  border-radius: 5px;
  padding: 10px 20px;
  cursor: pointer;
}

.add-button-red {
  font-family: 'Pirata One', cursive;
  font-size: 28px;
  background-color: #7d0b0b;
  color: #fff;
  border: none;
  border-radius: 5px;
  padding: 10px 20px;
  cursor: pointer;
}
.delete-button {
  font-family: 'Pirata One', cursive;
  font-size: 28px;
  background-color: #224c72;
  color: #fff;
  border: none;
  border-radius: 5px;
  padding: 10px 20px;
  cursor: pointer;
}
.add-button:hover, .delete-button:hover {
  background-color: #798f0c;
}
.crew-list {
  font-family: 'Pirata One', cursive;
  font-size: 28px;
  margin-top: 20px;
  color: whitesmoke;
  display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: center;
}
.crew-list-item {
  margin-bottom: 5px;
}
.contenitore-sass {
  background-color: black;
  width: 100%;
  height: 50px;
  display: flex;
  .test{
    margin: auto;
    width: 100px;
    .sotto-classe{
      font-size: 20px;
      &.sotto-classe-1{ color:red; }
      &.sotto-classe-2{ color:green; }
    }
  }
}
</style>

