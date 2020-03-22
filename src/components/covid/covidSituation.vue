<template>
  <v-container fluid>
    <v-row justify="center" align="center" class="d-none d-sm-flex">
      <v-card width="80%" height="auto" color="rgba(255, 255, 255, 0.1)" shaped>
        <v-row justify="center" align="center" style="padding-top: 40px;">
          <v-card color="transparent">
            <v-tabs background-color="transparent">
              <v-tab @click="situation='world'">
                <v-icon left>fas fa-globe-asia</v-icon>ทั่วโลก
              </v-tab>

              <v-tab @click="situation = 'thai'">
                <img src="https://www.countryflags.io/th/flat/32.png" style="padding-right: 5px;" />ประเทศไทย
              </v-tab>
            </v-tabs>
          </v-card>
        </v-row>
        <v-row v-if="situation == 'world'">
          <v-col>
            <h1 style="padding-top: 30px;">
              ยอดผู้ติดเชื้อทั้งหมด (Total Cases)
              <h2>
                <img
                  src="@/assets/icons/COVID_19/Coronavirus 2/PNG/64/5879324 - avatar coronavirus covid19 man mask person wearing.png"
                />
                {{ covid.total_cases }}
                <img
                  src="@/assets/icons/COVID_19/Coronavirus 2/PNG/64/5879325 - avatar coronavirus covid19 mask user wearing woman.png"
                />
              </h2>
            </h1>
            <v-row align="center" justify="center">
              <v-list color="transparent" width="600">
                <v-list-item>
                  <v-list-item-icon>
                    <img
                      src="@/assets/icons/COVID_19/Covid 19/PNG/48/5929228 - death grave halloween rip.png"
                      style="padding-right: 10px;"
                    />
                  </v-list-item-icon>
                  <v-list-item-content>
                    <v-list-item-title>
                      <h2>ผู้เสียชีวิตทั้งหมด</h2>
                    </v-list-item-title>
                    <v-list-item-subtitle>
                      <h3>Total Deaths</h3>
                    </v-list-item-subtitle>
                  </v-list-item-content>
                  <v-spacer></v-spacer>
                  <v-list-item-content>
                    <v-btn x-large rounded color="error">{{ covid.total_deaths }}</v-btn>
                  </v-list-item-content>
                </v-list-item>
                <!-- รักษาหาย -->
                <v-list-item>
                  <v-list-item-icon>
                    <img
                      src="@/assets/icons/COVID_19/Covid 19/PNG/48/5929232 - avatar face man mask sick.png"
                      style="padding-right: 10px;"
                    />
                  </v-list-item-icon>
                  <v-list-item-content>
                    <v-list-item-title>
                      <h2>ผู้ป่วยที่รักษาหาย</h2>
                    </v-list-item-title>
                    <v-list-item-subtitle>
                      <h3>Total Recovered</h3>
                    </v-list-item-subtitle>
                  </v-list-item-content>
                  <v-spacer></v-spacer>
                  <v-list-item-content>
                    <v-btn x-large rounded color="success">
                      {{
                      covid.total_recovered
                      }}
                    </v-btn>
                  </v-list-item-content>
                </v-list-item>
                <v-list-item>
                  <v-list-item-icon>
                    <img
                      src="@/assets/icons/COVID_19/Coronavirus/PNG/48/5859223 - checklist clipboard healthcare medical report.png"
                      style="padding-right: 10px;"
                    />
                  </v-list-item-icon>
                  <v-list-item-content>
                    <v-list-item-title>
                      <h2>ผู้ป่วยรายใหม่</h2>
                    </v-list-item-title>
                    <v-list-item-subtitle>
                      <h3>New Cases</h3>
                    </v-list-item-subtitle>
                  </v-list-item-content>
                  <v-spacer></v-spacer>
                  <v-list-item-content>
                    <v-btn x-large rounded color="warning">{{ covid.new_cases }}</v-btn>
                  </v-list-item-content>
                </v-list-item>
                <v-list-item>
                  <v-list-item-icon>
                    <v-icon
                      style="font-size: 3em; color: rgb(255, 0, 0, 0.5); padding-right: 10px;"
                    >fas fa-skull-crossbones</v-icon>
                  </v-list-item-icon>
                  <v-list-item-content>
                    <v-list-item-title>
                      <h2>ผู้เสียชีวิตรายใหม่</h2>
                    </v-list-item-title>
                    <v-list-item-subtitle>
                      <h3>New Deaths</h3>
                    </v-list-item-subtitle>
                  </v-list-item-content>
                  <v-spacer></v-spacer>
                  <v-list-item-content>
                    <v-btn x-large rounded color="error">{{ covid.new_deaths }}</v-btn>
                  </v-list-item-content>
                </v-list-item>
              </v-list>
            </v-row>
          </v-col>
          <v-col style="padding-top: 30px; padding-right: 30px; padding-left: 30px;">
            <v-card style="background-color: rgb(255,255,255,0.5);">
              <v-card-title>
                ข้อมูล ณ วันที่ {{ statistic_taken_at }}
                <v-spacer></v-spacer>
                <v-text-field
                  v-model="search"
                  append-icon="mdi-magnify"
                  label="ค้นหาข้อมูล"
                  single-line
                  hide-details
                ></v-text-field>
              </v-card-title>
              <v-data-table
                class="elevation-1"
                :loading="loading"
                :search="search"
                :headers="headers"
                :items="data"
              ></v-data-table>
            </v-card>
          </v-col>
        </v-row>
        <v-row v-else>
          <v-container>
            <v-row>
              <v-col>
                <h1 style="padding-top: 30px;">
                  ยอดผู้ติดเชื้อทั้งหมดในประเทศไทย (Total Cases)
                  <h2>
                    <img
                      src="@/assets/icons/COVID_19/Coronavirus 2/PNG/64/5879324 - avatar coronavirus covid19 man mask person wearing.png"
                    />
                    {{ thailand.cases }}
                    <img
                      src="@/assets/icons/COVID_19/Coronavirus 2/PNG/64/5879325 - avatar coronavirus covid19 mask user wearing woman.png"
                    />
                  </h2>
                </h1>
              </v-col>
            </v-row>
            <v-row>
              <v-col>
                <img
                  src="@/assets/icons/COVID_19/Coronavirus Flat/PNG/48/5728195 - building healthcare hospital medical nursing.png"
                />
                <h2>ผู้ป่วยที่กำลังรักษาอยู่</h2>
                <h2>{{ thailand.active_cases }}</h2>
              </v-col>
              <v-col>
                <img
                  src="@/assets/icons/COVID_19/Covid 19/PNG/48/5929232 - avatar face man mask sick.png"
                />
                <h2>ผู้ป่วยที่รักษาหาย</h2>
                <h2>{{ thailand.total_recovered }}</h2>
              </v-col>
              <v-col>
                <img
                  src="@/assets/icons/COVID_19/Coronavirus/PNG/48/5859223 - checklist clipboard healthcare medical report.png"
                />
                <h2>ผู้ป่วยรายใหม่</h2>
                <h2>{{ thailand.new_cases }}</h2>
              </v-col>
              <v-col>
                <img
                  src="@/assets/icons/COVID_19/Covid 19/PNG/48/5929228 - death grave halloween rip.png"
                />
                <!-- <v-icon
                  style="font-size: 3em; color: rgb(255, 0, 0, 0.5); padding-bottom: 5px;"
                >fas fa-skull-crossbones</v-icon>-->
                <h2>ผู้เสียชีวิตทั้งหมด</h2>
                <h2>{{ thailand.deaths }}</h2>
              </v-col>
            </v-row>
          </v-container>
        </v-row>
      </v-card>
    </v-row>
    <v-row justify="center" align="center" class="d-lg-none d-md-none d-sm-none">
      <v-row justify="center" align="center">
        <v-card color="transparent">
          <v-tabs background-color="transparent">
            <v-tab @click="situationMB='world'">
              <v-icon left>fas fa-globe-asia</v-icon>สถานการณ์
            </v-tab>

            <v-tab @click="situationMB = 'datatable'">
              <img src="https://www.countryflags.io/th/flat/32.png" style="padding-right: 5px;" />ตาราง
            </v-tab>
          </v-tabs>
        </v-card>
      </v-row>

      <v-row
        justify="center"
        align="center"
        style="padding-top: 20px;"
        v-if="situationMB == 'datatable'"
      >
        <v-card style="background-color: rgb(255,255,255,0.5);">
          <v-card-title style="background-color: rgb(255,255,255,0.5);">
            ข้อมูล ณ วันที่ {{ statistic_taken_at }}
            <v-spacer></v-spacer>
            <v-text-field
              v-model="search"
              append-icon="mdi-magnify"
              label="ค้นหาข้อมูล"
              single-line
              hide-details
              style="background-color: rgb(255,255,255,0.5);"
            ></v-text-field>
          </v-card-title>
          <v-data-table
            item-key="name"
            class="elevation-1"
            :search="search"
            :headers="headers"
            :items="data"
            style="background-color: rgb(255,255,255,0.5);"
          ></v-data-table>
        </v-card>
      </v-row>

      <v-row
        justify="center"
        align="center"
        style="padding-top: 20px;"
        v-if="situationMB == 'world'"
      >
        <v-card width="350">
          <h3>ยอดผู้ติดเชื้อทั้งหมด (Total Cases)</h3>
          <h3>
            <img
              src="@/assets/icons/COVID_19/Coronavirus 2/PNG/32/5879324 - avatar coronavirus covid19 man mask person wearing.png"
            />
            {{ covid.total_cases }}
            <img
              src="@/assets/icons/COVID_19/Coronavirus 2/PNG/32/5879325 - avatar coronavirus covid19 mask user wearing woman.png"
            />
          </h3>
        </v-card>
      </v-row>
      <v-row
        justify="center"
        align="center"
        style="padding-top: 20px;"
        v-if="situationMB == 'world'"
      >
        <v-card width="350">
          <v-row>
            <v-col></v-col>
            <v-col>
              <v-chip label color="transparent">
                <v-icon left>fas fa-globe-asia</v-icon>ทัวโลก
              </v-chip>
            </v-col>
            <v-col>
              <div class="text-center">
                <v-chip label color="transparent">
                  <img src="https://www.countryflags.io/th/flat/32.png" style="padding-right: 5px;" />ประเทศไทย
                </v-chip>
              </div>
            </v-col>
          </v-row>
          <v-row>
            <v-col>ผู้ป่วยทั้งหมด</v-col>
            <v-col>{{ covid.total_cases }}</v-col>
            <v-col>{{ thailand.cases }}</v-col>
          </v-row>
          <v-row>
            <v-col>ผู้ป่วยรักษาหาย</v-col>
            <v-col>{{ covid.total_recovered }}</v-col>
            <v-col>{{ thailand.total_recovered }}</v-col>
          </v-row>
          <v-row>
            <v-col>ผู้ป่วยรายใหม่</v-col>
            <v-col>{{ covid.new_cases }}</v-col>
            <v-col>{{ thailand.new_cases }}</v-col>
          </v-row>
          <v-row>
            <v-col>ผู้เสียชีวิต</v-col>
            <v-col>{{ covid.total_deaths }}</v-col>
            <v-col>{{ thailand.deaths }}</v-col>
          </v-row>
        </v-card>
      </v-row>
    </v-row>
  </v-container>
