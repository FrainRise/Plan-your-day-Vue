<template>
  <div class="form-header">
    <div class="date-row">
      <div class="date-column">
        <span class="date-label day-number">
          {{ getDayNumber }}
        </span>
        <span class="date-label day-month">
          {{ getMonth }}
        </span>
        
      </div>
      <div class="date-column">
        <span class="date-label day">
          {{ getDay }}
        </span>
        <span class="date-label day-year">
          {{ getYear }}
        </span>
      </div> 
    </div>
  </div>
</template>

<script>
export default {
    name: 'FormHeader',
    data: () => {
        return {
            date: new Date(),
            days: ['Sunday', 'Monday', 'Tuesday', 'Wednesday', 'Thursday', 'Friday', 'Saturday'],
            months: ['Jan', 'Feb', 'Mar', 'Apr', 'May', 'June', 'July', 
            'Aug', 'Sep', 'Oct', 'Nov', 'Dec',]
            
        }
    },
    computed: {
      getDayNumber: function() {
        return this.date.getDate()
      },
      getMonth: function() {
        return this.months[this.date.getMonth()]
      },
      getDay: function() {
        return this.days[this.date.getDay()]
      },
      getYear: function() {
        return this.date.getFullYear()
      }
    }
}
</script>

<style>
  .date-label {
    color: #70757c;
  }
  
  .date-row {
    width: 100%;
    display: flex;
    flex-direction: row;
    justify-content: space-between;
    align-items: center;
  }

  .date-column {
    display: inherit;
    flex-direction: column;
  }

  .day-number {
    font-size: 1.5  rem;
  }
  
  .date-label {
    font-weight: bold;
    letter-spacing: 0.2rem;
  }
</style>