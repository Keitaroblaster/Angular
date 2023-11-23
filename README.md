# Angular
# Créer la liste de produits
- Avec la syntaxe <div *ngFor="let product of products"></div> on va exporter nos produits qu'on a implémenté dans notre fichier "products.ts" dans notre fichier "product-list.component.html".
- On va ensuite l'afficher sur notre interface sous forme de texte via la syntaxe {{ product.name }}
- Dans la Div, en ajoutant la balise <a [title]="product.name + ' details'">, cela permettra d'afficher une valeur ("nom du produit" détails) quand on passe le curseur sur le produit.
- 
