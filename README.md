# Angular
## Débuter avec Angular
### Créer la liste de produits

1. Avec la syntaxe <div *ngFor="let product of products"></div> on fait une boucle "for" qui va lister la variable products implémentée dans le fichier "products.ts" sous forme de tableau pour l'exporter dans notre fichier "product-list.component.html".
  
2. On va ensuite l'afficher sur notre interface sous forme de texte via la syntaxe {{ product.name }}. Dans le fichier "products.ts" on créé une classe Product avec des attributs et un constructeur qui lors de l'instanciation permettra d'appeler le paramètre souhaité. Notamment ici avec "product.name" on va pouvoir appeler la valeur donnée à "name" lors de l'instanciation de l'objet, "name" correspond au nom du produit.
  
3. Dans la Div, en ajoutant la balise <a [title]="product.name + ' details'">, cela permet d'afficher un texte en survol contenant des infos notamment ici ("nom du produit" détails) quand on passe le curseur sur le produit. 

4. On ajoute ensuite une balise paragraphe dans laquelle on rajoute la syntaxe <p *ngIf="product.description">Description: {{ product.description }}</p> dans laquelle on va mettre une condition "If" pour dire que si dans l'instance de l'object il y a un paramètre "description", on va l'afficher sur l'interface grâce à la syntaxe {{product.description}} et afficher ainsi la description de chaque produit de la liste.

5. On ajoute un bouton "share" qui comme la balise est dans la Div  "ngFor", boucle sur chaque produit et s'affiche ainsi en dessous de chaque produits. (click) va appeler la fonction share() qui se trouve dans le fichier 'product-lit.component.ts' et qui lorsqu'on clique sur le bouton, ouvrira une fenêtre d'alert dans laquelle sera affiché "Vous avez partagé ce produit !"

### Transmettre des données à un composant enfant

On crée une nouvelle fonctionnalité d'alerte qui va vérifier qu'elle correspond bien à la condition qu'on va lui donner et si c'est le cas, va afficher un bouton qui permettra à l'utilisateur de cliquer dessus et ce qui lui permettra de visualiser la mise en vente du produit. Cette fonctionnalité est créée dans le composant 'ProductAlert' (composant enfant) et héritera du composant 'ProductListComponent' (composant parent).

1. On va créer un nouveau composant via le terminal en tapant la commmande ng generate component product-alerts.
 
2. Dans le fichier 'product-alerts.component.ts', on y retrouve le décorateur qui va nous permettre de définir le composant et dans lequel on y retrouve le sélecteur qui va spécifier comment on peut utiliser le composant dans les templatesHTML ici dans ce cas en utilisant la balise <app-product-alerts></app-product-alerts>.
  
3. Ensuite il faut configurer la réception des données produit en important 'Input' depuis @angular/core.
   
4. On implémente ensuite dans la class ProductAlertsComponent une propriété 'product' qui sera de type 'Product' ou 'undefined' et qui hérite du parent du composant par le biais du décorateur '@Input()'.
   
5. On va ensuite dans le fichier 'product-alerts.component.html' qui va nous permettre de créer le bouton qui permettra de mettre la condition d'affichage du bouton qui permettra à l'utilisateur d'être notifié en utilisant une condition 'If' pour dire que si le produit et son prix son supérieur à 700 patates alors on affiche ce bouton d'alerte pour ce produit.*
   
6. Le générateur a automatiquement importé le 'ProductAlertsComponent' dans l'app.module.ts afin qu'il soit accessible par les autres composants du projet.
   
7. Il faut ensuite ajouter la balise <app-product-alerts></app-product-alerts> dans le fichier 'product-list.component.html' du composant 'productListComponent' afin de lui dire que 'ProductAlertsComponent' est un enfant de 'ProductListComponent'.
   
8. Dans le fichier 'product-list.component.html' on va implémenter la balise <app-product-alerts> pour inclure le composant enfant 'ProductAlertsComponent' dans le template du composant parent 'ProductListComponent' qui a une propriété 'product' et va transmettre sa valeur au composant enfant à l'aide de l'attribut [product].

