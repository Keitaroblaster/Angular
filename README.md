# Angular
## Débuter avec Angular
### Créer la liste de produits
1. Avec la syntaxe <div *ngFor="let product of products"></div> on fait une boucle "for" qui va lister la variable products implémentée dans le fichier "products.ts" sous forme de tableau pour l'exporter dans notre fichier "product-list.component.html".
  
2. On va ensuite l'afficher sur notre interface sous forme de texte via la syntaxe {{ product.name }}. Dans le fichier "products.ts" on a crée une classe Product avec des attributs et un constructeur qui lors de l'instanciation permettra d'appeler le paramètre souhaité. Notamment ici avec "product.name" on va pouvoir appeler la valeur donnée à "name" lors de l'instanciation de l'objet, "name" correspond au nom du produit.
  
3. Dans la Div, en ajoutant la balise <a [title]="product.name + ' details'">, cela permet d'afficher un texte en survol contenant des infos notamment ici ("nom du produit" détails) quand on passe le curseur sur le produit. 

4. On ajoute ensuite une balise paragraphe dans laquelle on rajoute la syntaxe <p *ngIf="product.description">Description: {{ product.description }}</p> dans laquelle on va mettre une condition "If" pour dire que si dans l'instance de l'object il y a un paramètre "description", on va l'afficher sur l'interface avec la syntaxe {{product.description}} et afficher ainsi la description de chaque produit de la liste.

5. On ajoute un bouton "share" qui comme la balise est dans la Div  "ngFor", boucle sur chaque produit et s'affiche ainsi en dessous de chaque produits. (click) va appeler la fonction share() qui se trouve dans le fichier "product-lit.component.ts" et qui lorsqu'on clique sur le bouton, ouvrira une fenêtre d'alert dans laquelle sera affiché "Vous avez partagé ce produit !"

### Transmettre des données à un composant enfant
Je n'ai rien compris de comment cela fonctionne à part générer des composants via le terminal les importer et exporter entre eux et que cette partie permet de mettre en place un bouton de notification sur chaque produits qui auraient une valeur supérieur à 700 pépins de maïs.

### Transmettre des données à un composant parent
Je n'ai encore pas plus compris à part afficher une alerte concernant la notification précédente quand l'utilisateur clique sur le bouton de notification.

### Et après
Bah je vais aller me coucher après avoir pris une boîte complète d'Ibuprofène et avoir vidé une bouteille entière de J&D ...

## Ajout de la navigation
### Associer un chemin URL à un composant
De ce que je comprends ici c'est qu'on va modifier l'ancrage dans le fichier product-list.component.html afin d'y ajouter le lien URL qui permettra d'accèder à la page du produit dans laquelle on y retrouve les détails et le pont qui permet d'y accèder est l'Id du produit.

### Afficher les détails du produit
1. On importe l'accès aux infos, puis l'initialisation ainsi que le tableaux des produits.
2. Ensuite dans la classe ProductDetailComponent on implément l'initialisation et les produits
3. On active en injectant l'accès aux infos
4. On va faire appel à une fonction pour qu'elle recherche l'Id du produit dans le tableau afin de l'extraire
5. Dans le fichier "Product-details.Component.html" on va définir le modèle d'affichage des éléments correpondant au produit afin que lorsque les utilisateurs cliquent sur un nom dans la liste de produits, le routeur les dirige vers l'URL distincte du produit, affiche le ProductDetailsComponent et affiche les détails du produit.

### Et après
Bah je vais aller me coucher une 2ème fois après avoir pris une nouvelle boîte complète d'Ibuprofène et avoir vidé une 2ème bouteille entière de J&D ...

## Gestion des données
### Créer le service de panier d'achat








