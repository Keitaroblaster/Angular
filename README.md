# Angular
## I. Débuter avec Angular
### 1. Créer la liste de produits

2. Dans notre fichier "_product-list.component.html_" on créé un titre "_Products_" et une balise "_div_" qui va utiliser la directive "_*ngFor_" qui est une directive **structurelle** et qui va parcourir chaque élément du tableau "_products_" pour stocker dans la variable "_product_" la valeur actuelle du tableau à chaque itération.
  
3. On affiche la valeur "_name_" de chaque objet "_product_" du tableau "_products_" avec **{{ product.name }}** qui est une **interpolation** .
  
5. On affiche au survole sur le produit des infos notamment ici le nom du produit et la chaîne de caractère "_details_" grâce à la **liaison de propriété**: "_[title]_".

6. On utilise une directive "_*ngIf_" qui définie que si "_product.description_" existe alors on récupère via l'interpolation, la valeur de la propriété "_description_" de l'objet "_product_" pour afficher la description du produit.

7. On ajoute un bouton et un évènement "_click_" qui réagira au clic de la souris sur le bouton et appellera la fonction "_share()_" qui doit ouvrir une fenêtre et afficher un message.

### 2. Transmettre des données à un composant enfant

2. On créé un nouveau composant via le terminal en tapant la commande "_ng generate component product-alerts_".
 
3. Dans le fichier "_product-alerts.component.ts_", on y retrouve le décorateur **@Component** qui est une **annotation** et qui définit les métadonnées d'un composant. Dans ce décorateur on y trouve le "_selector_" qui identifie le composant qui sera utilisé dans le HTML via la balise "_app-product-alerts_". On y trouve aussi le "_TemplateUrl_" qui indique le chemin du fichier HTML et le "_StyleUrls_" qui indique une liste de fichiers CSS contenant les styles pour le composant.
  
4. Importation des décorateurs "_Component_" et "_Input_" depuis le module **@angular/core** ce qui va permettre de définir et configurer des composants Angular et de la classe "_Product_".
   
5. On définit une propriété d'entrée "_product_" de type "_Product_" ou "_undefined_" via le décorateur **@Input()** qui permet de passer les données contenues dans "_Product_". Cette propriété d'entrée sera fournie par le composant parent lors de l'utilisation de "_app-product-alerts_".
   
6. On utilise une directive "_*ngIf_" qui va vérifier si la propriété "_product_" existe et si la propriété "_price_" de l'objet "_product_" est supérieur à 700 qui dans ce cas si c'est true affichera un bouton "_Notify Me_".
   
7. Ajout automatique de la classe "_ProductAlertsComponent_" dans le fichier "_app.module.ts_" où on y trouve le décorateur **@NgModule** utilisé pour configurer un module en spécifiant les composants, directives qui appartiennent à ce module sous forme de tableau nommé "_declarations_".
   
8. Dans la balise "_app-product-alerts_" on ajoute une liaison de propriété qui passe la valeur de la propriété "_product_" du composant parent au composant "_app-product-alerts_", ce qui permet de transmettre des données du composant parent au composant enfant et d'intéragir avec le composant "_app-product-alerts_" en fonction de la valeur de "_product_".

### 3. Transmettre des données à un composant parent

1. Dans le fichier "_product-alerts.component.ts_" on importe en plus des décorateur, "_Component_" et "_Input_" et de la classe "_Product_", le décorateur "_Output_" qui va permettre de déclarer une propriété de sortie dans le composant et la classe "_EventEmitter_" qui va permettre de créer un objet émettant des événements personnalisés.

2. Dans la classe "_ProductAlertsComponent_" on configure le composant avec une propriété d'entrée "_product_" qui peut être fournie par le composant parent et une propriété de sortie "_notify_" qui va permettre au composant enfant d'émettre un évènement quand quelque chose doit être notifié.

