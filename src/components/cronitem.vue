<template>
  <div>
    <span>occurs</span>
    <span class="cron_period">
      <select @change="recurrence_change()" v-model="recurrence">
        <option value="day">daily</option>
        <option value="week">weekly</option>
        <option value="month">monthly</option>
      </select>
      {{getmindifference()}}
    </span>
    <span v-if="recurrence == 'month'" class="cron_block_month">
      day of month
      <select v-model="dayofmonth" class="select">
        <option value="*">All</option>
        <option
          v-for="(cronitem,index) in daysofmonth"
          :key="index"
          :value="cronitem.id"
        >{{cronitem.Name}}</option>
      </select>
      month
      <br>
      <span class="weekDays-selector">
        <span v-for="(cronitem,index) in month" :key="index" class="month">
          <input v-model="months" type="checkbox" :value="cronitem.id" class="select">
          <label for="checkbox">{{cronitem.Name}}</label>
        </span>
      </span>
    </span>
    
    <span v-if="recurrence == 'week'" class="weekDays-selector">
      on
      <span v-for="(cronitem,index) in dayofweek" :key="index">
        <input v-model="daysofweek" type="checkbox" :value="cronitem.id" class="select">
        <label for="checkbox">{{cronitem.Name}}</label>
      </span>
    </span>
    <div>
      <span class="cron_block_time">
        at
        <select v-model="starttimehrs" name="cron-time-hour" class="cron-time-hour">
          <option value="0">00</option>
          <option value="1">01</option>
          <option value="2">02</option>
          <option value="3">03</option>
          <option value="4">04</option>
          <option value="5">05</option>
          <option value="6">06</option>
          <option value="7">07</option>
          <option value="8">08</option>
          <option value="9">09</option>
          <option value="10">10</option>
          <option value="11">11</option>
          <option value="12">12</option>
          <option value="13">13</option>
          <option value="14">14</option>
          <option value="15">15</option>
          <option value="16">16</option>
          <option value="17">17</option>
          <option value="18">18</option>
          <option value="19">19</option>
          <option value="20">20</option>
          <option value="21">21</option>
          <option value="22">22</option>
          <option value="23">23</option>
        </select>
        :
        <select v-model="starttimemin" name="cron-time-min" class="cron-time-min">
          <option value="0">00</option>
          <option value="1">01</option>
          <option value="2">02</option>
          <option value="3">03</option>
          <option value="4">04</option>
          <option value="5">05</option>
          <option value="6">06</option>
          <option value="7">07</option>
          <option value="8">08</option>
          <option value="9">09</option>
          <option value="10">10</option>
          <option value="11">11</option>
          <option value="12">12</option>
          <option value="13">13</option>
          <option value="14">14</option>
          <option value="15">15</option>
          <option value="16">16</option>
          <option value="17">17</option>
          <option value="18">18</option>
          <option value="19">19</option>
          <option value="20">20</option>
          <option value="21">21</option>
          <option value="22">22</option>
          <option value="23">23</option>
          <option value="24">24</option>
          <option value="25">25</option>
          <option value="26">26</option>
          <option value="27">27</option>
          <option value="28">28</option>
          <option value="29">29</option>
          <option value="30">30</option>
          <option value="31">31</option>
          <option value="32">32</option>
          <option value="33">33</option>
          <option value="34">34</option>
          <option value="35">35</option>
          <option value="36">36</option>
          <option value="37">37</option>
          <option value="38">38</option>
          <option value="39">39</option>
          <option value="40">40</option>
          <option value="41">41</option>
          <option value="42">42</option>
          <option value="43">43</option>
          <option value="44">44</option>
          <option value="45">45</option>
          <option value="46">46</option>
          <option value="47">47</option>
          <option value="48">48</option>
          <option value="49">49</option>
          <option value="50">50</option>
          <option value="51">51</option>
          <option value="52">52</option>
          <option value="53">53</option>
          <option value="54">54</option>
          <option value="55">55</option>
          <option value="56">56</option>
          <option value="57">57</option>
          <option value="58">58</option>
          <option value="59">59</option>
        </select>
      </span>
      <span>to</span>
      <span class="cron_block_time">
        <select v-model="endtimehrs" name="cron-time-hour" class="cron-time-hour">
          <option value="0">00</option>
          <option value="1">01</option>
          <option value="2">02</option>
          <option value="3">03</option>
          <option value="4">04</option>
          <option value="5">05</option>
          <option value="6">06</option>
          <option value="7">07</option>
          <option value="8">08</option>
          <option value="9">09</option>
          <option value="10">10</option>
          <option value="11">11</option>
          <option value="12">12</option>
          <option value="13">13</option>
          <option value="14">14</option>
          <option value="15">15</option>
          <option value="16">16</option>
          <option value="17">17</option>
          <option value="18">18</option>
          <option value="19">19</option>
          <option value="20">20</option>
          <option value="21">21</option>
          <option value="22">22</option>
          <option value="23">23</option>
        </select>
        :
        <select v-model="endtimemin" name="cron-time-min" class="cron-time-min">
          <option value="0">00</option>
          <option value="1">01</option>
          <option value="2">02</option>
          <option value="3">03</option>
          <option value="4">04</option>
          <option value="5">05</option>
          <option value="6">06</option>
          <option value="7">07</option>
          <option value="8">08</option>
          <option value="9">09</option>
          <option value="10">10</option>
          <option value="11">11</option>
          <option value="12">12</option>
          <option value="13">13</option>
          <option value="14">14</option>
          <option value="15">15</option>
          <option value="16">16</option>
          <option value="17">17</option>
          <option value="18">18</option>
          <option value="19">19</option>
          <option value="20">20</option>
          <option value="21">21</option>
          <option value="22">22</option>
          <option value="23">23</option>
          <option value="24">24</option>
          <option value="25">25</option>
          <option value="26">26</option>
          <option value="27">27</option>
          <option value="28">28</option>
          <option value="29">29</option>
          <option value="30">30</option>
          <option value="31">31</option>
          <option value="32">32</option>
          <option value="33">33</option>
          <option value="34">34</option>
          <option value="35">35</option>
          <option value="36">36</option>
          <option value="37">37</option>
          <option value="38">38</option>
          <option value="39">39</option>
          <option value="40">40</option>
          <option value="41">41</option>
          <option value="42">42</option>
          <option value="43">43</option>
          <option value="44">44</option>
          <option value="45">45</option>
          <option value="46">46</option>
          <option value="47">47</option>
          <option value="48">48</option>
          <option value="49">49</option>
          <option value="50">50</option>
          <option value="51">51</option>
          <option value="52">52</option>
          <option value="53">53</option>
          <option value="54">54</option>
          <option value="55">55</option>
          <option value="56">56</option>
          <option value="57">57</option>
          <option value="58">58</option>
          <option value="59">59</option>
        </select>
        of The
        <select v-model="repeat_day">
          <option
            v-for="(repeat,index) in repeating_time"
            :key="index"
            :value="repeat.id"
          >{{repeat.Name}}</option>
        </select>
      </span>
    </div>
    <div class="cron_buttons">
      <button :disabled="intervallength<=0" @click="addrecurrence()" class="save_cron">Add</button>
    </div>
    <span v-if="intervallength <=0">Day cannot Be in the Past</span>
  </div>
