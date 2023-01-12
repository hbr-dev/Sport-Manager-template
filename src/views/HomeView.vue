<template>
  <header>
    <div class="headline">
      <div class="inner">
        <h1>Best web app for whose crazy about sports</h1>
        <p>Scroll down the page</p>
        <div>
          <button><a href="#matches">Book tiket</a></button>
          <button type="button" @click="returnMyBookingHistory"><a href="#bookmark-history">My Booking</a></button>
        </div>
      </div>
    </div>
  </header>
  <div id="matches" class="matches">
    <div class="title"><h3>Upcoming Match</h3></div>
    <div class="container">
      <div class="matche" v-for="matche in matches" :key="matche.id">
        <!-- ======================================================== -->
        <div class="flags">
          <div class="team1-flag">
            <div class="flag"><img src="../assets/img/logo_1.png" alt=""></div>
            <div class="team-name">{{ matche.team1.name }}</div>
          </div>
          <!-- --------------------------- -->
          <div class="versus">VS</div>
          <!-- --------------------------- -->
          <div class="team2-flag">
            <div class="flag"><img src="../assets/img/logo_2.png" alt=""></div>
            <div class="team-name">{{ matche.team2.name }}</div>
          </div>
        </div>
        <!-- ========================================================= -->
        <div class="competition">
          <h3>{{ matche.team1.competition }}</h3>
        </div>
        <!-- ========================================================= -->
        <div class="date-time">
          <p id="date">{{ matche.team1.start_date }}</p>
          <p id="time">{{ matche.team1.start_time }}</p>
        </div>
        <!-- ========================================================= -->
        <div class="field">
          <p>{{ matche.team1.field }}</p>
        </div>
        <!-- ========================================================= -->
        <div class="book-tiket">
          <button type="button" class="btn btn-primary"> 
            <a href="#code-check" @click="bindn_IDref(matche.team1.id)">Book Now</a> 
          </button>
        </div>
        <!-- ========================================================= -->
        <!-- ========================================================= -->
      </div>
    </div>
  </div>
  <!-- ########################################################################################## -->
  <div class="wf-modal" aria-hidden="true" id="code-check">
    <article class="wf-dialog-modal">
      <header class="wf-header-modal">
        <h2 class="tit">Code verification</h2>
        <span class="close"><a href="#" class="bt" aria-hidden="true"></a></span>
      </header>
      <div class="wf-content-modal">
        <label for="code">Enter verification code : </label>
        <input type="text" v-model="codeToVerify">
      </div>
      <footer class="wf-footer-modal">
        <span class="ok">
          <a href="#" class="bt" aria-hidden="true"  @click="addToBookMarks">ok</a>
        </span>
      </footer>
    </article>
  </div>
  <!-- ################################################################################# -->
  <div class="wf-modal" aria-hidden="true" id="bookmark-history">
    <article class="wf-dialog-modal">
      <header class="wf-header-modal">
        <h2 class="tit">Booking history</h2>
        <span class="close"><a href="#" class="bt" aria-hidden="true"></a></span>
      </header>
      <div class="wf-content-modal">
        <table id="bookmark-table">
          <thead>
            <tr>
              <th>P</th>
              <th>Field</th>
              <th>Date</th>
              <th>Time</th>
              <th>Teams</th>
            </tr>
          </thead>
          <tbody>
            <tr v-for="historyBookMark in historyBookMarks" :key="historyBookMark.id">
              <td>{{ historyBookMark.game_id }}</td>
              <td>{{ historyBookMark.field }}</td>
              <td>{{ historyBookMark.start_date }}</td>
              <td>{{ historyBookMark.start_time }}</td>
              <td>{{ historyBookMark.teams }}</td>
            </tr>
          </tbody>
        </table>
      </div>
      <footer class="wf-footer-modal">
        <span class="ok"><a href="#" class="bt" aria-hidden="true">ok</a></span>
      </footer>
    </article>
  </div>
  <!-- ################################################################################# -->
</template>

<style scoped>
  @import '../assets/css/homeVue.css';
  @import 'https://cdn.jsdelivr.net/npm/bootstrap@5.2.3/dist/css/bootstrap.min.css';
</style>

<script>

let id = 0

