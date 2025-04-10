<template>
  <div class="notification-container" :class="type">
    <div class="notification-content">
      <div class="notification-icon">
        <svg aria-hidden="true" fill="none" viewBox="0 0 24 24">
          <path
            stroke="currentColor"
            stroke-linecap="round"
            stroke-linejoin="round"
            stroke-width="2"
            :d="iconPath"
          ></path>
        </svg>
      </div>
      <div class="notification-text">{{ message }}</div>
    </div>
    <div class="notification-progress-bar"></div>
  </div>
</template>

<script>
export default {
  name: "Notification",
  props: {
    type: {
      type: String,
      required: true,
    },
    message: {
      type: String,
      required: true,
    },
    iconPath: {
      type: String,
      required: true,
    },
  },
};
</script>

<style scoped>
.notification-container {
    grid-column: 2 / 4;
    grid-row: 2;
    position: relative;
    background-color: #7dffbc;
    color: #047857;
    padding: 10px 15px;
    border-radius: 6px;
    box-shadow: rgba(111, 111, 111, 0.2) 0px 8px 24px;
    font-family: sans-serif;
    font-size: 0.9em;
}

.notification-container.success {
    background-color: #ffffff;
    color: #047857;
}

.notification-content {
    display: flex;
    align-items: center;
    gap: 10px;
}

.notification-icon svg {
    width: 1.5em;
    height: 1.5em;
}

.notification-text {
    font-weight: bold;
}

.notification-progress-bar {
    position: absolute;
    bottom: 0;
    left: 0;
    height: 4px;
    background-color: #047857;
    width: 100%;
    animation: progressBar 3s linear forwards; 
}

@keyframes progressBar {
    from {
        width: 100%;
    }
    to {
        width: 0;
    }
}
</style>
