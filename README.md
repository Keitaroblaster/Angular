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

1. On met à jour le fichier 'product-details.component.ts' en important le décorateur 'OnInit' que le composant implémente l'interface 'OnInit' et la classe 'ActivatedRoute' afin d'accéder aux informations associées à la route active.

2. On définit la classe 'ProductDetailsComponent' qui a une propriété 'product' de type 'Product' ou 'undefined' et qui va implémenter l'interface 'OnInit' qui appellera la méthode 'ngOnInit' lors de l'initialisation du composant.

3. On y ajoute dans la classe 'ProductDetailsComponent' le constructeur qui prend en paramètre une instance de la classe 'ActivatedRoute' et l'assigne à la propriété privée 'route' ce qui permettra à la classe d'accéder aux informations 'ActivatedRoute'.

4. Dans le fichier product-details.component.ts, on créé la méthode 'ngOnInit qui sera appelée lors de l'initialisation du composant. Cette méthode va utiliser dans un 1er temps les informations de 'route' via la constante 'routeParams' avec 'snapshot' qui est la propriété d'ActivatedRoute et représente une capture instantanée des informations de route au moment de la navigation et 'paramMap' qui contient les paramètres de la route sous forme de map, pour extraire l'Id du produit à partir de l'URL via la constante 'productIdFromRoute' avec 'routeParams.get('productId')' qui va permettre de récupérer la valeur du paramètre 'productId' de l'URL en tant que chaîne de caractères pour ensuite être convertit en un nombre entier par la méthode number(). Puis une fois l'Id extraite la méthode va permettre de rechercher le produit correspondant dans une liste de produits et l'assigne à la propriété 'product' de la classe.

5. On finit en mettant à jour le fichier 'product-details.component.html' afin d'afficher les détails d'un produit uniquement si la propriété 'product' existe et affichera le nom, le prix et la description du produit.

### Et après

Bah ....