export default {
  data () {
    return {
      // In Backe-end matches will be
      // matches : []
      // Then will get the axios request result
      id_ref : "",
      codeToVerify : "",
      trueCode : "ab123", 
      matches : [ 
        {
          team1 : {
            id : id++, name : 'Football League', flag : '../assets/img/logo_1.png', start_date : 'December 25th, 2022',   start_time : '04:30 PM GMT+0', field : 'Mal3ab al khima', competition : 'World Cup League'
          }, 
          team2 : {
            id : id++, name : 'Soccer', flag : '../assets/img/logo_2.png', start_date : 'December 25th, 2022',   start_time : '08:30 PM GMT+0', field : 'Mal3ab al khima', competition : 'World Cup League'
          }
        },
        {
          team1 : {
            id : id++, name : 'Football League', flag : '../assets/img/logo_1.png', start_date : 'December 26th, 2022',   start_time : '04:30 PM GMT+0', field : 'Mal3ab al khima', competition : 'World Cup League'
          }, 
          team2 : {
            id : id++, name : 'Soccer', flag : '../assets/img/logo_2.png', start_date : 'December 26th, 2022',   start_time : '08:30 PM GMT+0', field : 'Mal3ab al khima', competition : 'World Cup League'
          }
        },
        {
          team1 : {
            id : id++, name : 'Football League', flag : '../assets/img/logo_1.png', start_date : 'December 27th, 2022',   start_time : '04:30 PM GMT+0', field : 'Mal3ab al khima', competition : 'World Cup League'
          }, 
          team2 : {
            id : id++, name : 'Soccer', flag : '../assets/img/logo_2.png', start_date : 'December 27th, 2022',   start_time : '08:30 PM GMT+0', field : 'Mal3ab al khima', competition : 'World Cup League'
          }
        },
        {
          team1 : {
            id : id++, name : 'Football League', flag : '../assets/img/logo_1.png', start_date : 'December 28th, 2022',   start_time : '04:30 PM GMT+0', field : 'Mal3ab al khima', competition : 'World Cup League'
          }, 
          team2 : {
            id : id++, name : 'Soccer', flag : '../assets/img/logo_2.png', start_date : 'December 28th, 2022',   start_time : '08:30 PM GMT+0', field : 'Mal3ab al khima', competition : 'World Cup League'
          }
        },
        {
          team1 : {
            id : id++, name : 'Football League', flag : '../assets/img/logo_1.png', start_date : 'December 29th, 2022',   start_time : '04:30 PM GMT+0', field : 'Mal3ab al khima', competition : 'World Cup League'
          }, 
          team2 : {
            id : id++, name : 'Soccer', flag : '../assets/img/logo_2.png', start_date : 'December 29th, 2022',   start_time : '08:30 PM GMT+0', field : 'Mal3ab al khima', competition : 'World Cup League'
          }
        },
        {
          team1 : {
            id : id++, name : 'Football League', flag : '../assets/img/logo_1.png', start_date : 'December 30th, 2022',   start_time : '04:30 PM GMT+0', field : 'Mal3ab al khima', competition : 'World Cup League'
          }, 
          team2 : {
            id : id++, name : 'Soccer', flag : '../assets/img/logo_2.png', start_date : 'December 30th, 2022',   start_time : '08:30 PM GMT+0', field : 'Mal3ab al khima', competition : 'World Cup League'
          }
        }
      ],
      bookingHistory : {// will be saved as the tiket data in the DB;
        user_id : '',
        game_id : '',
        field : '',
        start_date : '',
        start_time : '',
        teams : '',
        bookingTime : ''
      },
      historyBookMarks : [ // will be returned from the DB 
        {
          game_id : '10',
          field : 'fake',
          start_date : 'AAAA-MM-DD',
          start_time : 'HH:mm:ss',
          teams : 'team1 VS team2',
          bookingTime : 'AAAA-MM-DD'
        }, 
        {
          game_id : '11',
          field : 'fake',
          start_date : 'AAAA-MM-DD',
          start_time : 'HH:mm:ss',
          teams : 'team1 VS team2',
          bookingTime : 'AAAA-MM-DD'
        }, 
        {
          game_id : '12',
          field : 'fake',
          start_date : 'AAAA-MM-DD',
          start_time : 'HH:mm:ss',
          teams : 'team1 VS team2',
          bookingTime : 'AAAA-MM-DD'
        }
      ]
    }
  },
  methods: {
    bindn_IDref(id){
      this.id_ref = id;
      console.log(this.id_ref);
    },
    addToBookMarks() {
      // trueCode = get Request from the database : transaction table;
      if(this.codeToVerify == this.trueCode) {
        let id = this.id_ref;
        alert('Your demand was succefully saved! Check your bookmark.');
        this.bookingHistory.game_id = id / 2;
        this.bookingHistory.field = this.matches[id / 2].team1.field;
        this.bookingHistory.start_date = this.matches[id / 2].team1.start_date;
        this.bookingHistory.start_time = this.matches[id / 2].team1.start_time;
        this.bookingHistory.teams = this.matches[id / 2].team1.name + " VS " + this.matches[id / 2].team2.name;
        this.bookingHistory.bookingTime = new Date();
        // Store into the database;
        console.log(this.bookingHistory);
      }
      else {
        alert('Your demand Failed! Check your code.');
        console.log(this.codeToVerify);
      }
    },
    returnMyBookingHistory() {
      console.log(this.bookingHistory);
    }
  }
}
</script>
