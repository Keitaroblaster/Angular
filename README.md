# Angular
# Créer la liste de produits
- Avec la syntaxe <div *ngFor="let product of products"></div> on fait une boucle "for" qui va lister la variable products implémentée dans le fichier "products.ts" sous forme de tableau pour l'exporter dans notre fichier "product-list.component.html".
  
- On va ensuite l'afficher sur notre interface sous forme de texte via la syntaxe {{ product.name }}. Dans le fichier "products.ts" on a crée une classe Product avec des attributs et un constructeur qui lors de l'instanciation permettra d'appeler le paramètre souhaité. Notamment ici avec "product.name" on va pouvoir appeler la valeur donnée à "name" lors de l'instanciation de l'objet, "name" correspond au nom du produit.
  
- Dans la Div, en ajoutant la balise <a [title]="product.name + ' details'">, cela permet d'afficher un texte en survol contenant des infos notamment ici ("nom du produit" détails) quand on passe le curseur sur le produit. 

- On ajoute ensuite une balise paragraphe dans laquelle on rajoute la syntaxe <p *ngIf="product.description">Description: {{ product.description }}</p> dans laquelle on va mettre une condition "If" pour dire que si dans l'instance de l'object il y a un paramètre "description", on va l'afficher sur l'interface avec la syntaxe {{product.description}} et afficher ainsi la description de chaque produit de la liste.

- On ajoute un bouton "share" qui comme la balise est dans la Div  "ngFor", boucle sur chaque produit et s'affiche ainsi en dessous de chaque produits. (click) va appeler la fonction share() qui se trouve dans le fichier "product-lit.component.ts" et qui lorsqu'on clique sur le bouton, ouvrira une fenêtre d'alert dans laquelle sera affiché "Vous avez partagé ce produit !"

# Transmettre des données à un composant enfant

Je n'ai rien compris à part importer et exporter des composants.

# Transmettre des données à un composant parent

J'ai encore pas plus compris.

# Et après

Bah je vais aller me coucher après avoir pris une boîte complète d'Ibuprofène, avoir vidé une bouteille entière de J&D ...





