<template>
  <div class="digitalClock">
    <div class="leftContainer">
      <div align="right">
        <div id="clock" class="zeit" >{{timeToDisplay}}</div>
        <div id="date">{{dateToDisplay}}</div>
        <!-- <div id="mir">Mirë se vini Familje Bala</div> -->
        <div id="text">by Labion Abazi</div>
      </div>
    </div>
    <div class="middleContainer">
    </div>
    <div class="rightContainer">
      <!-- <div id="shahada">{{shahada}}</div> -->
      <table class="table">
        <tr>
          <td>Imsaku</td>
          <td class="zeit">{{imsaku}}</td>
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
          <td>Akshami</td>
          <td class="zeit">{{akshami}}</td>
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

      setTimeout(this.showDateTime, 1000);
    },
    getVaktia(dateNumber) {
      console.log(dateNumber)
      switch (dateNumber) {
        case 1:
          this.imsaku = "05:17"
          this.dreka = "13:33"
          this.ikindia = "17:08"
          this.akshami = "20:04"
          this.jacia = "21:34"
          break
        case 2:
          this.imsaku = "05:15"
          this.dreka = "13:33"
          this.ikindia = "17:09"
          this.akshami = "20:06"
          this.jacia = "21:36"
          break
        case 3:
          this.imsaku = "05:13"
          this.dreka = "13:32"
          this.ikindia = "17:09"
          this.akshami = "20:07"
          this.jacia = "21:37"
          break
        case 4:
          this.imsaku = "05:11"
          this.dreka = "13:32"
          this.ikindia = "17:10"
          this.akshami = "20:09"
          this.jacia = "21:39"
          break
        case 5:
          this.imsaku = "05:09"
          this.dreka = "13:32"
          this.ikindia = "17:11"
          this.akshami = "20:10"
          this.jacia = "21:40"
          break
        case 6:
          this.imsaku = "05:07"
          this.dreka = "13:30"
          this.ikindia = "17:11"
          this.akshami = "20:11"
          this.jacia = "21:41"
          break
        case 7:
          this.imsaku = "05:05"
          this.dreka = "13:31"
          this.ikindia = "17:12"
          this.akshami = "20:13"
          this.jacia = "21:43"
          break
        case 8:
          this.imsaku = "05:03"
          this.dreka = "13:31"
          this.ikindia = "17:12"
          this.akshami = "20:14"
          this.jacia = "21:44"
          break
        case 9:
          this.imsaku = "05:01"
          this.dreka = "13:31"
          this.ikindia = "17:13"
          this.akshami = "20:16"
          this.jacia = "21:46"
          break
          //Bis hier ist schon April
        case 10:
          this.imsaku = "05:01"
          this.dreka = "12:39"
          this.ikindia = "15:50"
          this.akshami = "18:33"
          this.jacia = "20:03"
          break
        case 11:
          this.imsaku = "04:59"
          this.dreka = "12:39"
          this.ikindia = "15:51"
          this.akshami = "18:34"
          this.jacia = "20:04"
          break
        case 12:
          this.imsaku = "04:57"
          this.dreka = "12:39"
          this.ikindia = "15:52"
          this.akshami = "18:36"
          this.jacia = "20:06"
          break
        case 13:
          this.imsaku = "04:55"
          this.dreka = "12:39"
          this.ikindia = "15:53"
          this.akshami = "18:37"
          this.jacia = "20:07"
          break
        case 14:
          this.imsaku = "04:53"
          this.dreka = "12:38"
          this.ikindia = "15:54"
          this.akshami = "18:39"
          this.jacia = "20:09"
          break
        case 15:
          this.imsaku = "04:51"
          this.dreka = "12:38"
          this.ikindia = "15:55"
          this.akshami = "18:40"
          this.jacia = "20:10"
          break
        case 16:
          this.imsaku = "04:49"
          this.dreka = "12:38"
          this.ikindia = "15:56"
          this.akshami = "18:42"
          this.jacia = "20:12"
          break
        case 17:
          this.imsaku = "04:47"
          this.dreka = "12:37"
          this.ikindia = "15:58"
          this.akshami = "18:43"
          this.jacia = "20:13"
          break
        case 18:
          this.imsaku = "04:45"
          this.dreka = "12:37"
          this.ikindia = "15:57"
          this.akshami = "18:45"
          this.jacia = "20:15"
          break
        case 19:
          this.imsaku = "04:43"
          this.dreka = "12:37"
          this.ikindia = "15:58"
          this.akshami = "18:46"
          this.jacia = "20:16"
          break
        case 20:
          this.imsaku = "04:41"
          this.dreka = "12:37"
          this.ikindia = "15:59"
          this.akshami = "18:47"
          this.jacia = "20:17"
          break
        case 21:
          this.imsaku = "04:39"
          this.dreka = "12:36"
          this.ikindia = "16:00"
          this.akshami = "18:49"
          this.jacia = "20:19"
          break
        case 22:
          this.imsaku = "04:37"
          this.dreka = "12:36"
          this.ikindia = "16:00"
          this.akshami = "18:50"
          this.jacia = "20:20"
          break
        case 23:
          this.imsaku = "04:35"
          this.dreka = "12:36"
          this.ikindia = "16:01"
          this.akshami = "18:52"
          this.jacia = "20:22"
          break
        case 24:
          this.imsaku = "04:33"
          this.dreka = "12:35"
          this.ikindia = "16:02"
          this.akshami = "18:53"
          this.jacia = "20:23"
          break
        case 25:
          this.imsaku = "04:31"
          this.dreka = "12:35"
          this.ikindia = "16:03"
          this.akshami = "18:54"
          this.jacia = "20:24"
          break
        case 26:
          this.imsaku = "04:29"
          this.dreka = "12:35"
          this.ikindia = "16:04"
          this.akshami = "18:56"
          this.jacia = "20:26"
          break
        case 27:
          this.imsaku = "04:27"
          this.dreka = "12:35"
          this.ikindia = "16:04"
          this.akshami = "18:57"
          this.jacia = "20:27"
          break
        case 28:
          this.imsaku = "05:25"
          this.dreka = "13:34"
          this.ikindia = "17:05"
          this.akshami = "19:59"
          this.jacia = "21:29"
          break
        case 29:
          this.imsaku = "05:23"
          this.dreka = "13:34"
          this.ikindia = "17:06"
          this.akshami = "20:00"
          this.jacia = "21:30"
          break
        case 30:
          this.imsaku = "05:21"
          this.dreka = "13:34"
          this.ikindia = "17:06"
          this.akshami = "20:02"
          this.jacia = "21:32"
          break
        case 31:
          this.imsaku = "05:19"
          this.dreka = "13:33"
          this.ikindia = "17:07"
          this.akshami = "20:03"
          this.jacia = "21:33"
          break
      }
    },
    playSound() {
      var audio = new Audio(require('../assets/adhan.mp3'));
      audio.crossOrigin = 'anonymous';
      audio.play();
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
  #mir{
    font-size: 70pt;
    margin-bottom: 0;
  }
  #shahada{
    font-size: 50pt;
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
    font-weight: 50S0;
  }
  .zeit{
    font-family: 'Dosis', sans-serif;
    font-family: 'Exo', sans-serif;
    font-family: 'Geo', sans-serif;
    font-family: 'Orbitron', sans-serif;
  }
</style>