</template>

<script>
export default {
  name: "covidSituation",
  data: () => ({
    knowledge: 30,
    search: "",
    statistic_taken_at: "",
    loading: true,
    thailand: {
      cases: null,
      active_cases: null,
      total_recovered: null,
      new_cases: null,
      deaths: null
    },
    headers: [
      {
        text: "ประเทศ",
        align: "start",
        value: "country_name"
      },
      { text: "ผู้ป่วยทั้งหมด", value: "cases" },
      { text: "ผู้ป่วยที่กำลังรักษา", value: "active_cases" },
      { text: "ผู้ป่วยที่หายดีแล้ว", value: "total_recovered" },
      { text: "ผู้ป่วยที่เสียชีวิตทั้งหมด", value: "deaths" }
    ],
    data: [],
    situation: "world",
    situationMB: "world",
    covid: {
      total_cases: null,
      total_deaths: null,
      total_recovered: null,
      active_cases: null,
      new_cases: null,
      new_deaths: null
    }
  }),
  created() {
    this.axios({
      method: "GET",
      url:
        "https://coronavirus-monitor.p.rapidapi.com/coronavirus/worldstat.php",
      headers: {
        "content-type": "application/octet-stream",
        "x-rapidapi-host": "coronavirus-monitor.p.rapidapi.com",
        "x-rapidapi-key": "ff9a19b384msh842596e9e359bdep1b6fd3jsn5be29a7b5ac5"
      }
    })
      .then(response => {
        this.covid.total_cases = response.data.total_cases;
        this.covid.total_deaths = response.data.total_deaths;
        this.covid.total_recovered = response.data.total_recovered;
        this.covid.active_cases = response.data.active_cases;
        this.covid.new_cases = response.data.new_cases;
        this.covid.new_deaths = response.data.new_deaths;
        this.loading = false;
      })
      .catch(error => {
        console.log(error);
      });
    this.axios({
      method: "GET",
      url:
        "https://coronavirus-monitor.p.rapidapi.com/coronavirus/cases_by_country.php",
      headers: {
        "content-type": "application/octet-stream",
        "x-rapidapi-host": "coronavirus-monitor.p.rapidapi.com",
        "x-rapidapi-key": "ff9a19b384msh842596e9e359bdep1b6fd3jsn5be29a7b5ac5"
      }
    })
      .then(response => {
        response.data.countries_stat.forEach(element => {
          if (element.country_name == "Thailand") {
            this.thailand.cases = element.cases;
            this.thailand.active_cases = element.active_cases;
            this.thailand.new_cases = element.new_cases;
            this.thailand.total_recovered = element.total_recovered;
            this.thailand.deaths = element.deaths;
          }
          this.data.push({
            country_name: element.country_name,
            cases: element.cases,
            active_cases: element.active_cases,
            total_recovered: element.total_recovered,
            deaths: element.deaths
          });
        });
        this.statistic_taken_at = response.data.statistic_taken_at;
      })
      .catch(error => {
        console.log(error);
      });
  }
};
</script>

<style></style>
