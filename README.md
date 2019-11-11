# Bercé, une forêt d'exception

Le site est propulsé par [Hugo](https://gohugo.io/documentation/).

La documentation n'est pas des plus simples, donc voici en résumé les points clés pour maintenir
à jour le site.

Le thème actuellement utilisé se nomme `ananke`.
Afin de réaliser le visuel principal, il faut une image d'au moins `1440 px` de large.


## Images

Les images sont à sauvegarder dans le dossier suivant:
> /static/images

Pour créer le visuel principal de chaque page, je te propose de toujours repartir de celui de
la page d'accueil. Il possède les dimensions suivantes `1440x642 px`:
> /static/images/foret-de-berce.jpg

Ce dernier est présent tout en haut du fichier Markdown :
`featured_image: "/images/articles/curiosites.jpg"`

Pour les articles, c'est ici:
> /static/images/articles

Partons du principe que toutes les images servant d'illustration au sein des articles font au
maximum `500 px` de large.

Avant de les utiliser sur le site, elles doivent être optimisées avec [tinypng](https://tinypng.com/)
pour réduire leur poids.

Pour ajouter une image, c'est le shotcode [figure](#figure) qu'il faut utiliser :
```
{{<figure src="/images/articles/plan-berce-1783.jpg" title="Plan de la forêt de Bercé en 1783">}}
```

## Contenus

L'ensemble du contenu se trouve dans le dossier `content` à la racine du projet.
Il y a actuellement 2 catégories `A propos` et `Articles`.
Chaque dossier de catégorie, y compris principal possède un fichier `_index.md` qui décrit
le comportement / texte de l'accueil.

Tous les articles se trouvent actuellement au sein du dossier `content/articles`, un fichier `.md`
pour markdown par page.
Nom de l'article en minuscule, sans accent avec un tiret pour les espaces.


## Markdown

Quelques bons guides pour apprendre la syntaxe Markdown avec des exemples :
+ https://docs.microsoft.com/fr-fr/contribute/how-to-write-use-markdown
+ https://guides.github.com/features/mastering-markdown/ (en anglais)


## Shortcodes

### figure

`figure` est une extension de la syntaxe pour une image en Markdown.
Il peut avoir les paramètres suivants : 

+ *src* : URL de l'image à afficher.
+ *link* : Si l'image doit être cliquable, l'URL de destination.
+ *target* : Si `link` est définie, permet d'ouvrir dans nouvelle page via `_blank`.
+ *alt* : Texte alternatif pour l'image.
+ *title* : Titre de l'image.
+ *caption* : Légende de l'image.
+ *class* : CSS classe.
+ *height* : Hauteur de l'image.
+ *width* : Largeur de l'image.
+ *attr* : Texte d'attribut de l'image
+ *attrlink* : Si l'attribut texte est définie et doit être cliquable, l'URL de destination.

Exemple de `figure`:

`{{<figure src="/images/articles/plan-berce-1783.jpg" title="Plan de la forêt de Bercé en 1783">}}`


### ref / relref

`rel` permettra de faire des liens au sein des différentes pages du site.
`relref` fait de même mais plus précisement puisqu'il permet d'accéder direction à une partie du site
par son ancre. Une ancre est créé pour chaque titre.
Sa valeur est le titre en minuscule et un tiret à la place des espaces.

Exemples de `rel` et `relref`:

```markdown
[Lieux Mythiques]({{<ref "articles/lieux-mythiques.md">}})
[La coudre]({{< relref "articles/lieux-mythiques.md#la-coudre" >}})
```
[Lieux Mythiques]({{<ref "articles/lieux-mythiques.md">}})
[La coudre]({{< relref "articles/lieux-mythiques.md#la-coudre" >}})

### youtube

Le shortcode `youtube` permet d'afficher un lecteur vidéo dédié aux vidéos présente sur Youtube.
Seul l'ID de la vidéo est requis., e.g.: `https://www.youtube.com/watch?v=w7Ft2ymGmfc`

Exemple youtube:

Copier l'ID de la vidéo YouTube qui suit `v=` dans l'URL and le passer au passer au shortcode:

`{{<youtube HRxGl709GUA>}}` ou ```{{<youtube id="HRxGl709GUA">}}```

{{<youtube HRxGl709GUA>}}

Tu peux de plus démarrer automatiquement la vidéo en paramétrant à `true` le paramètre `autoplay`.

> Note : on ne peut pas mélanger les paramètres nommés et non nommés, donc ici seule la syntaxe suivante est possible.

`{{<youtube id="w7Ft2ymGmfc" autoplay="true">}}`