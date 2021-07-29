<template>
  <ion-page>
    <ion-header :translucent="true">
      <ion-toolbar>
        <ion-title>Blank</ion-title>
      </ion-toolbar>
    </ion-header>

    <ion-content :fullscreen="true">
      <ion-header collapse="condense">
        <ion-toolbar>
          <ion-title size="large">Blank</ion-title>
        </ion-toolbar>
      </ion-header>

<!--      <div id="container">-->
      <div style="margin-top: 50px">
        <ion-item>
          <ion-textarea
                  ref="target"
                  v-show="show"
                  :autoGrow="true"
                  v-model="data"
                  inputmode="text"
                  :rows="1"
                  @ionBlur="onBlur"
          ></ion-textarea>
            <span v-show="!show" @click="show = true">{{ data }}</span>
        </ion-item>
      </div>
<!--      </div>-->
    </ion-content>
  </ion-page>
</template>

<script lang="ts">
import { IonContent, IonHeader, IonPage, IonTitle, IonToolbar, IonItem, IonTextarea } from '@ionic/vue';
import { defineComponent, ref, watch } from 'vue';

export default defineComponent({
  name: 'Home',
  components: {
    IonContent,
    IonHeader,
    IonPage,
    IonTitle,
    IonToolbar,
    IonItem,
    IonTextarea
  },
  setup() {
    const data = ref('Test value');
    const show = ref(false);
    const target= ref();

    function onBlur() {
      show.value = false;
    }

    watch(show, () => {
      setTimeout(() => {
        show.value ? target.value.$el.children[0].children[0].focus() : '';
      }, 50);

    });

    return {data, show, onBlur, target};
  }
});
</script>

<style scoped>
#container {
  text-align: center;

  position: absolute;
  left: 0;
  right: 0;
  top: 50%;
  transform: translateY(-50%);
}

#container strong {
  font-size: 20px;
  line-height: 26px;
}

#container p {
  font-size: 16px;
  line-height: 22px;

  color: #8c8c8c;

  margin: 0;
}

#container a {
  text-decoration: none;
}

.sc-ion-textarea-md-h {
  font-family: unset;
  margin-top: 0px;
  --padding-top: 0px;
  --padding-bottom: 0px;
  --padding-start: 0px;
}

.sc-ion-textarea-ios-h {
  font-family: unset;
  --padding-top: 0px;
  --padding-bottom: 0px;
  --padding-end: 0px;
}
</style>