### Transmettre des données à un composant parent
Maintenant qu'on a définie la fonctionnalité du bouton d'alerte et qu'il est affiché il faut que ce bouton fonctionne afin que le composant enfant notifie et transmette les donnes au composant parent.

1. Dans le fichier 'product-alerts.component.ts', on va importer une propriété de sortie de donnée avec 'Output' et une propriété d'émission d'événement avec 'EventEmitter' depuis @angular/core.

2. On implémente ensuite dans la class ProductAlertsComponent une propriété 'notify' avec un décorateur @Output et une nouvelle instance de 'EventEmitter' ce qui permettra d'émettre un évènement quand la valeur de la propriété 'notify' change.

3. Ensuite, dans le fichier 'product-alerts.component.html' on va rajouter à la balise bouton l'élément '(click)' qui va appeler la function onNotify() quand on clique sur le bouton.

4. On définit la fonctionnalité de la function onNotify() dans le fichier 'product-list.component.ts' qui sera d'afficher, au click du bouton, une fenêtre qui va afficher l'information.

5. On va ensuite mettre à jour le fichier 'product-list.component.html' en créant une liaison d'événement '(notify)' (les parenthèses indique qu'on déclare un écouteur de l'événement 'notify') qui va appeler la function onNotify() à l'intérieur de la balise <app-product-alerts>.
   
### Et après

Bah je vais aller me coucher après avoir pris une boîte complète d'Ibuprofène et avoir vidé une bouteille entière de J&D ...

