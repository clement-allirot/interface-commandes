<template>
    <div>
        <h1 class="display-2">Commandes</h1>

        <hr />
        <div class="row">
            <div class="col-md-6">
                <h2>Produits disponibles</h2>
                <br/>
                <div v-if="!produits.length">Aucun produit disponible ...</div>
                <div class="card-deck">
                    <Produit v-for="produit in produits" :key="produit.id" :id="produit.id" :nom="produit.nom"
                        :prix="produit.prix" :site="produit.site" role="commander" v-on:commande="ajouterProduit" />
                </div>
            </div>
            <div class="col-md-6">
                <h2>Produits commandés</h2>
                <br/>
                <div v-if="!commandes.length">Aucune commande ...</div>
                <div class="card-deck">
                    <Produit v-for="commande in commandes" :key="commande.id" :id="commande.id" :nom="commande.nom"
                        :prix="commande.prix" :site="commande.site" v-on:commande="supprimerProduit" role="affichage" />
                </div>
            </div>
        </div>

    </div>
</template>

<script>
import Produit from '@/components/Produit.vue'
export default {
    components: {
        Produit
    },
    data() {
        return {
            produits: [
                { id: 1, nom: 'Pizza', prix: 3.0, site: 'https://www.dominos.fr/' },
                { id: 2, nom: 'Frites', prix: 2.0, site: 'https://www.achat-vente-frites.com/' },
            ],
            commandes: [
                { id: 3, nom: 'Hamburger', prix: 2.5, site: 'https://speed-burger.com/' },
                { id: 4, nom: 'Cheeseburger', prix: 3.0, site: 'https://www.cheezburger.com/' },
            ]
        }
    },
    methods: {
        ajouterProduit(id, nom, prix, site) {
            this.spliceIndex(this.produits, id);
            this.commandes.push({ id: id, nom: nom, prix: prix, site: site });
        },
        supprimerProduit(id, nom, prix, site) {
            this.spliceIndex(this.commandes, id);
            this.produits.push({ id: id, nom: nom, prix: prix, site: site });
        },

        spliceIndex(arr, id) {
            const index = arr.findIndex(obj => obj.id === id);
            if (index !== -1) {
                arr.splice(index, 1);
            }
        }
    }
}
</script>

<style scoped></style>