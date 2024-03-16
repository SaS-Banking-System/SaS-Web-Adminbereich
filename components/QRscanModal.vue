<script setup lang="ts">
const props = defineProps(["show"]);
const emit = defineEmits(["close", "sendUUID"]);

import { QrcodeStream } from "vue-qrcode-reader";

let scannedUUID = ref<string>("");

function onDetect(detected: string) {
  const code = (detected[0] as any).rawValue;

  scannedUUID.value = code;
  emit("sendUUID", scannedUUID.value);
  emit("close");
}

function handleClose() {
  emit("close");
}
</script>

<template>
  <Transition name="modal">
    <div v-if="props.show" class="wrapper">
      <div class="modal-container">
        <div class="modal-info-header">
          <p>Kontenkarte scannen</p>
        </div>
        <div class="modal-info-body">
          <p>Bitte Kontenkarte mit QR-Code vor die Kamera halten. </p>
        </div>
        <div class="qr-reader-wrapper">
          <qrcode-stream @detect="onDetect"></qrcode-stream>
        </div>
        <div class="modal-info-footer">
          <button class="cancel" @click="handleClose" type="button">Abbrechen</button>
        </div>
      </div>
    </div>
  </Transition>
</template>

<style scoped>

.modal-enter-from {
  opacity: 0;
}

.modal-leave-to {
  opacity: 0;
}

.modal-enter-from .modal-container,
.modal-leave-to .modal-container {
  -webkit-transform: scale(1.1);
  transform: scale(1.1);
}

.wrapper {
  position: fixed;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  background-color: rgba(0, 0, 0, 0.5);
  display: flex;
  transition: opacity 0.3s ease;
}

.modal-container {
  width: 40vw;
  height: 65vh;
  margin: auto;
  padding: 10px 30px;

  border-radius: 10px;
  background-color: white;
  box-shadow: 0 0px 10px rgba(0, 0, 0, 0.8);
  transition: all 0.3s ease;
}

.modal-info-header {
  display: flex;
  justify-content: center;
}

.modal-info-header > p {
  font-size: 2.5rem;
  font-weight: 700;
}

.modal-info-body {
  display: flex;
  justify-content: center;
}

.modal-info-body > p {
  font-size: 1.5rem;
}

.modal-info-footer {
  margin-top: 10vh;
}

.qr-reader-wrapper {
  display: flex;
  flex-direction: center;
  justify-content: center;
  margin-top: 5vh;
  margin-left: 25%;
  width: 50%;
}

.cancel {
  all: unset;
  font-size: 1.2rem;
  font-weight: 500;
  font-family: "Segoe UI", Tahoma, Geneva, Verdana, sans-serif;
  border-radius: 10px;
  padding: 10px;
  border: 2px solid black;
  color: black;
  float: right;
}

p {
  font-weight: 500;
  font-family: "Segoe UI", Tahoma, Geneva, Verdana, sans-serif;
}

.cancel:hover {
  background-color: rgb(241, 241, 241);
  color: rgb(41, 41, 41);
  cursor: pointer;
}

</style>