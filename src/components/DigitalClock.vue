<template>
  <div class="digitalClock">
    <div class="leftContainer">
      <div align="right">
        <div id="clock" class="zeit" >{{timeToDisplay}}</div>
        <div id="date">{{dateToDisplay}}</div>
        <div id="text">by Labion Abazi</div>
      </div>
    </div>
    <div class="middleContainer">
    </div>
    <div class="rightContainer">
      <div v-if="ditaRam" id="ramadan">{{ditaRam}} Ram. 2021</div>
      <table class="table">
        <tr>
          <td class="ram">Imsaku</td>
          <td class="zeit ram">{{imsaku}}</td>
        </tr>
        <tr>
          <td>Dreka</td>
          <td class="zeit">{{dreka}}</td>
        </tr>
        <tr>
          <td>Ikindija</td>
          <td class="zeit">{{ikindia}}</td>
        </tr>
        <tr>
          <td class="ram">Akshami</td>
          <td class="zeit ram">{{akshami}}</td>
        </tr>
        <tr>
          <td>Jacia</td>
          <td class="zeit">{{jacia}}</td>
        </tr>
      </table>
    </div>
  </div>
</template>

<script>
export default {
  name: 'DigitalClock',
  data(){
    return {
      titeltoDisplay: "Gjumin e embël",
      timeToDisplay: null,
      timeToCheck: null,
      dateToDisplay: null,
      shahada: 'لَا إِلَٰهَ إِلَّا ٱللَّٰهُ',
      imsaku: null,
      dreka: null,
      ikindia: null,
      akshami: null,
      jacia: null,
      ditaRam: null,
    }
  },
  created(){
    this.showDateTime()
    var dateSplitOne = this.dateToDisplay.split(" ")
    var dateSplitTwo = dateSplitOne[2].split(".")
    this.getVaktia(parseInt(dateSplitTwo[0]))

  },
  methods:{
    showDateTime(){
      var date = new Date()

      //get and format the time
      var h = date.getHours()   //This returns 0-23h
      var m = date.getMinutes() //This returns 0-59m
      var s = date.getSeconds()

      h = (h < 10) ? "0" + h : h;
      m = (m < 10) ? "0" + m : m;
      s = (s < 10) ? "0" + s : s;

      this.timeToDisplay = h + ":" + m
      this.timeToCheck = h + ":" + m + ":" + s

      //get and format the date
      var day = date.getDay()
      // var dayarray = ["e diel", "e hënë", "e marte", "e mërkurë", "e enjte", "e premte", "e shtunë", "e diel"];
      // day = dayarray[day];
      day = "e hënë"

      var dateNumber = date.getDate()
      // var dateNumber = 13
      
      var month = date.getMonth()
      var montharray = ["janar", "shkurt", "mars", "prill", "maj", "qershor", "korrik", "gusht", "shtator", "tetor", "nëntor", "dhjetor"];
      month = montharray[month];

      var year = date.getFullYear()

      //set title logic
      if (h >= 5) {
        this.titeltoDisplay = "Mirëmëngjes"
      } 
      if (h >= 10) {
        this.titeltoDisplay = "Mirëdita"
      } 
      if (h >= 18) {
        this.titeltoDisplay = "Mirëmbrëma"
      } 
      if (h >= 23) {
        this.titeltoDisplay = "Naten e mirë"
      } 

      this.dateToDisplay = day + ", " + dateNumber + ". " + month + " " + year;
      

      if (this.timeToCheck === "00:00:00") {
        this.getVaktia(dateNumber)
      }

      var drekaSound = this.dreka + ":00"
      var ikindiaSound = this.ikindia + ":00"
      var akshamiSound = this.akshami + ":00"
      var jaciaSound = this.jacia + ":00"

      if (this.timeToCheck === akshamiSound || this.timeToCheck === jaciaSound){
        console.log("Qazim")
        this.playSound()
      }

      if (this.timeToCheck === drekaSound || this.timeToCheck === ikindiaSound) {
        if (day === "e shtunë" || day === "e diel"){
        console.log("hans")
          this.playSound()
        }
      }

      setTimeout(this.showDateTime, 1000);
    },
    playSound() {
      var audio = new Audio(require('../assets/adhan.mp3'));
      audio.crossOrigin = 'anonymous';
      audio.play();
    },
    getVaktia(dateNumber) {
      switch (dateNumber) {
        case 1:
          this.imsaku = "04:21"
          this.dreka = "13:26"
          this.ikindia = "17:25"
          this.akshami = "20:46"
          this.jacia = "22:16"
          break
        case 2:
          this.imsaku = "04:20"
          this.dreka = "13:26"
          this.ikindia = "17:26"
          this.akshami = "20:48"
          this.jacia = "22:18"
          break
        case 3:
          this.imsaku = "04:18"
          this.dreka = "13:26"
          this.ikindia = "17:26"
          this.akshami = "20:49"
          this.jacia = "22:19"
          break
        case 4:
          this.imsaku = "04:17"
          this.dreka = "13:26"
          this.ikindia = "17:26"
          this.akshami = "20:50"
          this.jacia = "22:20"
          break
        case 5:
          this.imsaku = "04:15"
          this.dreka = "13:26"
          this.ikindia = "17:27"
          this.akshami = "20:52"
          this.jacia = "22:22"
          break
        case 6:
          this.imsaku = "04:14"
          this.dreka = "13:26"
          this.ikindia = "17:28"
          this.akshami = "20:53"
          this.jacia = "22:23"
          break
        case 7:
          this.imsaku = "04:12"
          this.dreka = "13:26"
          this.ikindia = "17:28"
          this.akshami = "20:54"
          this.jacia = "22:24"
          break
        case 8:
          this.imsaku = "04:11"
          this.dreka = "13:26"
          this.ikindia = "17:29"
          this.akshami = "20:56"
          this.jacia = "22:26"
          break
        case 9:
          this.imsaku = "04:09"
          this.dreka = "13:26"
          this.ikindia = "17:29"
          this.akshami = "20:57"
          this.jacia = "22:27"
          break
        case 10:
          this.imsaku = "04:08"
          this.dreka = "13:26"
          this.ikindia = "17:30"
          this.akshami = "20:58"
          this.jacia = "22:28"
          break
        case 11:
          this.imsaku = "04:07"
          this.dreka = "13:26"
          this.ikindia = "17:30"
          this.akshami = "21:00"
          this.jacia = "22:30"
          break
        //Bis hier ist schon Mai
        case 12:
          this.imsaku = "04:55"
          this.dreka = "13:30"
          this.ikindia = "17:15"
          this.akshami = "20:20"
          this.jacia = "21:50"
          break
        case 13:
          this.imsaku = "04:53"
          this.dreka = "13:30"
          this.ikindia = "17:16"
          this.akshami = "20:21"
          this.jacia = "21:51"
          this.ditaRam = "1"
          break
        case 14:
          this.imsaku = "04:51"
          this.dreka = "13:29"
          this.ikindia = "17:16"
          this.akshami = "20:23"
          this.jacia = "21:53"
          break
        case 15:
          this.imsaku = "04:49"
          this.dreka = "13:29"
          this.ikindia = "17:17"
          this.akshami = "20:24"
          this.jacia = "21:54"
          break
        case 16:
          this.imsaku = "04:48"
          this.dreka = "13:29"
          this.ikindia = "17:17"
          this.akshami = "20:25"
          this.jacia = "21:55"
          break
        case 17:
          this.imsaku = "04:46"
          this.dreka = "13:29"
          this.ikindia = "17:18"
          this.akshami = "20:27"
          this.jacia = "21:57"
          break
        case 18:
          this.imsaku = "04:44"
          this.dreka = "13:29"
          this.ikindia = "17:18"
          this.akshami = "20:28"
          this.jacia = "21:58"
          break
        case 19:
          this.imsaku = "04:42"
          this.dreka = "13:28"
          this.ikindia = "17:19"
          this.akshami = "20:30"
          this.jacia = "22:00"
          break
        case 20:
          this.imsaku = "04:40"
          this.dreka = "13:27"
          this.ikindia = "17:20"
          this.akshami = "20:31"
          this.jacia = "22:01"
          break
        case 21:
          this.imsaku = "04:38"
          this.dreka = "13:28"
          this.ikindia = "17:20"
          this.akshami = "20:32"
          this.jacia = "22:02"
          break
        case 22:
          this.imsaku = "04:37"
          this.dreka = "13:28"
          this.ikindia = "17:21"
          this.akshami = "20:34"
          this.jacia = "22:04"
          break
        case 23:
          this.imsaku = "04:35"
          this.dreka = "13:28"
          this.ikindia = "17:21"
          this.akshami = "20:35"
          this.jacia = "22:05"
          break
        case 24:
          this.imsaku = "04:33"
          this.dreka = "13:27"
          this.ikindia = "17:22"
          this.akshami = "20:37"
          this.jacia = "22:07"
          break
        case 25:
          this.imsaku = "04:31"
          this.dreka = "13:27"
          this.ikindia = "17:22"
          this.akshami = "20:38"
          this.jacia = "22:08"
          break
        case 26:
          this.imsaku = "04:30"
          this.dreka = "13:27"
          this.ikindia = "17:23"
          this.akshami = "20:39"
          this.jacia = "22:09"
          break
        case 27:
          this.imsaku = "04:28"
          this.dreka = "13:27"
          this.ikindia = "17:23"
          this.akshami = "20:41"
          this.jacia = "22:11"
          break
        case 28:
          this.imsaku = "04:26"
          this.dreka = "13:27"
          this.ikindia = "17:24"
          this.akshami = "20:42"
          this.jacia = "22:12"
          break
        case 29:
          this.imsaku = "04:25"
          this.dreka = "13:27"
          this.ikindia = "17:24"
          this.akshami = "20:43"
          this.jacia = "22:13"
          break
        case 30:
          this.imsaku = "04:23"
          this.dreka = "13:26"
          this.ikindia = "17:25"
          this.akshami = "20:45"
          this.jacia = "22:15"
          break
        // case 31:
        //   this.imsaku = "05:19"
        //   this.dreka = "13:33"
        //   this.ikindia = "17:07"
        //   this.akshami = "20:03"
        //   this.jacia = "21:33"
        //   break
      }
    },
  },
}
</script>

<style scoped>
  #titel{
    font-size: 120pt;
    margin: -20pt 0;
  }
  #clock{
    font-size: 150pt;
  }
  #date{
    font-size: 50pt;
  }
  #ramadan{
    font-size: 40pt;
  }
  #text{
    margin-top: 10px;
    font-size: 18pt;
  }
  .digitalClock{
    background-color: #8b864e;
    justify-content: center;
    align-items: center;
    display: flex;
    width: 100%;
    height: 400px;
  }
  .leftContainer{
    margin-right: 20px;
  }
  .middleContainer{
    height: 90%;
    width: 3px;
    background-color: #000000;
  }
  .rightContainer{
    margin-left: 20px;
  }
  .table{
    font-size: 35pt;
    font-weight: 500;
  }
  .zeit{
    font-family: 'Dosis', sans-serif;
    font-family: 'Exo', sans-serif;
    font-family: 'Geo', sans-serif;
    font-family: 'Orbitron', sans-serif;
  }
</style>