<template>

  <div class=" d-flex justify-center align-center" style="height:100vh;">
    <v-card class="mx-auto" width="500" style="background-color: rgba(250,0,0,0)">

      <div align="center" class="pa-5">
        <v-img src="logo.png" width="200">


        </v-img>
      </div>

      <div class="mx-6">
        <v-card-text>
          <v-row>
            <v-col cols="12" md="6">
              <v-btn block outlined>

                <v-icon color="red">
                  mdi-google
                </v-icon>
                google
              </v-btn>
            </v-col>



            <v-col cols="12" md="6">
              <v-btn block outlined>

                <v-icon color="blue">
                  mdi-facebook
                </v-icon>
                Facebook
              </v-btn>
            </v-col>
          </v-row>
        </v-card-text>


        <v-card-text>
          <v-form ref="form" v-model="valid" lazy-validation>
            <v-text-field outlined label="Email" prepend-inner-icon="mdi-email" :rules="emailRules" required>

            </v-text-field>
            <v-text-field outlined label="Password" prepend-inner-icon="mdi-lock " :rules="passRules" required>

            </v-text-field>
            <v-btn class="mx-auto" block color="blue" @click="sumbit" :disabled="!valid">
              Sign In
            </v-btn>




          </v-form>
        </v-card-text>
      </div>
    </v-card>
  </div>

</template>



<script>
export default {
  layout: "auth",
  data: () => ({
    valid: true,
    password: "",
    passRules: [(v) => !!v || "Password is required"],
    emailRules: [
    v => !!v || 'E-mail is required',
        v => /.+@.+\..+/.test(v) || 'E-mail must be valid',


    ],
  }),


  methods: {
    sumbit() {
      if (this.$refs.form.validate()) {
        console.log("Successfully Login");
        this.$router.push("/dashboard");
      }
    },

  },
}
</script>