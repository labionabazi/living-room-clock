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
        case 3:
          this.imsaku = "05:28"
          this.dreka = "12:15"
          this.ikindia = "14:46"
          this.akshami = "17:17"
          this.jacia = "18:47"
          break
        case 4:
          this.imsaku = "05:30"
          this.dreka = "12:16"
          this.ikindia = "14:46"
          this.akshami = "17:17"
          this.jacia = "18:47"
          break
        case 5:
          this.imsaku = "05:31"
          this.dreka = "12:16"
          this.ikindia = "14:45"
          this.akshami = "17:15"
          this.jacia = "18:45"
          break
        case 6:
          this.imsaku = "05:33"
          this.dreka = "12:16"
          this.ikindia = "14:43"
          this.akshami = "17:13"
          this.jacia = "18:43"
          break
        case 7:
          this.imsaku = "05:34"
          this.dreka = "12:16"
          this.ikindia = "14:42"
          this.akshami = "17:11"
          this.jacia = "18:41"
          break
        case 8:
          this.imsaku = "05:36"
          this.dreka = "12:16"
          this.ikindia = "14:41"
          this.akshami = "17:10"
          this.jacia = "18:40"
          break
        case 9:
          this.imsaku = "05:37"
          this.dreka = "12:16"
          this.ikindia = "14:40"
          this.akshami = "17:09"
          this.jacia = "18:39"
          break
        case 10:
          this.imsaku = "05:39"
          this.dreka = "12:16"
          this.ikindia = "14:39"
          this.akshami = "17:07"
          this.jacia = "18:37"
          break
        case 11:
          this.imsaku = "05:40"
          this.dreka = "12:16"
          this.ikindia = "14:38"
          this.akshami = "17:06"
          this.jacia = "18:36"
          break
        case 12:
          this.imsaku = "05:42"
          this.dreka = "12:17"
          this.ikindia = "14:37"
          this.akshami = "17:05"
          this.jacia = "18:35"
          break
        case 13:
          this.imsaku = "05:43"
          this.dreka = "12:17"
          this.ikindia = "14:36"
          this.akshami = "17:04"
          this.jacia = "18:34"
          break
        case 14:
          this.imsaku = "05:45"
          this.dreka = "12:17"
          this.ikindia = "14:35"
          this.akshami = "17:02"
          this.jacia = "18:32"
          break
        case 15:
          this.imsaku = "05:46"
          this.dreka = "12:17"
          this.ikindia = "14:34"
          this.akshami = "17:01"
          this.jacia = "18:31"
          break
        case 16:
          this.imsaku = "05:48"
          this.dreka = "12:17"
          this.ikindia = "14:33"
          this.akshami = "17:00"
          this.jacia = "18:30"
          break
        case 17:
          this.imsaku = "05:49"
          this.dreka = "12:17"
          this.ikindia = "14:32"
          this.akshami = "16:59"
          this.jacia = "18:29"
          break
        case 18:
          this.imsaku = "05:49"
          this.dreka = "12:17"
          this.ikindia = "14:32"
          this.akshami = "16:59"
          this.jacia = "18:29"
          break
        case 19:
          this.imsaku = "05:51"
          this.dreka = "12:18"
          this.ikindia = "14:32"
          this.akshami = "16:58"
          this.jacia = "18:28"
          break
        case 20:
          this.imsaku = "05:53"
          this.dreka = "12:18"
          this.ikindia = "14:30"
          this.akshami = "16:56"
          this.jacia = "18:26"
          break
        case 21:
          this.imsaku = "05:55"
          this.dreka = "12:18"
          this.ikindia = "14:30"
          this.akshami = "16:55"
          this.jacia = "18:25"
          break
        case 22:
          this.imsaku = "05:56"
          this.dreka = "12:19"
          this.ikindia = "14:29"
          this.akshami = "16:55"
          this.jacia = "18:25"
          break
        case 23:
          this.imsaku = "05:58"
          this.dreka = "12:19"
          this.ikindia = "14:28"
          this.akshami = "16:54"
          this.jacia = "18:24"
          break
        case 24:
          this.imsaku = "05:59"
          this.dreka = "12:19"
          this.ikindia = "14:28"
          this.akshami = "16:53"
          this.jacia = "18:23"
          break
        case 25:
          this.imsaku = "06:00"
          this.dreka = "12:19"
          this.ikindia = "14:27"
          this.akshami = "16:52"
          this.jacia = "18:22"
          break
        case 26:
          this.imsaku = "06:02"
          this.dreka = "12:20"
          this.ikindia = "14:27"
          this.akshami = "16:51"
          this.jacia = "18:21"
          break
        case 27:
          this.imsaku = "06:03"
          this.dreka = "12:20"
          this.ikindia = "14:26"
          this.akshami = "16:51"
          this.jacia = "18:21"
          break
        case 28:
          this.imsaku = "06:04"
          this.dreka = "12:20"
          this.ikindia = "14:26"
          this.akshami = "16:50"
          this.jacia = "18:20"
          break
        case 29:
          this.imsaku = "06:06"
          this.dreka = "12:21"
          this.ikindia = "14:25"
          this.akshami = "16:50"
          this.jacia = "18:20"
          break
        case 30:
          this.imsaku = "06:07"
          this.dreka = "12:21"
          this.ikindia = "14:25"
          this.akshami = "16:49"
          this.jacia = "18:19"
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