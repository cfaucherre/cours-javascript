---
layout: page
title: Manipulation d’objets
permalink: /js/manipulation/
---

Extensions au noyau JS
==

Objets de type BOM:

Window, Navigator, Screen, History, Location

Objets de type DOM:

DOM Document, DOM Elements, DOM Attributes, DOM Events, ...

Objets de type HTML:

```html
<a>, <area>, <canvas>, <button>, <form>, <iframe>, <image>,
<input>, <link>, <meta>, <object>, <option>, <select>, 
<table>, <td>, <th>, <tr>, <textarea>, ...
```

Permet de manipuler le navigateur
 
Tous les navigateurs (IE, Firefox, Chrome, ...) sont des logiciels qui offrent les mêmes fonctionnalités de base
 
Ouvrir/fermer des onglets, aller à une URL, mémoriser la liste des URL précédemment consultées, etc
 
Arborescence d'objets
 
((image))

Méthodes d'interaction avec l'utilisateur par le biais de la fenêtre du navigateur

Utilisation de l'objet window

```javascript
window.alert("Bienvenue sur ce site !");
```

Divers exemples BOM

```javascript
//affiche dans la console le nom de code du navigateur utilisé
console.log(window.navigator.appCodeName);

//redirige le navigateur vers une adresse quelconque
window.location = "http://www.univ-pau.fr";

//ouvre un nouvel onglet dans le navigateur
var onglet = window.open('http://www.youtube.com');

//Fais revenir une page en arrière (similaire au boutton 'Back')
window.history.back();

//Affiche dans une boite de dialogue la résolution de l'écran utilisé
window.alert(window.screen.availWidth + "x" + window.screen.availHeight);

//Ecrit de l'html directement dans le document (et supprime l'existant)
window.document.write("<b>Bienvenue à l'université de Pau</b>");
```

DOM: Document Object Model

Représentation d'un document x(ht)ml sous sa

* Les balises sont des noeuds et leurs imbrications forment une arborescence

L'arbre DOM est chargé dans le navigateur

* L'arbre est parcouru par le moteur de rendu du navigateur afin de produire l'affichage graphique

Document XHTML : exemple

```html
<!DOCTYPE html>
<html>
<body>
    <ul>
    </ul>
  <form>
  </form>
</html>
```

Arbre du document XHTML:

![Arbre du document XHTML](/cours-javascript/img/arbre-DOM.jpg)

**Propriétés d'un nœud:**

**Popriétés** | **Commentaires**
childNodes | nœuds enfants (Array)
firstChild | premier nœud enfant

Navigation dans l'arbre DOM

![Navigation DOM](/cours-javascript/img/DOM-navigation.jpg)

**Méthodes d'un nœud:**

**Méthodes** | **Commentaires**
```createElement()``` | Méthode pour créer un nouvel élément HTML dans le document (div, p, span, a, form, input, etc...).
```createTextNode()``` | Méthode pour créer un nœud texte.
```appendChild()``` | Pour ajouter l'élément créé dans le document. L'élément sera ajouté comme étant le dernier nœud enfant d'un élément parent.
```insertBefore()``` | Pour ajouter l'élément créé avant un autre nœud.
```removeChild()``` | Pour supprimer un nœud.

Accès direct aux nœuds

Par la valeur de **l'attribut id** (si il existe)

```javascript
var result = document.getElementById("intro") ;
// Renverra 0 ou 1 résultat
```  

Par la valeur de **l'attribut class** (si il existe)

var result = document.getElementsByClassName("joli1") ;
// Renverra 0 ou n résultats
```      


Par le **nom de la balise** (Tag en anglais)

```javascript
var result = document.getElementsByTagName("input") ;
// Renverra 0 ou n résultats
```   


Par la valeur de **l'attribut name** (si il existe)

```javascript
var result = document.getElementsByName("news_email") ;
// Renverra 0 ou n résultats
```  

Par **les sélecteurs CSS**  

var result = document.querySelector("p#intro") ;
// Renverra 0 ou 1 résultat, le premier trouvé
```  


```javascript
var result = document.querySelectorAll("ul.joli > li") ;
// Renverra 0 ou n résultats
```

Exemple qui change les couleurs de fond de tout élément ayant la classe ```.example``` :

```javascript
var x = document.querySelectorAll(".example");
var i;
for (i = 0; i < x.length; i++) {
    x[i].style.backgroundColor = "red";
}
```

Mode d'accès : comparaison
===

Accès par navigation dans l'arbre DOM:

```html
<html>
  <head>
      function changeColor() {
        var htmlTag = document.childNodes[0];
        var bodyTag = htmlTag.lastChild;
        var pTag = bodyTag.firstChild;
        pTag.style.color="#0000FF";
      }
    </script>
  </body>
```

Accès direct, par l'attribut ID('foo'): 

```html
<html>
  <head>
      function changeColor() {
        var pTag = document.getElementById('foo');
        pTag.style.color="#0000FF";
      }
  </body>
</html>
```

Objets HTML
===

Après avoir navigué et atteint le nœud de son choix, il faut agir dessus


nœud ```<body>``` ? nœud ```<h1>``` ?, nœud ```<img>``` ? Etc.

Principe : les attributs Html correspondent aux propriétés de l'objet (en notation CamelCase)

```html
<img src="tux.gif" alt="Linux" id="foo"/>
```

```javascript
var imgTag = document.getElementById('foo'); //navigation
imgTag.src = "tux2.gif"; //action !
```

```html
<input type="text" value="" size="5" id="bar"/>
```

```javascript
var inputTag = document.getElementById('bar'); //navigation
inputTag.value = "coucou"; //action !
inputTag.size = inputTag.size * 2; //action !
```