<template>
  <v-container fluid>
    <v-row>
      <v-col cols="12" offset-sm>
        <v-row justify="center" align="center" justify-sm="center">
          <v-card>
            <v-tabs
              v-model="tab"
              background-color="deep-purple accent-4"
              centered
              dark
              icons-and-text
              show-arrows
            >
              <v-tabs-slider></v-tabs-slider>

              <v-tab @click="page = 'situation'">
                สถานะการณ์ปัจจุบัน
                <v-icon>mdi-clock</v-icon>
              </v-tab>

              <v-tab @click="page = 'prevent'">
                วิธีป้องกันเบื้องต้น
                <v-icon>mdi-heart</v-icon>
              </v-tab>

              <v-tab @click="page = 'sympotoms'">
                อาการเบื้องต้น
                <v-icon>fas fa-temperature-high</v-icon>
              </v-tab>
            </v-tabs>
          </v-card>
        </v-row>
      </v-col>
      <situation v-if="page == 'situation'"></situation>
      <sympotoms v-if="page == 'sympotoms'"></sympotoms>
      <prevent v-if="page == 'prevent'"></prevent>
    </v-row>
  </v-container>
</template>

<script>
import situation from "@/components/covid/covidSituation";
import sympotoms from "@/components/covid/covidSymptoms";
import prevent from "@/components/covid/covidPrevent";

export default {
  name: "Covid",
  components: {
    situation,
    sympotoms,
    prevent
  },
  data() {
    return {
      page: "situation"
    };
  },
  methods: {}
  //   created() {
  //     this.axios({
  //       method: "GET",
  //       url:
  //         "https://coronavirus-monitor.p.rapidapi.com/coronavirus/worldstat.php",
  //       headers: {
  //         "content-type": "application/octet-stream",
  //         "x-rapidapi-host": "coronavirus-monitor.p.rapidapi.com",
  //         "x-rapidapi-key": "ff9a19b384msh842596e9e359bdep1b6fd3jsn5be29a7b5ac5"
  //       }
  //     })
  //       .then(response => {
  //         console.log(response);
  //       })
  //       .catch(error => {
  //         console.log(error);
  //       });
  //   }
};
</script>

<style></style>
