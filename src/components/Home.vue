<template id="home">
    <Card @password-copied="showNotification" />
    <Notification 
        v-if="notificationVisible" 
        type="success" 
        message="Contraseña copiada correctamente!" 
        iconPath="M8.5 11.5 11 14l4-4m6 2a9 9 0 1 1-18 0 9 9 0 0 1 18 0Z" 
    />
</template>

<script>
import Card from "@/components/Card.vue";
import Notification from "@/components/Notification.vue";

export default {
    name: "Home",
    components: {
        Card,
        Notification
    },
    data() {
        return {
            notificationVisible: false, 
        };
    },
    methods: {
        showNotification() {
            this.notificationVisible = true;
            setTimeout(() => {
                this.notificationVisible = false; 
            }, 3000);
        },
    },
};
</script>

<style>
</style>