![](https://raw.githubusercontent.com/Keitaroblaster/Angular/main/why.webp)

## Gestion des données
### Créer le service de panier d'achat
#### Définir un service de panier

1. On va créer un nouveau composant via le terminal en tapant la commmande 'ng generate service cart'.

2. Dans le fichier 'cart.service.ts' on importe la classe 'Product'. Le décorateur '**@Injectable**' est utilisé pour indiquer qu'une classe peut être injectée avec des dépendances et 'providedIn:'root'' indique qu'une seule instance de ce service sera partagée par toute l'application. Puis déclaration dans la classe 'CartService' de la propriété 'items' qui sera un tableau de produits initialisé vide.

3. Dans la classe 'CartService' on définit des méthodes pour la gestion du panier :
   
     - Dans un 1er temps on définit une méthode 'addToCart(product: Product)' qui prend en paramètre un 'product' de type 'Product' et va ajouter un produit au panier grâce à 'this.items.push(product)' qui va permettre d'ajouter le produit à la fin du tableau 'items' du panier.
  
     - Dans un 2eme temps on définit une méthode 'getItems()' qui va retourner les produits présents dans le panier.
  
     - Puis dans un dernier temps on définit une méthode 'clearCart()' qui va permettre de vider le panier en réinitialisant le tableau grâce au 'this.items = []' qui attribue un tableau vide à la propriété 'items' et le retourne avec 'return this.items'.

#### Utiliser le service de panier

1. Importation de la classe 'CartService' dans le fichier 'product-details.component.ts' pour accéder à la fonctionnalité fournie par le service pour ajouter des produits au panier. Puis on initialise la propriété 'cartService' de type de la classe 'CartService dans le constructeur de la classe 'ProductDetailsComponent'.

3. Ajout dans la classe 'ProductDetailsComponent' de la méthode 'addToCart(product: Product)' qui va faire appelle au service 'cartService' qui va appeler la méthode 'addToCart' avec le produit en argument ce qui ajoutera le produit au panier puis afficher une alerte pour informer l'utilisateur que son produit est bien dans le panier.

4. Dans le fichier 'product-details.component.html' on met en place un bouton d'évènement 'Buy' qui lorsque l'utilisateur cliquera sur ce bouton, cela fera appel à la méthode 'addToCart(product)' qui ajoutera le produit au panier.

### Créer la vue du panier
#### Configurer le composant panier

1. On va créer un nouveau composant via le terminal en tapant la commmande 'ng generate component cart'.

3. Dans le fichier 'app.module.ts', on définit le chemin vers l'URL '/cart' qui quand il sera atteint, le composant 'CartComponent' sera chargé et affiché.

4. Mise à jour du bouton 'payer' dans le fichier 'top-bar.component.html' avec une directive 'routerLink' qui point vers l'URL '/cart'.

#### Afficher les articles du panier

1. Importation de la classe 'CartService' dans le fichier 'cart.component.ts' puis on ajoute au constructeur de la classe 'CartComponent' la propriété 'cartService' de type de la classe 'CartService'.

3. On définit la propriété 'items' qui va permettre d'enregistrer dans le panier le produit sélectionné en appelant la méthode 'getItems()' dont la valeur retournée sera attribuée à la variable 'items'.

4. Dans le fichier 'cart.component.html', ajout d'une directive '*ngFor' qui va itérer sur la liste 'items' afin d'afficher via l'interpolation le nom et le prix de l'article.

### Récupérer les prix d'expédition
#### Configurer AppModule pour utiliser HttpClient

1. Importation du module 'HttpClientModule' dans le fichier 'app.module.ts' qui va fournir les fonctionnalités liées à la gestion des requêtes HTTP dans les applications pour récupérer ou envoyer des données vers un serveur.

#### Configurer CartService pour utiliser HttpClient

1. Importation de la classe 'HttpClient' dans le fichier 'cart.service.ts' afin de pouvoir récupérer des données et intéragir avec des API et des ressources externes puis ajout au constructeur de la classe 'CartService' la propriété 'http' de type de la classe 'HttpClient'.

#### Configurer CartService pour obtenir les prix d'expédition

1. Après la configuration pour pouvoir utiliser 'HttpClient' et permettre la récupération des données, il faut pouvoir récupérer les données d'expédition à partir d'un fichier 'shipping.json'. On définit une méthode 'getShippingPrices()' dans la classe 'CartService' du fichier 'cart.service.ts' qui utilisera la méthode 'get()' vers le fichier JSON qui contient les prix d'expéditions.

### Créer un composant d'expédition

1. On va créer un nouveau composant via le terminal en tapant la commmande 'ng generate component shipping' qui va nous permettre d'afficher les données d'expédition.

2. Dans le fichier 'app.module.ts' on ajoute le chemin pour l'expédition dans @NgModule -> RouteurModule.forRoot -> {path: "shipping", component:ShippingComponent},

#### Configuration du ShippinComponent pour utiliser CartService

1. Afin de récupérer les données d'expédition depuis le fichier 'shipping.json' via le Http, on importe 'CartService' dans le fichier 'shipping.component.ts'.

2. Dans la classe 'ShippingComponent', on crée le constructeur prenant en paramètre la propriété 'cartService' de type de la classe 'CarteService'.

3. On définit la propriété 'shippingCosts', qui ne sera pas intialisée dans le constructeur, de type 'Observable' sous forme de tableau d'objets avec les propriétés 'type' de type String et 'price' de type number. Ensuite on crée une méthode 'ngOnInit' qui sera appelé quand le composant sera initialisé et permettra de récupérer les coûts d'expédition via la méthode 'getShippingPrices()' et assigner la valeur à 'ShippingCosts'.

4. On met à jour le fichier 'shipping.component.html' en configurant le modèle d'affichage des expéditions et leur prix avec une directive'*ngFor' pour les expéditions en mode async ce qui permet de renvoyer la dernière valeure de façon automatique jusqu'à ce le composant s'arrête.

5. Mise à jour du fichier 'cart.component.html' en rajoutant le chemin vers l'URL '/shipping' qui permettra d'afficher les prix d'expédition.

## Utilisation de formulaires pour la saisie utilisateur
### Définir le modèle de formulaire de paiement

2. Importation dans le fichier 'cart.component.ts' de la classe 'FormBuilder' pour fournir des utilitaires pour la création et la gestion de formulaires dans l'application.

3. On initialise dans le constructeur de la class 'CartComponent' la propriété 'formBuilder' de type de la classe 'FormBuilder' puis on définit une méthode group() du FormBuilder pour récupérer des données.

3. On appelle la méthode 'clearCart()' de 'cartService' pour effacer le contenu du panier et assigner les éléments du panier à la propriété 'items' puis afficher une fenêtre de confirmation et la valeur du formulaire dans la console du navigateur pour ensuite réinitialiser le formulaire pour une nouvelle entrée.

### Créer le formulaire de paiement

1. Dans le fichier 'cart.component.html' on crée un élément HTML 'form' dans lequel on assigne un attribut '[formGroup]' pour lier le formulaire à un objet 'FormGroup' via l'instance 'checkoutForm' puis on ajoute un bouton pour soumettre le formulaire via la liaison d'évènement 'ngSubmit' qui appellera la méthode 'onSubmit()'.

2. On ajoute ensuite des balises 'input' afin de saisir les valeurs correspondants aux champs et les lier au 'checkoutForm'.

### Et après

![]()

