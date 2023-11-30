# Angular
## Débuter avec Angular
### Créer la liste de produits

2. Dans notre fichier "product-list.component.html" on créé un titre 'Products' et une balise 'div' qui va utiliser la directive '*ngFor' qui est une directive **structurelle** et qui va parcourir chaque élément du tableau 'products' pour stocker dans la variable 'product' la valeur actuelle du tableau à chaque itération.
  
3. On afficher la valeur 'name' de chaque objet 'product' du tableau 'products'avec {{ product.name }} qui est une **interpolation** .
  
5. On affiche au survole sur le produit des infos notamment ici le nom du produit et la chaîne de caractère 'details' grâce à la **liaison de propriété** '[title]'.

6. On utilise une directive '*ngIf' qui définie que si 'product.description' existe alors on récupère via l'interpolation, la valeur de la propriété 'description' de l'objet 'product' pour afficher la description du produit.

7. On ajoute un bouton et un évènement 'click' qui réagira au clic de la souris sur le bouton et appellera la fonction 'share()' qui doit ouvrir une fenêtre et afficher un message.

### Transmettre des données à un composant enfant

2. On créé un nouveau composant via le terminal en tapant la commmande 'ng generate component product-alerts'.
 
3. Dans le fichier 'product-alerts.component.ts', on y retrouve le décorateur **@Component** qui est une **annotation** et qui définit les métadonnées d'un composant. Dans ce décorateur on y trouve le 'selector' qui identifie le composant qui sera utilisé dans le HTML via la balise '<app-product-alerts>'. On y trouve aussi le 'TemplateUrl' qui indique le chemin du fichier HTML et le 'StyleUrls' qui indique une liste de fichiers CSS contenant les styles pour le composant.
  
4. Importation des décorateurs 'Component' et 'Input' depuis le module @angular/core ce qui va permettre de définir et configurer des composants Angular et de la classe 'Product'.
   
5. On définit une propriété d'entrée 'product' de type 'Product' ou 'undefined' via le décorateur **@Input()** qui permet de passer les données contenues dans 'Product'. Cette propriété d'entrée sera fournie par le composant parent lors de l'utilisation de '<app-product-alerts>'.
   
6. On utilise une directive '*ngIf' qui va vérifier si la propriété 'product' existe et si la propriété 'price' de l'objet 'product' est supérieur à 700 qui dans ce cas si c'est true affichera un bouton 'Notify Me'.
   
7. Ajout automatique de la classe 'ProductAlertsComponent' dans le fichier 'app.module.ts' où on y trouve le décorateur **@NgModule** utilisé pour configurer un module en spécifiant les composants, directives qui appartiennent à ce module sous forme de tableau nommé 'declarations'.
   
8. Dans la balise '<app-product-alerts>' on ajoute une liaison de propriété qui passe la valeur de la propriété 'product' du composant parent au composant 'app-product-alerts', ce qui permet de transmettre des données du composant parent au composant enfant et d'intéragir avec le composant 'app-product-alerts' en fonction de la valeur de 'product'.

### Transmettre des données à un composant parent

1. Dans le fichier 'product-alerts.component.ts' on importe en plus des décorateur, 'Component' et 'Input' et de la classe 'Product', le décorateur 'Output' qui va permettre de déclarer une propriété de sortie dans le composant et la classe 'EventEmitter' qui va permettre de créer un objet émettant des événements personnalisés.

2. Dans la classe 'ProductAlertsComponent' on configure le composant avec une propriété d'entrée 'product' qui peut être fournie par le composant parent et une propriété de sortie 'notify' qui va permettre au composant enfant d'émettre un évènement quand quelque chose doit être notifié.

3. Mise à jour du bouton 'Notify Me' dans le fichier 'product-alerts.component.html' en ajoutant l'évènement '(click)' qui réagira au clic de la souris sur le bouton et appellera la fonction 'emit()' dela propriété 'notify'.

4. Ajout dans la classe 'ProductListComponent' du fichier 'product-list.component.ts' de la méthode 'onNotify()' qui lorsqu'elle sera appelé, ouvrira une boîte de dialogue pour afficher le message que l'utilisateur sera notifié quand le produit sera en vente.

