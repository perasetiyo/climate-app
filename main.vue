
new Vue({
  el: '#app',
  data: {
    selected: '',
    //convertedTime: null,
    itemss: null,
    link: ''
  },
  methods:{
    getWeathers: function(){
        this.$http.get(this.link).then(function(response){
            this.itemss = response.data;
        }, function(error){
            console.log(error.statusText);
        });
    },
    // TODO: convert epoch time
    /*
    convertTime: function(epochTime){
      this.convertedTime = new Date(epochTime)
    },
    */
    // TODO: make getWeather always sync with selected city
    checkCity: function(){
      if(this.selected == 'London') {
          this.link = 'http://api.openweathermap.org/data/2.5/forecast/daily?q=London&mode=json&units=metric&cnt=5&dt_txt=date&APPID=481e3bc28e5264e5607c2b65b449bfc1'
      } else if(this.selected == 'Tokyo'){
          this.link = 'http://api.openweathermap.org/data/2.5/forecast/daily?q=Tokyo&mode=json&units=metric&cnt=5&dt_txt=date&APPID=481e3bc28e5264e5607c2b65b449bfc1'
      } else {
          this.link = 'http://api.openweathermap.org/data/2.5/forecast/daily?q=Jakarta&mode=json&units=metric&cnt=5&dt_txt=date&APPID=481e3bc28e5264e5607c2b65b449bfc1'
          this.selected = 'Jakarata';
      }
    }
  },
  mounted: function () {
    this.checkCity();
    this.getWeathers();
    //this.convertTime(itemss.list.dt);
  }
});