</template>
<script>
import moment from "moment";
import cronstrue from "cronstrue";
export default {
  data: function() {
    return {
      recurrence: "day",
      monthrecurrence: "everymonth",
      daysofweek: [],
      dayofmonth: "*",
      repeat_dayvalid: true,
      cron_strarray: [],
      intervallength: 0,
      starttimehrs: "8",
      starttimemin: "30",
      endtimehrs: "13",
      endtimemin: "30",
      recurrenceendtime: "",
      error: "",
      repeat_day: 0,
      months: [],
      daysofmonth: [
        { id: 1, Name: "1" },
        { id: 2, Name: "2" },
        { id: 3, Name: "3" },
        { id: 4, Name: "4" },
        { id: 5, Name: "5" },
        { id: 6, Name: "6" },
        { id: 7, Name: "7" },
        { id: 8, Name: "8" },
        { id: 9, Name: "9" },
        { id: 10, Name: "10" },
        { id: 11, Name: "11" },
        { id: 12, Name: "12" },
        { id: 13, Name: "13" },
        { id: 14, Name: "14" },
        { id: 15, Name: "15" },
        { id: 16, Name: "16" },
        { id: 17, Name: "17" },
        { id: 18, Name: "18" },
        { id: 19, Name: "19" },
        { id: 20, Name: "20" },
        { id: 21, Name: "21" },
        { id: 22, Name: "22" },
        { id: 23, Name: "23" },
        { id: 24, Name: "24" },
        { id: 25, Name: "25" },
        { id: 26, Name: "26" },
        { id: 27, Name: "27" },
        { id: 28, Name: "28" },
        { id: 29, Name: "29" },
        { id: 30, Name: "30" },
        { id: 31, Name: "31" }
      ],
      month: [
        { id: 1, Name: "Jan" },
        { id: 2, Name: "Feb" },
        { id: 3, Name: "Mar" },
        { id: 4, Name: "Apr" },
        { id: 5, Name: "May" },
        { id: 6, Name: "Jun" },
        { id: 7, Name: "Jul" },
        { id: 8, Name: "Aug" },
        { id: 9, Name: "Sept" },
        { id: 10, Name: "Oct" },
        { id: 11, Name: "Nov" },
        { id: 12, Name: "Dec" }
      ],
      dayofweek: [
        { id: 1, Name: "Mon" },
        { id: 2, Name: "Tue" },
        { id: 3, Name: "Wed" },
        { id: 4, Name: "Thur" },
        { id: 5, Name: "Fri" },
        { id: 6, Name: "Sat" },
        { id: 0, Name: "Sun" }
      ],
      repeating_time: [
        { id: 0, Name: "same day" },
        { id: 1, Name: "next day" },
        { id: 2, Name: "2nd day" },
        { id: 3, Name: "3rd day" },
        { id: 4, Name: "4th day" },
        { id: 5, Name: "5th day" },
        { id: 6, Name: "6th day" }
      ]
    };
  },
  methods: {
    recurrence_change() {
      (this.daysofweek = []), (this.months = []);
      this.dayofmonth = "*";
    },
    addrecurrence() {
      this.$emit("cronpattern", {
        recurringstring: this.cron_string,
        intervallengthmins: this.intervallength,
        endtime: this.recurrenceendtime,
        parsedcron: cronstrue.toString(this.cron_string)
      });
    },
    getmindifference() {
      var starttime = this.starttimehrs + ":" + this.starttimemin;
      var endtime = this.endtimehrs + ":" + this.endtimemin;
      var date = "10/02/2019";
      var startdatetime = moment(date + " " + starttime, "DD/MM/YYYY HH:mm")
        .utc()
        .format("YYYY-MM-DD HH:mm:ssZ");
      var enddatetime = moment(date + " " + endtime, "DD/MM/YYYY HH:mm")
        .utc()
        .format("YYYY-MM-DD HH:mm:ssZ");
      var enddate = moment(enddatetime).add(this.repeat_day, "days");
      var duration = moment.duration(enddate.diff(startdatetime));
      this.recurrenceendtime = moment(
        date + " " + endtime,
        "DD/MM/YYYY HH:mm"
      ).format("hh:mm A");
      this.intervallength = duration.asMinutes();
      return duration.asMinutes() >= 60
        ? Math.ceil(duration.asMinutes() / 60) + " " + "hrs"
        : duration.asMinutes() + " " + "mins";
    }
  },
  computed: {
    daysofweekcom() {
      return this.daysofweek.length == 0 || this.daysofweek.length == 7
        ? "*"
        : this.daysofweek.join(",");
    },
    monthscom() {
      return this.months.length == 0 || this.months.length == 12
        ? "*"
        : this.months.join(",");
    },
    cron_string() {
      return (
        this.starttimemin +
        " " +
        this.starttimehrs +
        " " +
        this.dayofmonth +
        " " +
        this.monthscom +
        " " +
        this.daysofweekcom
      );
    },
    repeat_intervalerror() {}
  }
};
</script>
<style scoped>
.cron_buttons {
  display: flex;
  flex-wrap: wrap;
}
select {
  padding: 2px 2px;
  background-color: #fff;
  border: 1px solid #ccc;
  border-radius: 4px;
  -webkit-box-shadow: inset 0 1px 1px rgba(0, 0, 0, 0.075);
  box-shadow: inset 0 1px 1px rgba(0, 0, 0, 0.075);
  -webkit-transition: border-color ease-in-out 0.15s,
    box-shadow ease-in-out 0.15s;
  -webkit-transition: border-color ease-in-out 0.15s,
    -webkit-box-shadow ease-in-out 0.15s;
  transition: border-color ease-in-out 0.15s,
    -webkit-box-shadow ease-in-out 0.15s;
  transition: border-color ease-in-out 0.15s, box-shadow ease-in-out 0.15s;
  transition: border-color ease-in-out 0.15s, box-shadow ease-in-out 0.15s,
    -webkit-box-shadow ease-in-out 0.15s;
}

.weekDays-selector input[type="checkbox"] + label {
  display: inline;
  border-radius: 3px;
  padding: 0px 2px 0px 2px;
  background: #dddddd;
  margin-right: 3px;
  line-height: 40px;
  text-align: center;
  cursor: pointer;
}

.weekDays-selector input[type="checkbox"]:checked + label {
  background: #0c9a9a;
  color: #ffffff;
}
.save_cron {
  background-color: #0c9a9a;
  color: #fff;
  font-weight: 400;
  width: 100px;
  font-family: "Arial Narrow Bold", Arial;
  text-align: center;
  text-transform: capitalize;
  cursor: pointer;
  border: 1px solid transparent;
  white-space: nowrap;
  padding: 0 5px;
  margin-right: 4px;
  font-size: 14px;
  line-height: 2;
  border-radius: 2px;
  margin-top: 8px;
}
div {
  margin-top: 10px;
}
button:disabled,
button[disabled] {
  border: 1px solid #999999;
  background-color: #cccccc;
  color: #666666;
}
</style>


