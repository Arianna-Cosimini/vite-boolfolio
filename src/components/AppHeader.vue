<script>


export default {
    name: "AppHeader",



    data() {
        return {
            showNavbar: false,

        }
    },

    mounted() {
        // Mostra la navbar con un effetto slide-in dopo un breve ritardo
        setTimeout(() => {
            this.showNavbar = true;
        }, 100);
    },


}


</script>

<template>
    <div class="container py-5">

        <nav v-if="showNavbar" class="navbar navbar-expand-lg slide-in" style="z-index: 1;">
            <div class="container-fluid">
                <router-link :to="{ name: 'home'}" class="navbar-brand">
                    <h1 class="display-1 text-uppercase fw-bold">Boolfolio</h1>
                </router-link>

                <button class="navbar-toggler" type="button" data-bs-toggle="collapse"
                    data-bs-target="#navbarSupportedContent" aria-controls="navbarSupportedContent"
                    aria-expanded="false" aria-label="Toggle navigation">
                    <span class="navbar-toggler-icon"></span>
                </button>
                <div class="collapse navbar-collapse" id="navbarSupportedContent">
                    <ul class="navbar-nav me-auto mb-2 mb-lg-0">

                    </ul>

                    <ul class="d-flex list-unstyled gap-4">
                        <router-link :to="{ name: 'home' }"
                            class="link text-decoration-none fw-bold text-white">Home</router-link>

                        <router-link :to="{ name: 'about' }" class="link text-decoration-none fw-bold text-white">Chi
                            sono</router-link>

                        <router-link :to="{ name: 'app-projects'}"
                            class="text-decoration-none fw-bold text-white">I miei progetti</router-link>

                        <router-link :to="{ name: 'contacts'}"
                            class="text-decoration-none fw-bold text-white">Contatti</router-link>

                    </ul>

                </div>
            </div>
        </nav>
    </div>


</template>

<style lang="scss" scoped>
h1 {
    font-size: 50px;
    margin-bottom: 0;
    background-image: linear-gradient(to right, #699ffc, #bc38fe);
    /* Colore sfumato */
    -webkit-background-clip: text;
    /* Applico la sfumatura al testo */
    -webkit-text-fill-color: transparent;
    /* Nascondo il colore del testo */
}

.link{
    padding-bottom: 5px;
    &:hover{
        border-bottom: 2px solid #bc38fe;
        scale: 1.2;
    }
}

button {
    border: 1px solid #bc38fe;
    border-radius: 8px;
    background-color: transparent;
}

@keyframes slideIn {
    from {
        transform: translateY(-100%); // Inizia sopra la pagina
        opacity: 0;
    }

    to {
        transform: translateY(0); // Torna alla posizione originale
        opacity: 1;
    }
}

.navbar.slide-in {
    animation: slideIn 0.8s ease-in-out forwards; 
}
</style>