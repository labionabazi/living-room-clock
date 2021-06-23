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
      <!-- <div v-if="ditaRam" id="ramadan">{{ditaRam}} Ram. 2021</div> -->
      <table class="table">
        <tr>
          <td class="ram">Imsaku</td>
          <td class="zeit ram">{{imsaku}}</td>
        </tr>
        <tr>
          <td class="ram">Dreka</td>
          <td class="zeit ram">{{dreka}}</td>
        </tr>
        <tr>
          <td class="ram">Ikindija</td>
          <td class="zeit ram">{{ikindia}}</td>
        </tr>
        <tr>
          <td class="ram">Akshami</td>
          <td class="zeit ram">{{akshami}}</td>
        </tr>
        <tr>
          <td class="ram">Jacia</td>
          <td class="zeit ram">{{jacia}}</td>
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
      var dayarray = ["e diel", "e hënë", "e marte", "e mërkurë", "e enjte", "e premte", "e shtunë", "e diel"];
      day = dayarray[day];

      var dateNumber = date.getDate()
      
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

      if (this.timeToCheck === akshamiSound){
        this.playSound()
      }

      if (this.timeToCheck === drekaSound || this.timeToCheck === ikindiaSound || this.timeToCheck === jaciaSound) {
        if (day === "e shtunë" || day === "e diel"){
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
          this.imsaku = "03:46"
          this.dreka = "13:27"
          this.ikindia = "17:39"
          this.akshami = "21:23"
          this.jacia = "23:36"
          // this.ditaRam = "19"
          break
        case 2:
          this.imsaku = "03:45"
          this.dreka = "13:27"
          this.ikindia = "17:40"
          this.akshami = "21:24"
          this.jacia = "22:54"
          // this.ditaRam = "20"
          break
        case 3:
          this.imsaku = "03:44"
          this.dreka = "13:28"
          this.ikindia = "17:40"
          this.akshami = "21:25"
          this.jacia = "22:55"
          // this.ditaRam = "21"
          break
        case 4:
          this.imsaku = "03:44"
          this.dreka = "13:28"
          this.ikindia = "17:40"
          this.akshami = "21:26"
          this.jacia = "22:56"
          // this.ditaRam = "22"
          break
        case 5:
          this.imsaku = "03:43"
          this.dreka = "13:28"
          this.ikindia = "17:41"
          this.akshami = "21:27"
          this.jacia = "22:57"
          // this.ditaRam = "23"
          break
        case 6:
          this.imsaku = "03:43"
          this.dreka = "13:28"
          this.ikindia = "17:41"
          this.akshami = "21:28"
          this.jacia = "22:58"
          // this.ditaRam = "24"
          break
        case 7:
          this.imsaku = "03:43"
          this.dreka = "13:28"
          this.ikindia = "17:41"
          this.akshami = "21:28"
          this.jacia = "22:58"
          // this.ditaRam = "25"
          break
        case 8:
          this.imsaku = "03:42"
          this.dreka = "13:28"
          this.ikindia = "17:42"
          this.akshami = "21:29"
          this.jacia = "22:59"
          // this.ditaRam = "26"
          break
        case 9:
          this.imsaku = "03:42"
          this.dreka = "13:29"
          this.ikindia = "17:42"
          this.akshami = "21:30"
          this.jacia = "23:00"
          // this.ditaRam = "27"
          break
        case 10:
          this.imsaku = "03:42"
          this.dreka = "13:29"
          this.ikindia = "17:42"
          this.akshami = "21:30"
          this.jacia = "23:00"
          // this.ditaRam = "28"
          break
        case 11:
          this.imsaku = "03:41"
          this.dreka = "13:29"
          this.ikindia = "17:43"
          this.akshami = "21:31"
          this.jacia = "23:01"
          // this.ditaRam = "29"
          break
        case 12:
          this.imsaku = "03:41"
          this.dreka = "13:29"
          this.ikindia = "17:43"
          this.akshami = "21:31"
          this.jacia = "23:01"
          break
        case 13:
          this.imsaku = "03:41"
          this.dreka = "13:29"
          this.ikindia = "17:43"
          this.akshami = "21:32"
          this.jacia = "23:02"
          // this.ditaRam = "1"
          break
        case 14:
          this.imsaku = "03:41"
          this.dreka = "13:30"
          this.ikindia = "17:44"
          this.akshami = "21:32"
          this.jacia = "23:02"
          // this.ditaRam = "2"
          break
        case 15:
          this.imsaku = "03:41"
          this.dreka = "13:30"
          this.ikindia = "17:44"
          this.akshami = "21:33"
          this.jacia = "23:03"
          // this.ditaRam = "3"
          break
        case 16:
          this.imsaku = "03:41"
          this.dreka = "13:30"
          this.ikindia = "17:44"
          this.akshami = "21:33"
          this.jacia = "23:03"
          // this.ditaRam = "4"
          break
        case 17:
          this.imsaku = "03:41"
          this.dreka = "13:30"
          this.ikindia = "17:44"
          this.akshami = "21:34"
          this.jacia = "23:04"
          // this.ditaRam = "5"
          break
        case 18:
          this.imsaku = "03:41"
          this.dreka = "13:30"
          this.ikindia = "17:45"
          this.akshami = "21:34"
          this.jacia = "23:04"
          // this.ditaRam = "6"
          break
        case 19:
          this.imsaku = "03:41"
          this.dreka = "13:31"
          this.ikindia = "17:45"
          this.akshami = "21:34"
          this.jacia = "23:04"
          // this.ditaRam = "7"
          break
        case 20:
          this.imsaku = "03:41"
          this.dreka = "13:31"
          this.ikindia = "17:45"
          this.akshami = "21:35"
          this.jacia = "23:05"
          // this.ditaRam = "8"
          break
        case 21:
          this.imsaku = "03:42"
          this.dreka = "13:31"
          this.ikindia = "17:45"
          this.akshami = "21:35"
          this.jacia = "23:05"
          // this.ditaRam = "9"
          break
        case 22:
          this.imsaku = "03:42"
          this.dreka = "13:31"
          this.ikindia = "17:46"
          this.akshami = "21:35"
          this.jacia = "23:05"
          // this.ditaRam = "10"
          break
        case 23:
          this.imsaku = "03:42"
          this.dreka = "13:32"
          this.ikindia = "17:46"
          this.akshami = "21:35"
          this.jacia = "23:05"
          // this.ditaRam = "11"
          break
        case 24:
          this.imsaku = "03:42"
          this.dreka = "13:32"
          this.ikindia = "17:46"
          this.akshami = "21:35"
          this.jacia = "23:05"
          // this.ditaRam = "12"
          break
        // Bis hier ist schon April
        case 25:
          this.imsaku = "03:51"
          this.dreka = "13:26"
          this.ikindia = "17:36"
          this.akshami = "21:16"
          this.jacia = "22:46"
          // this.ditaRam = "13"
          break
        case 26:
          this.imsaku = "03:50"
          this.dreka = "13:26"
          this.ikindia = "17:37"
          this.akshami = "21:17"
          this.jacia = "22:47"
          // this.ditaRam = "14"
          break
        case 27:
          this.imsaku = "03:49"
          this.dreka = "13:27"
          this.ikindia = "17:37"
          this.akshami = "21:19"
          this.jacia = "22:49"
          // this.ditaRam = "15"
          break
        case 28:
          this.imsaku = "03:48"
          this.dreka = "13:27"
          this.ikindia = "17:38"
          this.akshami = "21:20"
          this.jacia = "22:50"
          // this.ditaRam = "16"
          break
        case 29:
          this.imsaku = "03:48"
          this.dreka = "13:27"
          this.ikindia = "17:38"
          this.akshami = "21:21"
          this.jacia = "22:51"
          // this.ditaRam = "17"
          break
        case 30:
          this.imsaku = "03:47"
          this.dreka = "13:27"
          this.ikindia = "17:38"
          this.akshami = "21:22"
          this.jacia = "22:52"
          // this.ditaRam = "18"
          break
        case 31:
          this.imsaku = "03:46"
          this.dreka = "13:27"
          this.ikindia = "17:39"
          this.akshami = "21:22"
          this.jacia = "22:52"
          break
      }
    },
  },
}
</script>

<style scoped>
  #titel{
    font-size: 125pt;
    margin: -20pt 0;
  }
  #clock{
    font-size: 155pt;
  }
  #date{
    font-size: 55pt;
  }
  #ramadan{
    font-size: 45pt;
    font-weight: 600;
  }
  #text{
    margin-top: 10px;
    font-size: 18pt;
  }
  .digitalClock{
    justify-content: center;
    align-items: center;
    display: flex;
    width: 100%;
    height: 400px;
    background: rgba(255, 255, 255, 0.2);
    backdrop-filter: blur(7px); 
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
  .ram{
    font-size: 40pt;
    font-weight: 600;
  }
</style>