<template>
    <div class="card" style="width: 18rem;">
        <!-- <img class="card-img-top"> -->
        <div class="card-body">
            <h5 class="card-title">{{ nom }}</h5>
            <p class="card-text">{{ prix }} €</p>
            <a :href="site" target="_blank" class="btn btn-primary">Site</a>
            <hr />
            <button v-if="role == 'commander'" @click="$emit('commande', id, nom, prix, site)">Commander !</button>
            <button v-if="role == 'affichage'" @click="$emit('commande', id, nom, prix, site)">Supprimer</button>
        </div>
    </div>
</template>

<script>
export default {
    name: "Produit",
    props: ["id", "nom", "prix", "site", "role"]
}
</script>