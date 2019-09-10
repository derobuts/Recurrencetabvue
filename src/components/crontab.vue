<template>
  <div>
    <cronitem v-on:cronpattern="getcronpattern"/>
    <ul class="cron_instances">
      <li class="cronparseinstance" v-for="(cron,index) in recurringpatterns" :key="index">
        <span>Occurs: {{crontohumanreadable(index)}} To: {{cron.endtime}}</span>
        <span @click="recurringpatterns.splice(index,1)">(X)</span>
      </li>
    </ul>
  </div>
</template>
<script>
import moment from "moment";
import cronitem from "@/components/cronitem";
import cronstrue from "cronstrue";
export default {
  components: {
    cronitem
  },
  data: function() {
    return {
      recurringpatterns: []
    };
  },
  methods: {
    getcronpattern(e) {
      this.recurringpatterns.push(e);
    },
    crontohumanreadable(index) {
      return cronstrue.toString(this.recurringpatterns[index].recurringstring);
    }
  },
  computed: {}
};
</script>
<style scoped>
</style>


