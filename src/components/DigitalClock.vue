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
          this.imsaku = "05:19"
          this.dreka = "12:42"
          this.ikindia = "15:41"
          this.akshami = "18:19"
          this.jacia = "19:49"
          break
        case 2:
          this.imsaku = "05:16"
          this.dreka = "12:41"
          this.ikindia = "15:42"
          this.akshami = "18:21"
          this.jacia = "19:51"
          break
        case 3:
          this.imsaku = "05:14"
          this.dreka = "12:41"
          this.ikindia = "15:43"
          this.akshami = "18:23"
          this.jacia = "19:53"
          break
        case 4:
          this.imsaku = "05:12"
          this.dreka = "12:41"
          this.ikindia = "15:44"
          this.akshami = "18:24"
          this.jacia = "19:54"
          break
        case 5:
          this.imsaku = "05:10"
          this.dreka = "12:41"
          this.ikindia = "15:45"
          this.akshami = "18:26"
          this.jacia = "19:56"
          break
        case 6:
          this.imsaku = "05:09"
          this.dreka = "12:40"
          this.ikindia = "15:46"
          this.akshami = "18:27"
          this.jacia = "19:57"
          break
        case 7:
          this.imsaku = "05:07"
          this.dreka = "12:40"
          this.ikindia = "15:47"
          this.akshami = "18:29"
          this.jacia = "19:59"
          break
        case 8:
          this.imsaku = "05:05"
          this.dreka = "12:40"
          this.ikindia = "15:48"
          this.akshami = "18:30"
          this.jacia = "20:00"
          break
          //AB HIER STIMMT NICHT MEHR - BIS MÄRZ
        case 9:
          this.imsaku = "05:54"
          this.dreka = "12:43"
          this.ikindia = "15:17"
          this.akshami = "17:48"
          this.jacia = "19:18"
          break
        case 10:
          this.imsaku = "05:53"
          this.dreka = "12:44"
          this.ikindia = "15:18"
          this.akshami = "17:49"
          this.jacia = "19:19"
          break
        case 11:
          this.imsaku = "05:51"
          this.dreka = "12:44"
          this.ikindia = "15:19"
          this.akshami = "17:51"
          this.jacia = "19:21"
          break
        case 12:
          this.imsaku = "05:50"
          this.dreka = "12:44"
          this.ikindia = "15:21"
          this.akshami = "17:52"
          this.jacia = "19:22"
          break
        case 13:
          this.imsaku = "05:50"
          this.dreka = "12:43"
          this.ikindia = "15:22"
          this.akshami = "17:54"
          this.jacia = "19:24"
          break
        case 14:
          this.imsaku = "05:46"
          this.dreka = "12:43"
          this.ikindia = "15:23"
          this.akshami = "17:55"
          this.jacia = "19:25"
          break
        case 15:
          this.imsaku = "05:45"
          this.dreka = "12:43"
          this.ikindia = "15:24"
          this.akshami = "17:57"
          this.jacia = "19:27"
          break
        case 16:
          this.imsaku = "05:43"
          this.dreka = "12:43"
          this.ikindia = "15:26"
          this.akshami = "17:58"
          this.jacia = "19:28"
          break
        case 17:
          this.imsaku = "05:41"
          this.dreka = "12:43"
          this.ikindia = "15:27"
          this.akshami = "17:58"
          this.jacia = "19:30"
          break
        case 18:
          this.imsaku = "05:40"
          this.dreka = "12:43"
          this.ikindia = "15:28"
          this.akshami = "18:02"
          this.jacia = "19:32"
          break
        case 19:
          this.imsaku = "05:38"
          this.dreka = "12:43"
          this.ikindia = "15:29"
          this.akshami = "18:03"
          this.jacia = "19:33"
          break
        case 20:
          this.imsaku = "05:36"
          this.dreka = "12:43"
          this.ikindia = "15:30"
          this.akshami = "18:05"
          this.jacia = "19:35"
          break
        case 21:
          this.imsaku = "05:35"
          this.dreka = "12:43"
          this.ikindia = "15:31"
          this.akshami = "18:06"
          this.jacia = "19:36"
          break
        case 22:
          this.imsaku = "05:33"
          this.dreka = "12:43"
          this.ikindia = "15:33"
          this.akshami = "18:08"
          this.jacia = "19:38"
          break
        case 23:
          this.imsaku = "05:31"
          this.dreka = "12:43"
          this.ikindia = "15:34"
          this.akshami = "18:09"
          this.jacia = "19:39"
          break
        case 24:
          this.imsaku = "05:29"
          this.dreka = "12:43"
          this.ikindia = "15:35"
          this.akshami = "18:11"
          this.jacia = "19:41"
          break
        case 25:
          this.imsaku = "05:27"
          this.dreka = "12:42"
          this.ikindia = "15:36"
          this.akshami = "18:12"
          this.jacia = "19:42"
          break
        case 26:
          this.imsaku = "05:26"
          this.dreka = "12:42"
          this.ikindia = "15:37"
          this.akshami = "18:14"
          this.jacia = "19:44"
          break
        case 27:
          this.imsaku = "05:24"
          this.dreka = "12:42"
          this.ikindia = "15:38"
          this.akshami = "18:15"
          this.jacia = "19:45"
          break
        case 28:
          this.imsaku = "05:22"
          this.dreka = "12:42"
          this.ikindia = "15:39"
          this.akshami = "18:17"
          this.jacia = "19:47"
          break
        // case 29:
        //   this.imsaku = "06:09"
        //   this.dreka = "12:42"
        //   this.ikindia = "15:03"
        //   this.akshami = "17:30"
        //   this.jacia = "19:00"
        //   break
        // case 30:
        //   this.imsaku = "06:08"
        //   this.dreka = "12:43"
        //   this.ikindia = "15:04"
        //   this.akshami = "17:32"
        //   this.jacia = "19:02"
        //   break
        // case 31:
        //   this.imsaku = "06:06"
        //   this.dreka = "12:43"
        //   this.ikindia = "15:06"
        //   this.akshami = "17:33"
        //   this.jacia = "19:03"
        //   break
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