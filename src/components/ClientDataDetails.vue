<template>
  <div class="text-center">
    <v-dialog
      v-model="openDialog"
      width="500"
    >

      <v-card>
        <v-card-title class="text-h5 grey lighten-2">
          Wiadomosc
        </v-card-title>

        <v-card-text class="text-center">
          <b style="font-size: 20px;">Tresc:</b>
          <p style="color: red;">To jest wiadomosc testowa</p>
          <p style="color: rgb(0, 190, 250);">To jest koniec wiadomosci</p>
        </v-card-text>

        <v-divider></v-divider>

        <v-card-actions>
          <v-spacer></v-spacer>
          <v-btn
            color="primary"
            text
            @click="openDialog = false"
          >
            Akceptuj
          </v-btn>
        </v-card-actions>
      </v-card>
    </v-dialog>
  </div>
</template>

<script>
  export default {
    props: {
        value: {
            type: Boolean,
            default: null
        }
    },
    mounted() {
        console.log("mounted component")
        this.openDialog = this.value
    },
    data () {
      return {
        openDialog: false,
      }
    },
    watch: {
        value() {
            console.log("zmiana dialog", this.value);
            this.openDialog = this.value;
        },
        openDialog() {
            this.$emit('input', this.openDialog)
        }
    },
    method: {
        open() {
            this.openDialog = true;
        }
    }
  }
</script>