![](https://github.com/Keitaroblaster/Angular/blob/main/elwjcajd.jpg?raw=true)

## Ajout de la navigation
### Associer un chemin URL à un composant

On va voir comment faire pour afficher les détails d'un produit individuel c'est à dire avoir comme une page dédiée avec un panel d'information sur le produi quand on clique sur ce produit parmi la liste de produits.

1. On va créer un nouveau composant via le terminal en tapant la commmande ng generate component product-details.

2. Dans le fichier 'app.module.ts' on va créer le chemin pour accéder aux détails du produit avec un 'path: "products/:productId", component: ProductDetailsComponent' et qui permet ainsi de faire correspondre une URL spécifique à un composant de 'ProductDetailsComponent' et qui sera responsable de l'affichage des détails du produit correspondant au 'productId' fourni dans l'URL.

3. On va ensuite dans le fichier 'product-list.component.html' dans lequel on va modifier l'ancre pour y rajouter un 'routerLink' qui est un lien qui va permettre de lancer la navigation vers un itinéraire en prenant comme paramètre le 'productId' c'est à dire qu'il va aller dans le fichier 'product.ts' dans lequel se trouve le tableau des produits et il va recherche via l'Id de chaque produit celui qui correspond au productId de l'URL.

### Afficher les détails du produit

1. On importe l'accès aux infos, puis l'initialisation ainsi que le tableaux des produits.

2. Ensuite dans la classe ProductDetailComponent on implément l'initialisation et les produits.

3. On active en injectant l'accès aux infos.

4. On va faire appel à une fonction pour qu'elle recherche l'Id du produit dans le tableau afin de l'extraire.

5. Dans le fichier 'Product-details.Component.html' on va définir le modèle d'affichage des éléments correpondant au produit afin que lorsque les utilisateurs cliquent sur un nom dans la liste de produits, le routeur les dirige vers l'URL distinct du produit, affiche le ProductDetailsComponent et affiche les détails du produit.

### Et après

Bah là ça y'est ....

![](https://raw.githubusercontent.com/Keitaroblaster/Angular/main/why.webp)

## Gestion des données
### Créer le service de panier d'achat
#### Définir un service de panier

On va créer maintenant un moyen pour permettre à l'utilisateur d'ajouter des produits dans un panier via un bouton qui sera configuré de manière à stocker des informations sur les produits dans la panier.

1. On va créer un nouveau composant via le terminal en tapant la commmande ng generate service cart.

2. On importe 'Products' depuis le fichier product.ts et dans la classe CartService, on va déclarer une propriété 'items' de type 'Product' sous forme de tableau qui permettra de stocker les produits sélectionnés dans le panier.

3. Dans la classe  CartService on va définir 3 méthodes qui vont permettre :
   
       - d'ajouter un produit dans le tableau de 'items' via la méthode 'addTo'.

       - de retourner le ou les articles avec sa quantité via un 'get'

       - d'effacer le panier via la méthode 'clear'

#### Utiliser le service de panier

On va voir maintenant comment ajouter un produit au panier.

1. Dans le fichier 'product-details.component.ts', on importe 'CartService' depuis 'cart.service'.

2. Puis dans le constructeur de la classe ProductDetailsComponent, on va rajouter la propriété cartService de type 'CartService' en mode privé qui sera accessible via la méthode 'get' implémentée dans le fichier 'cart.service.ts'

3. Puis dans la classe ProductDetailsComponent, on va créer la méthode 'addToCart' qui va récupérer le produit depuis le fichier 'cart.service.ts' (this.cartservice) dans laquelle se trouve la méthode 'addToCart' qui pousse le produit afin d'ensuite l'ajouter au panier (.addToCart(product)).

4. Dans le fichier 'product-details.component.html', on va ajouter le bouton pour acheter le produit qui va en fait ajouter le produit au panier lors du click. on va donc rajouter une balise button de type button et on va ajouter l'élément d'événement click qui appellera la méthode d'ajout du produit dans le panier implémenté dans le fichier 'product-details.component.ts'.

### Créer la vue du panier
#### Configurer le composant panier

1. Création d'un nouveau composant via le terminal en tapant la commande ng generate component cart.

2. on rajoute dans le fichier 'app.module.ts' l'itinéraire { path: "cart", component: CartComponent} pour accéder au panier. 

3. Dans le fichier 'top-bar.component.html' on met à jour l'ancre en ajoutant le lien de routage 'routerLink="/cart"' vers le composant 'cart'.

#### Afficher les articles du panier

1. On importe le fichier 'CartService' depuis le fichier 'cart.service.ts' dans le fichier 'cart.component.ts'.

2. Dans le fichier 'cart.component.ts' on ajoute au constructeur de la classe 'CartComponent' la propriété 'cartService' de type 'CartService'.

3. Puis on définit la propriété 'items' qui va permettre d'enregistrer le produit sélectionner dans le panier via l'accesseur 'Items'par la méthode 'this.cartService.getItems()'.

4. Dans le fichier 'cart.component.html' on va boucler sur les produits qui quand il correspondra au produit sélectionné affichera le nom de l'item via la syntaxe {{item.name}} ainsi que le prix du produit via la syntaxe {{item.price | currency}}.

### Récupérer les prix d'expédition
#### Configurer AppModule pour utiliser HttpClient

1. Importation de 'HttpClientModule' dans le fichier 'app.module.ts' et rajouter 'HttpClientModule' dans les imports de '@NgModule' pour pouvoir utiliser le service 'HttpClient'.

#### Configurer CartService pour utiliser HttpClient

1. Importation de 'HttpClient' dans le fichier 'cart.service.ts' afin de pouvoir récupérer des données et intéragir avec des API et des ressources externes puis ajouter au constructeur de la classe 'CartService' la propriété 'http' de type 'HttpClient'.

#### Configurer CartService pour obtenir les prix d'expédition

1. Après la configuration pour pouvoir utiliser 'HttpClient' et permettre la récupération des données, il faut pouvoir récupérer les données d'expédition à partir d'un fichier 'shipping.json'. On va définir une méthode 'getShippingPrices()' dans la classe 'CartService' du fichier 'cart.service.ts' qui utilisera la méthode 'get()' de 'HttpClient' :

'return this.http.get<{type: String, price: number}[]>('/assets/shipping.json');'

### Créer un composant d'expédition

1. 



     









