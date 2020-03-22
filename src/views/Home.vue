<template>
  <v-container fluid>
    <v-row justify="center" align="center">
      <v-card class="transparent">
        <v-container fluid>
          <v-row>
            <v-col>
              <v-card class="mx-auto" width="400" height="100%" color="rgb(255,255,255,0.3)">
                <img src="@/assets/home/node_js.png" width="80%" />
                <v-card-text>
                  <p
                    style="font-size: 20px; font-weight: bold;"
                  >รับพัฒนา Website ด้วยเทคโนโลยี Node js</p>
                  <div class="text-start" style="font-size: 18px;">
                    <p>
                      <b>Frontend:</b> Vuejs
                      <v-icon right>fab fa-vuejs</v-icon>
                    </p>
                    <p>
                      <b>Backend:</b> Express,Django, Flask
                      <v-icon right>fas fa-server</v-icon>
                    </p>
                  </div>
                </v-card-text>
              </v-card>
            </v-col>
            <v-col>
              <v-card class="mx-auto" width="400" height="100%" color="rgb(255,255,255,0.3)">
                <img src="@/assets/home/electron.png" width="80%" />
                <v-card-text>
                  <p
                    style="font-size: 20px; font-weight: bold;"
                  >รับพัฒนา Desktop Application ด้วย Electron</p>
                </v-card-text>
              </v-card>
            </v-col>
            <v-col>
              <v-card class="mx-auto" width="400" height="100%" color="rgb(255,255,255,0.3)">
                <img src="@/assets/home/flutter.png" width="80%" />
                <v-card-text>
                  <p style="font-size: 20px; font-weight: bold;">รับพัฒนา Mobile App ด้วย Flutter</p>
                </v-card-text>
              </v-card>
            </v-col>
          </v-row>
        </v-container>
      </v-card>
    </v-row>
  </v-container>
</template>

<script>
export default {
  name: "Home"
};
</script>
