# Model D'attributs

Geny est basé en partie sur la personnalisation, le fait de pouvoir utiliser Geny non pas comme un jeu a part entière mais comme un outil, et de pouvoir laisser son imagination faire le reste

Ainsi, dés le début Geny a été créé pour laisser au MJ la possibilité d'utiliser les règle de jeu de rôle qui lui plait

Et l'une des partie commune a la plus part des JdR sont les compétences, ou les attributs

On va plus ici parler d'attribut, car le nom, le nombre de PVs etc, ne peut pas vraiment être comptabilisé en tant que "compétences"

Les attribut sont donc une des partie commune a la plupart des JdR mais son contenu est rarement le même en fonction des règles suivies

Certaines règles préconise 3 ou 4 attributs, d'autre plusieurs dizaines, tout de type différent, c'est pour cette raison que Geny propose au MJ de personnaliser le **model d'attribut**

## Ou le trouver

Le model d'attribut peut être personnalisé lors de la création de la partie, en cliquant sur 'plus d'option'

// To Do: mettre tout les autre moyens d'y accèder

## Editer le model

Voici un exemple de code model d'attribut

```json
[
	{"nodeType": "category", "title": "Identité", "content": [
		{"nodeType": "structureNormal", "content": [
			{"nodeType": "attr", "name": "Nom", "vartype": "string"},
			{"nodeType": "attr", "name": "Description", "vartype": "string"},
			{"nodeType": "attr", "name": "Spécialité", "vartype": "string"},
			{"nodeType": "attr", "name": "PVs", "vartype": "numeric"}
		]}
	]},
	{"nodeType": "category", "title": "Compétence", "content": [
		{"nodeType": "structureGrid", "title": "Principales", "content": [
			{"nodeType": "attr", "name": "Force", "vartype": "numeric"},
			{"nodeType": "attr", "name": "Habilité", "vartype": "numeric"},
			{"nodeType": "attr", "name": "Perception", "vartype": "numeric"}
			{"nodeType": "attr", "name": "Résistance", "vartype": "numeric"}
			{"nodeType": "attr", "name": "Mental", "vartype": "numeric"}
		]},
		{"nodeType": "structureGrid", "title": "Secondaires", "content": [
			{"nodeType": "attr", "name": "Charisme", "vartype": "numeric"},
			{"nodeType": "attr", "name": "Courir / Sauter", "vartype": "numeric"},
			{"nodeType": "attr", "name": "Mentir / Convaincre", "vartype": "numeric"},
			{"nodeType": "attr", "name": "Psychologie", "vartype": "numeric"},
			{"nodeType": "attr", "name": "Reflexe", "vartype": "numeric"},
			{"nodeType": "attr", "name": "Discrétion", "vartype": "numeric"},
			{"nodeType": "attr", "name": "Artisanat", "vartype": "numeric"},
		]},
		{"nodeType": "structureGrid", "specials": ["addableElements"], "title": "Talents", "content": []}
	]}
]
```

C'est le model utilisé par Geny Spil (l'ensemble des règle de bases utilisé par Geny)



```javascript
var hljs=function(){"use strict";function e(t){}
```



++ctrl+alt+del++



++a++

*[MJ]: Maitre du Jeu

*[JdR]: Jeu de Rôle

*[PV]: Point de vie

*[PVs]: Points de vie