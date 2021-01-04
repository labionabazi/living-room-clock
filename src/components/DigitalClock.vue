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
        // case 1:
        //   this.imsaku = "05:28"
        //   this.dreka = "12:15"
        //   this.ikindia = "14:46"
        //   this.akshami = "17:17"
        //   this.jacia = "18:47"
        //   break
        // case 2:
        //   this.imsaku = "05:28"
        //   this.dreka = "12:15"
        //   this.ikindia = "14:46"
        //   this.akshami = "17:17"
        //   this.jacia = "18:47"
        //   break
        // case 3:
        //   this.imsaku = "05:28"
        //   this.dreka = "12:15"
        //   this.ikindia = "14:46"
        //   this.akshami = "17:17"
        //   this.jacia = "18:47"
        //   break
        case 4:
          this.imsaku = "06:25"
          this.dreka = "12:34"
          this.ikindia = "14:34"
          this.akshami = "16:57"
          this.jacia = "18:27"
          break
        case 5:
          this.imsaku = "06:25"
          this.dreka = "12:34"
          this.ikindia = "14:35"
          this.akshami = "16:58"
          this.jacia = "18:28"
          break
        case 6:
          this.imsaku = "06:25"
          this.dreka = "12:34"
          this.ikindia = "14:36"
          this.akshami = "16:59"
          this.jacia = "18:29"
          break
        case 7:
          this.imsaku = "06:25"
          this.dreka = "12:34"
          this.ikindia = "14:37"
          this.akshami = "17:00"
          this.jacia = "18:30"
          break
        case 8:
          this.imsaku = "06:24"
          this.dreka = "12:36"
          this.ikindia = "14:38"
          this.akshami = "17:01"
          this.jacia = "18:31"
          break
        case 9:
          this.imsaku = "06:24"
          this.dreka = "12:36"
          this.ikindia = "14:39"
          this.akshami = "17:02"
          this.jacia = "18:32"
          break
        case 10:
          this.imsaku = "06:24"
          this.dreka = "12:37"
          this.ikindia = "14:40"
          this.akshami = "17:04"
          this.jacia = "18:34"
          break
        case 11:
          this.imsaku = "06:24"
          this.dreka = "12:37"
          this.ikindia = "14:41"
          this.akshami = "17:05"
          this.jacia = "18:35"
          break
        case 12:
          this.imsaku = "06:23"
          this.dreka = "12:37"
          this.ikindia = "14:42"
          this.akshami = "17:06"
          this.jacia = "18:36"
          break
        case 13:
          this.imsaku = "06:23"
          this.dreka = "12:38"
          this.ikindia = "14:43"
          this.akshami = "17:07"
          this.jacia = "18:37"
          break
        case 14:
          this.imsaku = "06:22"
          this.dreka = "12:38"
          this.ikindia = "14:45"
          this.akshami = "17:09"
          this.jacia = "18:39"
          break
        case 15:
          this.imsaku = "06:21"
          this.dreka = "12:39"
          this.ikindia = "14:46"
          this.akshami = "17:10"
          this.jacia = "18:40"
          break
        case 16:
          this.imsaku = "06:21"
          this.dreka = "12:39"
          this.ikindia = "14:47"
          this.akshami = "17:11"
          this.jacia = "18:41"
          break
        case 17:
          this.imsaku = "06:20"
          this.dreka = "12:39"
          this.ikindia = "14:48"
          this.akshami = "17:13"
          this.jacia = "18:43"
          break
        case 18:
          this.imsaku = "06:19"
          this.dreka = "12:40"
          this.ikindia = "14:49"
          this.akshami = "17:14"
          this.jacia = "18:44"
          break
        case 19:
          this.imsaku = "06:19"
          this.dreka = "12:40"
          this.ikindia = "14:50"
          this.akshami = "17:16"
          this.jacia = "18:46"
          break
        case 20:
          this.imsaku = "06:18"
          this.dreka = "12:40"
          this.ikindia = "14:52"
          this.akshami = "17:17"
          this.jacia = "18:47"
          break
        case 21:
          this.imsaku = "06:17"
          this.dreka = "12:40"
          this.ikindia = "14:53"
          this.akshami = "17:18"
          this.jacia = "18:48"
          break
        case 22:
          this.imsaku = "06:16"
          this.dreka = "12:41"
          this.ikindia = "14:54"
          this.akshami = "17:20"
          this.jacia = "18:50"
          break
        case 23:
          this.imsaku = "06:15"
          this.dreka = "12:41"
          this.ikindia = "14:55"
          this.akshami = "17:21"
          this.jacia = "18:51"
          break
        case 24:
          this.imsaku = "06:14"
          this.dreka = "12:41"
          this.ikindia = "14:57"
          this.akshami = "17:23"
          this.jacia = "18:53"
          break
        case 25:
          this.imsaku = "06:13"
          this.dreka = "12:41"
          this.ikindia = "14:58"
          this.akshami = "17:24"
          this.jacia = "18:54"
          break
        case 26:
          this.imsaku = "06:12"
          this.dreka = "12:42"
          this.ikindia = "14:59"
          this.akshami = "17:26"
          this.jacia = "18:56"
          break
        case 27:
          this.imsaku = "06:11"
          this.dreka = "12:42"
          this.ikindia = "15:00"
          this.akshami = "17:27"
          this.jacia = "18:57"
          break
        case 28:
          this.imsaku = "06:10"
          this.dreka = "12:42"
          this.ikindia = "15:02"
          this.akshami = "17:29"
          this.jacia = "18:59"
          break
        case 29:
          this.imsaku = "06:09"
          this.dreka = "12:42"
          this.ikindia = "15:03"
          this.akshami = "17:30"
          this.jacia = "19:00"
          break
        case 30:
          this.imsaku = "06:08"
          this.dreka = "12:43"
          this.ikindia = "15:04"
          this.akshami = "17:32"
          this.jacia = "19:02"
          break
        case 31:
          this.imsaku = "06:06"
          this.dreka = "12:43"
          this.ikindia = "15:06"
          this.akshami = "17:33"
          this.jacia = "19:03"
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