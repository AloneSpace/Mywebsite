<template>
  <v-container fluid>
    <v-row justify="center" align="center">
      <v-card color="rgb(255,255,255,0.5)" width="1024">
        <v-container fluid>
          <v-row align="center" justify="center" style="padding-bottom: 10px;">
            <div class="text-center">
              <v-card-title>
                <h2>AloneCoding's Team</h2>
              </v-card-title>
            </div>
          </v-row>
          <v-row>
            <v-col>
              <img
                src="@/assets/profile/jomPic.jpg"
                width="256"
                height="256"
                style="border-radius: 50%"
              />
            </v-col>
            <v-col>
              <v-list disabled color="transparent">
                <v-list-item-group v-model="item" color="primary">
                  <v-list-item v-for="(item, i) in jom" :key="i">
                    <v-list-item-icon>
                      <v-icon v-text="item.icon"></v-icon>
                    </v-list-item-icon>
                    <v-list-item-content>
                      <div class="text-start">
                        <v-list-item-title style="font-size: 18px;">
                          <p class="text-start text-wrap">
                            <b>{{ item.text }}</b>
                            {{ item.data}}
                          </p>
                        </v-list-item-title>
                      </div>
                    </v-list-item-content>
                  </v-list-item>
                </v-list-item-group>
              </v-list>
            </v-col>
          </v-row>
          <v-row align="center" justify="center">
            <img
              src="@/assets/skills/jom.png"
              width="90%"
              height="auto"
              style="padding-bottom: 10px;"
            />
          </v-row>
          <v-divider style="padding-bottom: 10px; "></v-divider>
          <v-row>
            <v-col cols="3.1">
              <img
                src="@/assets/profile/kan.png"
                width="256"
                height="256"
                style="border-radius: 50%"
              />
            </v-col>
            <v-col>
              <v-list disabled color="transparent">
                <v-list-item-group v-model="item" color="primary">
                  <v-list-item v-for="(item, i) in kan" :key="i">
                    <v-list-item-icon>
                      <v-icon v-text="item.icon"></v-icon>
                    </v-list-item-icon>
                    <v-list-item-content>
                      <div class="text-start">
                        <v-list-item-title style="font-size: 18px;">
                          <p class="text-start text-wrap">
                            <b>{{ item.text }}</b>
                            {{ item.data}}
                          </p>
                        </v-list-item-title>
                      </div>
                    </v-list-item-content>
                  </v-list-item>
                </v-list-item-group>
              </v-list>
            </v-col>
            <v-row align="center" justify="center">
              <img
                src="@/assets/skills/kan.png"
                width="90%"
                height="auto"
                style="padding-bottom: 10px;"
              />
            </v-row>
          </v-row>
        </v-container>
      </v-card>
    </v-row>
  </v-container>
</template>

<script>
export default {
  data: () => ({
    jom: [
      {
        text: "ชื่อ-นามสกุล:",
        data: "นาย กรัณย์ภัทร พรหมวิสุทธิ์",
        icon: "fas fa-id-card m-r-10"
      },
      {
        text: "ว/ด/ป เกิด:",
        data: "5 มกราคม 2545 (18 ปี)",
        icon: "fas fa-baby m-r-10"
      },
      {
        text: "สถานศึกษา:",
        data: "มัธยมศึกษาปีที่ 6 แผนการเรียน วิทย์-คณิต โรงเรียนฤทธิยะวรรณาลัย",
        icon: "fas fa-graduation-cap m-r-10"
      },
      {
        text: "ความใฝ่ฝัน:",
        data:
          "อยากทำงานกับบริษัทชั้นนำ หรือใน Silicon valley ด้าน Machine Learning",
        icon: "fas fa-laptop-code m-r-10"
      },
      {
        text: "งานอดิเรก",
        icon: "fas fa-play m-r-10"
      },
      {
        text: "-",
        data: "ศึกษาและอ่าน Document เกี่ยวกับ IT ที่สนใจ"
      },
      {
        text: "-",
        data: "ดูสารคดีสัตว์โลก และดาราศาสตร์"
      },
      {
        text: "-",
        data: "ออกกำลังกาย"
      }
    ],
    kan: [
      {
        text: "ชื่อ-นามสกุล:",
        data: "นาย นนทกร อินทอง",
        icon: "fas fa-id-card m-r-10"
      },
      {
        text: "ว/ด/ป เกิด:",
        data: "6 พฤษภาคม 2545 (17 ปี)",
        icon: "fas fa-baby m-r-10"
      },
      {
        text: "สถานศึกษา:",
        data: "มัธยมศึกษาปีที่ 6 แผนการเรียน Gifted โรงเรียนฤทธิยะวรรณาลัย",
        icon: "fas fa-graduation-cap m-r-10"
      },
      {
        text: "ความใฝ่ฝัน:",
        data: "สนใจ Graphic และการเขียนโปรแกรมมาประยุกต์ใช้ในเทคโนโลยีใหม่",
        icon: "fas fa-laptop-code m-r-10"
      },
      {
        text: "งานอดิเรก",
        icon: "fas fa-play m-r-10"
      },
      {
        text: "-",
        data: "ทำกราฟิค และศึกษา UX/UI Design"
      },
      {
        text: "-",
        data: "ฝึกเขียนโปรแกรม"
      },
      {
        text: "-",
        data: "ตัดต่อ Video"
      }
    ]
  })
};
</script>

<style>
.wrap-text {
  -webkit-line-clamp: unset !important;
}
</style>
