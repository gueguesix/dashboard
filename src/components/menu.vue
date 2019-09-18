<template>
  <div class="hello">
    <div class="menu-container">
      <div>
        <nav>
          <ul>
            <div id="menuTitle">Sélectionner une région</div>
            <li v-for="region in allRegions" @click="showStats(region)">{{region.name}}</li>
          </ul>
        </nav>
      </div>
    </div>
     <div class="text">
        <div class="text-orange">Contrat de professionalisation des salariés</div>
        <div class="text-title">Répartition des stagiaires par sexe et par tranche d'âge</div>
        <div class="text-grey">en 2016</div>
      </div>
    <div id="chart-container">
      <div id="donut-container">
        <canvas id="doughnut-chart" ></canvas>
        <canvas id="doughnut-chart2" ></canvas>
      </div>
      <div id="bar-container">
        <canvas id="bar-chart"></canvas>
      </div>
    </div>
  </div>
 
</template>
<script>

import allRegions from '../assets/json/regions.js'
import region84 from '../assets/json/84.json'
import region27 from '../assets/json/27.json'
import region53 from '../assets/json/53.json'
import region24 from '../assets/json/24.json'
import region94 from '../assets/json/94.json'
import region44 from '../assets/json/44.json'
import region1 from '../assets/json/1.json'
import region3 from '../assets/json/3.json'
import region32 from '../assets/json/32.json'
import region11 from '../assets/json/11.json'
import region4 from '../assets/json/4.json'
import region2 from '../assets/json/2.json'
import region28 from '../assets/json/28.json'
import region75 from '../assets/json/75.json'
import region76 from '../assets/json/76.json'
import region52 from '../assets/json/52.json'
import region93 from '../assets/json/93.json'
import Chart from 'chart.js';
export default {
  name: 'menu',
  props: {
    
  },
  data() {
    
    return {
      allRegions
    }
  },
  
  methods: {
    showStats: function (regions) {
      if (regions.code == "84") {
        this.createDonutHomme(region84);
        this.createDonutfemme(region84);
        this.createbar(region84);
      }
      else if (regions.code == "27") {
        this.createDonutHomme(region27);
        this.createDonutfemme(region27);
        this.createbar(region27);
      }
       else if (regions.code == "53") {
        this.createDonutHomme(region53);
        this.createDonutfemme(region53);
        this.createbar(region53);
      }
       else if (regions.code == "24") {
        this.createDonutHomme(region24);
        this.createDonutfemme(region24);
        this.createbar(region24);
      }
       else if (regions.code == "94") {
        this.createDonutHomme(region94);
        this.createDonutfemme(region94);
        this.createbar(region94);
      }
       else if (regions.code == "44") {
        this.createDonutHomme(region44);
        this.createDonutfemme(region44);
        this.createbar(region44);
      }
       else if (regions.code == "1") {
        this.createDonutHomme(region1);
        this.createDonutfemme(region1);
        this.createbar(region1);
      }
       else if (regions.code == "3") {
        this.createDonutHomme(region3);
        this.createDonutfemme(region3);
        this.createbar(region3);
      }
       else if (regions.code == "32") {
        this.createDonutHomme(region32);
        this.createDonutfemme(region32);
        this.createbar(region32);
      }
       else if (regions.code == "11") {
        this.createDonutHomme(region11);
        this.createDonutfemme(region11);
        this.createbar(region11);
      }
       else if (regions.code == "4") {
        this.createDonutHomme(region4);
        this.createDonutfemme(region4);
        this.createbar(region4);
      }
       else if (regions.code == "2") {
        this.createDonutHomme(region2);
        this.createDonutfemme(region2);
        this.createbar(region2);
      }
       else if (regions.code == "28") {
        this.createDonutHomme(region28);
        this.createDonutfemme(region28);
        this.createbar(region28);
      }
       else if (regions.code == "75") {
        this.createDonutHomme(region75);
        this.createDonutfemme(region75);
        this.createbar(region75);
      }
       else if (regions.code == "76") {
        this.createDonutHomme(region76);
        this.createDonutfemme(region76);
        this.createbar(region76);
      }
       else if (regions.code == "52") {
        this.createDonutHomme(region52);
        this.createDonutfemme(region52);
        this.createbar(region52);
      }
       else if (regions.code == "93") {
        this.createDonutHomme(region93);
        this.createDonutfemme(region93);
        this.createbar(region93);
      }


    },
    createDonutHomme: function(data) {
      new Chart(document.getElementById("doughnut-chart"), {
      type: 'doughnut',
      data: {
        
        datasets: [
          {
            backgroundColor: ["#FFA500", "#D3D3D3"],
            data: [parseFloat(data.data_sexe.homme[0].content[0]).toFixed(2), 100 - parseFloat(data.data_sexe.homme[0].content[0]).toFixed(2)]
          }
        ],
        labels : [
          'hommes',
          'femmes',
        ]
      },
      options: {
        title: {
          display: true,
          text: 'Hommes',
          fontSize: 30
        },
        cutoutPercentage: 80,
        tooltips: {
          titleFontSize: 30,
          bodyFontSize: 30
        },
        legend: {
            display: false
        }
      }
      });
    },
    createDonutfemme: function(data) {
      new Chart(document.getElementById("doughnut-chart2"), {
    type: 'doughnut',
    data: {
      datasets: [
        {
          backgroundColor: ["#FFA500", "#D3D3D3"],
          data: [parseFloat(data.data_sexe.femme[0].content[0]).toFixed(2), 100 - parseFloat(data.data_sexe.femme[0].content[0]).toFixed(2)]
        }
      ],
      labels : [
        'femmes',
        'hommes'
      ]
    },
    options: {
      title: {
        display: true,
        text: 'Femmes',
        fontSize: 30
      },
      cutoutPercentage: 80,
      tooltips: {
        titleFontSize: 30,
        bodyFontSize: 30
      },
      legend: {
        display: false
      }

    }
});
  },
  createbar: function(data) {
      new Chart(document.getElementById("bar-chart"), {
        type: 'horizontalBar',
        data: {
          labels: [
            data.data_age[0].title, data.data_age[1].title, data.data_age[2].title, data.data_age[3].title
        ],
          datasets: [
            {
              backgroundColor: ["#FFA500", "#FFA500","#FFA500","#FFA500","#FFA500"],
              data: [data.data_age[0].content[0],  data.data_age[1].content[0], data.data_age[2].content[0],  data.data_age[3].content[0] ]
            }
          ]
        },
        options: {
                
                  scales: {
                    yAxes:[{
                        barThickness: 20,
                        ticks: {
                            beginAtZero:true,
                          mirror: true,
                          display: false
                        },
                        gridLines: {
                          color: "rgba(0, 0, 0, 0)",
                        }
                    }],
                    xAxes: [{
                      gridLines: {
                          color: "rgba(0, 0, 0, 0)",
                      }
                    }]
                  },
                  legend: {
                  display: false
                },
                
        }
    });
    
  }
  },
  created: function(){
    this.showStats(region1);
    }
  
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style>


.menu-container {
  background-color: #D3D3D3;
  width: 100%;
  display: flex;
  align-items: flex-end;
  justify-content: flex-end;
  height: 50px;
  position: absolute;
  top: 0;
}

li {
  display: none;
}

ul:hover > li {
    display: flex;
}

li:hover ~ li {
  display: flex;
}
li {
  list-style-type: none;
  margin: 15px 5px 15px 5px;
}

#menuTitle {
  margin: 15px 5px 15px 5px;
}

ul {
  background-color: #D3D3D3;
      padding: 0;
    margin: 0;
    list-style: none;
    position: absolute;
    width: 15%;
    right: 0;
    top: 0;
}

#doughnut-chart {
  background-image:url(../assets/manager.png);
  background-repeat: no-repeat;
  background-position-x: center;
  background-position-y: 60%;
  height: 234px!important;
  width: 470px!important;
}

#doughnut-chart2 {
  margin-top: 30px;
  background-image:url(../assets/woman.png);
  background-repeat: no-repeat;
  background-position-x: center;
  background-position-y: 60%;
  height: 234px!important;
  width: 470px!important;
}



nav {
  background-color: #D3D3D3;
}

#donut-container {
  width: 50%;
  display: flex;
  flex-direction: column;
}

#bar-container {
    width: 40%;
  display: flex;
  justify-content: center;
  align-items: center;
}

#chart-container {
  display: flex;
  margin-top: 20px;
}

.text {
  margin-top: 60px;
  margin-left: 40px;
}

.text-orange {
  color: #FFA500;
}

.text-grey {
  color: #D3D3D3;
}

.text-title {
  font-size: 18px;
}

</style>
