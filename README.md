## Hi there 👋

<!--
**C-TX28/C-TX28** is a ✨ _special_ ✨ repository because its `README.md` (this file) appears on your GitHub profile.

Here are some ideas to get you started:

- 🔭 I’m currently working on ...
- 🌱 I’m currently learning ...
- 👯 I’m looking to collaborate on ...
- 🤔 I’m looking for help with ...
- 💬 Ask me about ...
- 📫 How to reach me: ...
- 😄 Pronouns: ...
- ⚡ Fun fact: ...
-->
// Code squelette d'une plateforme de création de boutiques en ligne (simplifié) en JavaScript

class Boutique {
  constructor(nomBoutique, proprietaire) {
    this.nomBoutique = nomBoutique;
    this.proprietaire = proprietaire;
    this.produits = []; // Tableau des produits dans la boutique
    this.theme = "theme_par_defaut"; // Thème visuel de la boutique
    this.paiementsAcceptes = ["carte_credit"]; // Modes de paiement acceptés
  }

  ajouterProduit(produit) {
    this.produits.push(produit);
    console.log(`Produit '${produit.nom}' ajouté à la boutique '${this.nomBoutique}'.`);
  }

  supprimerProduit(nomProduit) {
    const index = this.produits.findIndex(produit => produit.nom === nomProduit);
    if (index > -1) {
      this.produits.splice(index, 1);
      console.log(`Produit '${nomProduit}' supprimé de la boutique '${this.nomBoutique}'.`);
    } else {
      console.log(`Produit '${nomProduit}' non trouvé dans la boutique '${this.nomBoutique}'.`);
    }
  }

  modifierProduit(nomProduit, nouvellesInformations) {
    const produit = this.produits.find(produit => produit.nom === nomProduit);
    if (produit) {
      Object.assign(produit, nouvellesInformations); // Fusionne les nouvelles informations dans l'objet produit
      console.log(`Produit '${nomProduit}' modifié dans la boutique '${this.nomBoutique}'.`);
    } else {
      console.log(`Produit '${nomProduit}' non trouvé dans la boutique '${this.nomBoutique}'.`);
    }
  }

  afficherBoutique() {
    console.log(`Nom de la boutique: ${this.nomBoutique}`);
    console.log(`Propriétaire: ${this.proprietaire}`);
    console.log("Produits:");
    if (this.produits.length === 0) {
      console.log("   Aucun produit disponible.");
    } else {
      this.produits.forEach(produit => {
        console.log(`   - ${produit.nom} - Prix: ${produit.prix}`); // Affiche nom et prix, vous pouvez ajouter d'autres infos
      });
    }
  }

  definirTheme(nouveauTheme) {
    this.theme = nouveauTheme;
    console.log(`Thème de la boutique '${this.nomBoutique}' changé en '${this.theme}'.`);
  }

  ajouterPaiementAccepte(methodePaiement) {
    if (!this.paiementsAcceptes.includes(methodePaiement)) {
      this.paiementsAcceptes.push(methodePaiement);
      console.log(`Méthode de paiement '${methodePaiement}' ajoutée à la boutique '${this.nomBoutique}'.`);
    } else {
      console.log(`La méthode de paiement '${methodePaiement}' est déjà acceptée par la boutique '${this.nomBoutique}'.`);
    }
  }
}

// Exemple d'utilisation
const maBoutique = new Boutique("Ma Boutique en Ligne", "Jean Dupont");

// Ajout de produits
const produit1 = { nom: "T-shirt en coton bio", prix: 25.00, description: "T-shirt confortable en coton biologique.", image: "tshirt.jpg" };
const produit2 = { nom: "Mug personnalisé", prix: 12.50, description: "Mug avec impression personnalisée.", image: "mug.jpg" };
maBoutique.ajouterProduit(produit1);
maBoutique.ajouterProduit(produit2);

// Modification d'un produit
maBoutique.modifierProduit("T-shirt en coton bio", { prix: 27.00, description: "T-shirt confortable en coton biologique, nouvelle collection." });

// Suppression d'un produit
maBoutique.supprimerProduit("Mug personnalisé");

// Affichage de la boutique
maBoutique.afficherBoutique();

// Changer le thème
maBoutique.definirTheme("theme_moderne");

// Ajouter une méthode de paiement
maBoutique.ajouterPaiementAccepte("paypal");

console.log(`Méthodes de paiement acceptées: ${maBoutique.paiementsAcceptes}`);
console.log(`Thème actuel de la boutique: ${maBoutique.theme}`);
