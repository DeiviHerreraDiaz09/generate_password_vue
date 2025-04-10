<template>
    <div class="card">
        <section class="gif">
            <img :src="gif" alt="Wake Up GIF" />
        </section>
        <div class="cardForm">
            <form class="form" @submit.prevent="generatePassword">
                <p>Welcome to</p>
                <h2>Fedora</h2>
                <p>SUPER-secure password generator</p>
                <input type="text" v-model="password" readonly @click="copyToClipboard">
                <button class="generateButton" type="submit">Generar</button>
                <p class="profile">
                    Do you like it?
                    <a href="https://github.com/DeiviHerreraDiaz09" target="_blank"
                        style="text-decoration: none; color: #65C09D;">Visit my profile</a>
                </p>
            </form>
        </div>
    </div>
</template>

<script>
import Gif from "@/assets/wakeUp.gif";
export default {
    name: "Card",
    data() {
        return {
            gif: Gif,
            password: "",
            passwords: ["123", "contraseñasegura", "password", "abcd1234", "qwerty", "letmein", "12345678", "password1", "123456789", "1234567"],
        };
    },
    methods: {
        generatePassword() {
            const randomIndex = Math.floor(Math.random() * this.passwords.length);
            this.password = this.passwords[randomIndex];
        },
        copyToClipboard() {
            if (this.password) {
                navigator.clipboard.writeText(this.password)
                    .then(() => {
                        this.$emit('password-copied'); 
                    })
                    .catch(err => {
                        console.error("Error al copiar la contraseña: ", err);
                    });
            } else {
                alert("No hay contraseña para copiar.");
            }
        },
    },
};

</script>

<style>
.card {
    border-radius: 15px;
    background-color: white;
    box-shadow: 0 4px 6px rgba(0, 0, 0, 0.1);
    grid-column: 5/9;
    grid-row: 2/17;
    position: relative;
    display: flex;
    justify-content: center;
}

.gif {
    background-color: rgb(18, 72, 26);
    width: 100%;
    height: 60%;
    border-top-left-radius: 15px;
    border-top-right-radius: 15px;
}

.gif img {
    width: 100%;
    height: 100%;
    border-top-left-radius: 15px;
    border-top-right-radius: 15px;
    object-fit: cover;
}

.cardForm {
    position: absolute;
    width: 85%;
    border-radius: 15px;
    height: 50%;
    z-index: 5;
    background-color: white;
    box-shadow: 0px 9px 16px -8px rgba(0, 0, 0, 0.75);
    top: 45%;
}

.form {
    width: 100%;
    height: 100%;
    display: flex;
    gap: 10px;
    flex-direction: column;
    align-items: center;
    justify-content: center;
    color: #788AA4;
    font-family: var(--font-Kdam);
}

h2 {
    font-size: 2.5em;
}

input {
    width: 80%;
    height: 3em;
    border-radius: 15px;
    border: none;
    background-color: #D9D9D9;
    outline: none;
    padding: 2%;
    color: #788AA4;
}

.generateButton {
    width: 80%;
    height: 3em;
    border-radius: 15px;
    background-color: #65C09D;
    color: white;
    border: none;
    font-weight: bold;
    font-family: var(--font-Kdam);
}

.profile {
    font-weight: bold;
    cursor: pointer;
    font-size: 0.8em;
}
</style>