3. Mise à jour du bouton "_Notify Me_" dans le fichier "_product-alerts.component.html_" en ajoutant l'évènement "_(click)_" qui réagira au clic de la souris sur le bouton et appellera la fonction "_emit()_" dela propriété "_notify_".

4. Ajout dans la classe "_ProductListComponent_" du fichier "_product-list.component.ts_" de la méthode "_onNotify()_" qui lorsqu'elle sera appelé, ouvrira une boîte de dialogue pour afficher le message que l'utilisateur sera notifié quand le produit sera en vente.

5. Par la même occasion dans le fichier "_product-list.component.ts_", on ajoute une liaison d'évènement qui écoute l'évènement "_notify_" émis par le composant "_app-product-alerts_" et appelle la méthode "_onNotify()_" du composant parent en réponse à cet évènement.
  
### 4. Et après

Bah je vais aller me coucher après avoir pris une boîte complète d'Ibuprofène et avoir vidé une bouteille entière de J&D ...

![](https://github.com/Keitaroblaster/Angular/blob/main/elwjcajd.jpg?raw=true)

## II. Ajout de la navigation
### 1. Associer un chemin URL à un composant

1. On crée un nouveau composant via le terminal en tapant la commande "_ng generate component product-details_".

2. Dans le décorateur **@NgModule** du fichier "_app.module.ts_" on va ajouter dans le module "_RouterModule_" qui fournit des fonctionnalités de routage pour la navigation, la route qui est associée aux pages de détails de produit où "_:productId_" est un paramètre dynamique qui peut être passé dans l'URL. Le composant "_ProductDetailsComponent_" est ainsi chargé quand le chemin est atteint.

3. Dans le fichier "_product-list.component.html_" on met à jour l'ancre en ajoutant la directive "_[routerLink]_"pour créer un lien de navigation en pointant vers le chemin "_/products_" avec l'Id spécifique du produit "_product.id_".

### 2. Afficher les détails du produit

1. On met à jour le fichier "_product-details.component.ts_" en important le décorateur "_OnInit_" que le composant implémente l'interface "_OnInit_" et la classe "_ActivatedRoute_" afin d'accéder aux informations associées à la route active.

2. On définit la classe "_ProductDetailsComponent_" qui a une propriété "_product_" de type "_Product_" ou "_undefined_" et qui va implémenter l'interface "_OnInit_" qui appellera la méthode "_ngOnInit_" lors de l'initialisation du composant.

3. On y ajoute dans la classe "_ProductDetailsComponent_" le constructeur qui prend en paramètre une instance de la classe "_ActivatedRoute_" et l'assigne à la propriété privée "_route_" ce qui permettra à la classe d'accéder aux informations "_ActivatedRoute_".

4. Dans le fichier "_product-details.component.ts_", on créé la méthode "_ngOnInit_" qui sera appelée lors de l'initialisation du composant. Cette méthode va utiliser dans un 1er temps les informations de "_route_" via la constante "_routeParams_" avec "_snapshot_" qui est la propriété d'_ActivatedRoute_ et représente une capture instantanée des informations de route au moment de la navigation et "_paramMap_" qui contient les paramètres de la route sous forme de map, pour extraire l'Id du produit à partir de l'URL via la constante "_productIdFromRoute_" avec "_routeParams.get('productId')_" qui va permettre de récupérer la valeur du paramètre "_productId_" de l'URL en tant que chaîne de caractères pour ensuite être convertit en un nombre entier par la méthode "_number()_". Puis une fois l'Id extraite la méthode va permettre de rechercher le produit correspondant dans une liste de produits et l'assigne à la propriété "_product_" de la classe.

5. On finit en mettant à jour le fichier "_product-details.component.html_" afin d'afficher les détails d'un produit uniquement si la propriété "_product_" existe et affichera le nom, le prix et la description du produit.

### 3. Et après

Bah ....

![](https://raw.githubusercontent.com/Keitaroblaster/Angular/main/why.webp)

## III. Gestion des données
### 1. Créer le service de panier d'achat
#### 1.1 Définir un service de panier

1. On va créer un nouveau composant via le terminal en tapant la commande "_ng generate service cart_".

2. Dans le fichier "_cart.service.ts_" on importe la classe "_Product_". Le décorateur **@Injectable** est utilisé pour indiquer qu'une classe peut être injectée avec des dépendances et "_providedIn:'root'_" indique qu'une seule instance de ce service sera partagée par toute l'application. Puis déclaration dans la classe "_CartService_" de la propriété "_items_" qui sera un tableau de produits initialisé vide.

3. Dans la classe "_CartService_" on définit des méthodes pour la gestion du panier :
   
     - Dans un 1er temps on définit une méthode "_addToCart(product: Product)_" qui prend en paramètre un "_product_" de type de la classe "_Product_" et va ajouter un produit au panier grâce à "_this.items.push(product)_" qui va permettre d'ajouter le produit à la fin du tableau "_items_" du panier.
  
     - Dans un 2eme temps on définit une méthode "_getItems()_" qui va retourner les produits présents dans le panier.
  
     - Puis dans un dernier temps on définit une méthode "_clearCart()_" qui va permettre de vider le panier en réinitialisant le tableau grâce au "_this.items = []_" qui attribue un tableau vide à la propriété "_items_" et le retourne avec "_return this.items_".

#### 1.2 Utiliser le service de panier

1. Importation de la classe "_CartService_" dans le fichier "_product-details.component.ts_" pour accéder à la fonctionnalité fournie par le service pour ajouter des produits au panier. Puis on initialise la propriété "_cartService_" de type de la classe "_CartService_" dans le constructeur de la classe "_ProductDetailsComponent_".

3. Ajout dans la classe "_ProductDetailsComponent_" de la méthode "_addToCart(product: Product)_" qui va faire appelle au service "_cartService_" qui va appeler la méthode "_addToCart_" avec le produit en argument ce qui ajoutera le produit au panier puis afficher une alerte pour informer l'utilisateur que son produit est bien dans le panier.

4. Dans le fichier "_product-details.component.html_" on met en place un bouton d'évènement "_Buy_" qui lorsque l'utilisateur cliquera sur ce bouton, cela fera appel à la méthode "_addToCart(product)_" qui ajoutera le produit au panier.

### 2. Créer la vue du panier
#### 2.1 Configurer le composant panier

1. On va créer un nouveau composant via le terminal en tapant la commande "_ng generate component cart_".

3. Dans le fichier "_app.module.ts_", on définit le chemin vers l'URL "_/cart_" qui quand il sera atteint, le composant "_CartComponent_" sera chargé et affiché.

4. Mise à jour du bouton "_payer_" dans le fichier "_top-bar.component.html_" avec une directive "_routerLink_" qui point vers l'URL "_/cart_".

#### 2.2 Afficher les articles du panier

1. Importation de la classe "_CartService_" dans le fichier "_cart.component.ts_" puis on ajoute au constructeur de la classe "_CartComponent_" la propriété "_cartService_" de type de la classe "_CartService_".

3. On définit la propriété "_items_" qui va permettre d'enregistrer dans le panier le produit sélectionné en appelant la méthode "_getItems()_" dont la valeur retournée sera attribuée à la variable "_items_".

4. Dans le fichier "_cart.component.html_", ajout d'une directive "_*ngFor_" qui va itérer sur la liste "_items_" afin d'afficher via l'interpolation le nom et le prix de l'article.

### 3. Récupérer les prix d'expédition
#### 3.1 Configurer AppModule pour utiliser HttpClient

1. Importation du module "_HttpClientModule_" dans le fichier "_app.module.ts_" qui va fournir les fonctionnalités liées à la gestion des requêtes HTTP dans les applications pour récupérer ou envoyer des données vers un serveur.

#### 3.2 Configurer CartService pour utiliser HttpClient

1. Importation de la classe "_HttpClient_" dans le fichier "_cart.service.ts_" afin de pouvoir récupérer des données et intéragir avec des API et des ressources externes puis ajout au constructeur de la classe "_CartService_" la propriété "_http_" de type de la classe "_HttpClient_".

#### 3.3 Configurer CartService pour obtenir les prix d'expédition

1. Après la configuration pour pouvoir utiliser "_HttpClient_" et permettre la récupération des données, il faut pouvoir récupérer les données d'expédition à partir d'un fichier "_shipping.json_". On définit une méthode "_getShippingPrices()_" dans la classe "_CartService_" du fichier "_cart.service.ts_" qui utilisera la méthode "_get()_" vers le fichier JSON qui contient les prix d'expéditions.

### 4. Créer un composant d'expédition

1. On va créer un nouveau composant via le terminal en tapant la commande "_ng generate component shipping_" qui va nous permettre d'afficher les données d'expédition.

2. Dans le fichier "_app.module.ts_" on ajoute le chemin pour l'expédition dans **@NgModule** -> **RouteurModule.forRoot** -> **{path: "shipping", component:ShippingComponent}**,

#### 4.1 Configuration du ShippinComponent pour utiliser CartService

1. Afin de récupérer les données d'expédition depuis le fichier "_shipping.json_" via le Http, on importe "_CartService_" dans le fichier "_shipping.component.ts_".

2. Dans la classe "_ShippingComponent_", on crée le constructeur prenant en paramètre la propriété "_cartService_" de type de la classe "_CartService_".

3. On définit la propriété "_shippingCosts_", qui ne sera pas intialisée dans le constructeur, de type "_Observable_" sous forme de tableau d'objets avec les propriétés "_type_" de type String et "_price_" de type number. Ensuite on crée une méthode "ngOnInit_" qui sera appelé quand le composant sera initialisé et permettra de récupérer les coûts d'expédition via la méthode "_getShippingPrices()_" et assigner la valeur à "_ShippingCosts_".

4. On met à jour le fichier "_shipping.component.html_" en configurant le modèle d'affichage des expéditions et leur prix avec une directive "_*ngFor_" pour les expéditions en mode async ce qui permet de renvoyer la dernière valeure de façon automatique jusqu'à ce que le composant s'arrête.

5. Mise à jour du fichier "_cart.component.html_" en rajoutant le chemin vers l'URL "_/shipping_" qui permettra d'afficher les prix d'expédition.

## IV. Utilisation de formulaires pour la saisie utilisateur
### 1. Définir le modèle de formulaire de paiement

2. Importation dans le fichier "_cart.component.ts_" de la classe "_FormBuilder_" pour fournir des utilitaires pour la création et la gestion de formulaires dans l'application.

3. On initialise dans le constructeur de la class "_CartComponent_" la propriété "_formBuilder_" de type de la classe "_FormBuilder_" puis on définit une méthode "_group()_" du "_FormBuilder_" pour récupérer des données.

3. On appelle la méthode "_clearCart()_" de "_cartService_" pour effacer le contenu du panier et assigner les éléments du panier à la propriété "_items_" puis afficher une fenêtre de confirmation et la valeur du formulaire dans la console du navigateur pour ensuite réinitialiser le formulaire pour une nouvelle entrée.

### 2. Créer le formulaire de paiement

1. Dans le fichier "_cart.component.html_" on crée un élément HTML "_form_" dans lequel on assigne un attribut "_[formGroup]_" pour lier le formulaire à un objet "_FormGroup_" via l'instance "_checkoutForm_" puis on ajoute un bouton pour soumettre le formulaire via la liaison d'évènement "_ngSubmit_" qui appellera la méthode "_onSubmit()_".

2. On ajoute ensuite des balises "_input_" afin de saisir les valeurs correspondants aux champs et les lier au "_checkoutForm_".

### 3. Et après

![](https://github.com/Keitaroblaster/Angular/blob/main/144-1448635_homer-simpson-lying-down-hd-png-download.png?raw=true)

