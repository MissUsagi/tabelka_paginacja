<template>
   <div class="row">
      <input type="date" id="start-date" name="start-date" min="2000-01-01" :value="getTodaysDate()"
         @input="datePicked($event)">
</div>
</template>

<script>
export default {
   emits: ['selectDate'],
   methods: {
      getTodaysDate() {
         const todaysDate = new Date;
         const zerofill = value => (value < 10 && value > -1 ? '0' : "") + value;
         const todayIs = `${todaysDate.getFullYear()}-${zerofill(todaysDate.getMonth() + 1)}-${zerofill(todaysDate.getDate())}`;
         return todayIs;
      },
      datePicked(e) {
         const selectedDate = e.target.value; //rr-mm-dd
         const reformatedDate = selectedDate.split('-').reverse().join('-');
         this.$emit('selectDate', reformatedDate);
      }
   },
}
</script>

<style scoped>
input[type='date']{
   padding: 8px 10px;
}
</style>