5. Par la même occasion dans le fichier 'product-list.component.ts', on ajoute une liaison d'évènement qui écoute l'évènement 'notify' émis par le composant 'app-product-alerts' et appelle la méthode 'onNotify()' du composant parent en réponse à cet évènement.
  
### Et après

Bah je vais aller me coucher après avoir pris une boîte complète d'Ibuprofène et avoir vidé une bouteille entière de J&D ...

![](https://github.com/Keitaroblaster/Angular/blob/main/elwjcajd.jpg?raw=true)

## Ajout de la navigation
### Associer un chemin URL à un composant

1. On crée un nouveau composant via le terminal en tapant la commmande 'ng generate component product-details'.

2. Dans le décorateur '**@NgModule**' du fichier 'app.module.ts' on va ajouter dans le module 'RouterModule' qui fournit des fonctionnalités de routage pour la navigation, la route qui est associée aux pages de détails de produit où '**:productId**' est un paramètre dynamique qui peut être passé dans l'URL. Le composant 'ProductDetailsComponent' est ainsi chargé quand le chemin est atteint.

3. Dans le fichier 'product-list.component.html' on met à jour l'ancre en ajoutant la directive '[routerLink]'pour créer un lien de navigation en pointant vers le chemin '**'/products'**' avec l'Id spécifique du produit '**product.id**'.

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

1. Création d'un composant via le terminal 'shipping' qui va nous permettre d'afficher les données d'expédition.

2. Dans le fichier 'app.module.ts' on ajoute le chemin pour l'expédition dans @NgModule -> RouteurModule.forRoot -> {path: "shipping", component:ShippingComponent},

#### Configuration du ShippinComponent pour utiliser CartService

1. Afin de récupérer les données d'expédition depuis le fichier 'shipping.json' via le Http, on importe 'CartService' dans le fichier 'shipping.component.ts'.

2. Dans la classe 'ShippingComponent', on crée le constructeur prenant en paramètre la propriété 'cartService' de type 'CarteService'.

3. Puis on déclare la propriété 'shippingCosts', qui ne sera pas intialisée dans le constructeur, de type 'Observable' sous forme de tableau d'objets avec les propriétés 'type' de type String et 'price' de type number. Ensuite on crée une méthode 'ngOnInit' qui sera appelé quand le composant sera initialisé et permettra de récupérer les coûts d'expédition via la méthode 'getShippingPrices()' et assigner la valeur à 'ShippingCosts'.

4. Dans le fichier 'shipping.component.html' on configure le modèle d'affichage des expéditions et leur prix avec une boucle pour les expéditions en mode async ce qui permet de renvoyer la dernière valeure de façon automatique jusqu'à ce le composant s'arrête.

5. Dans le fichier 'cart.component.html' on rajoute le chemin qui va afficher les prix d'expédition.

## Utilisation de formulaires pour la saisie utilisateur
### Définir le modèle de formulaire de paiement

1. Dans le fichier 'cart.component.ts' on importe 'FormBuilder' pour faciliter la création d'abstractControl qui est la classe de base les formulaires de contrôle, de groupe et de tableau puis on l'initialise dans le constructeur.

2. On fait une méthode group() du FormBuilder pour récupérer des données.

3. On appelle la méthode 'clearCart()' de 'cartService' pour effacer le contenu du panier et assigner les éléments du panier à la propriété 'items' puis afficher une fenêtre de confirmation et la valeur du formulaire dans la console du navigateur pour ensuite réinitialiser le formulaire pour une nouvelle entrée.

### Créer le formulaire de paiement

1. Dans le fichier 'cart.component.html' on crée un élément HTML 'form' et y ajouter un attribut '[formGroup]' pour lier le formulaire à un objet 'FormGroup' via l'instance 'checkoutForm' puis on ajout un bouton pour soumettre le formulaire via la liaison d'évènement 'ngSubmit' qui appellera la méthode 'onSubmit()'.

2. On ajoute ensuite des balises 'input' afin de saisir les valeurs correspondants aux champs et les lier au 'checkoutForm'.
