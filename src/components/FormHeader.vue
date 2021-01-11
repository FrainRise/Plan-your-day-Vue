<template>
  <div class="form-header">
    <div class="date-row">
      <div class="date-column">
        <span class="date-label day-number">
          {{ date.getDate() }}
        </span>
        <span class="date-label day-month">
          {{ months[date.getMonth()]}}
        </span>
        
      </div>
      <div class="date-column">
        <span class="date-label day">
          {{ days[date.getDay()] }}
        </span>
        <span class="date-label day-year">
          {{ date.getFullYear() }}
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