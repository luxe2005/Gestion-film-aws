 Projet : API de Films Sans Serveur avec AWS

Ce projet met en œuvre une API sans serveur qui permet de récupérer des informations sur des films, telles que leurs titres, leurs années de sortie et des résumés fictifs. L’infrastructure repose sur AWS Lambda, DynamoDB, S3, et API Gateway.

---

**Fonctionnalités**
1. **GetMovies** : Retourne tous les films enregistrés.
2. **GetMoviesByYear** : Retourne les films publiés lors d'une année spécifique.
3. **GetMovieSummary** : Retourne un résumé fictif pour un film donné.

---

 **Architecture**
- **DynamoDB** : Stocke les informations des films (titre, année de sortie, genre, URL de l'image de couverture).
- **S3** : Héberge les images des films.
- **Lambda** : Contient le code exécuté pour chaque fonction.
- **API Gateway** : Expose les fonctions Lambda via des endpoints REST.


**Prérequis**
- Un compte AWS actif.
- AWS CLI configuré avec des permissions IAM appropriées.
- Postman ou un outil similaire pour tester les endpoints API.


 **Instructions**

**1. Création de la Base de Données DynamoDB**

Créer une table DynamoDB :
```bash
aws dynamodb create-table \
    --table-name Movies \
    --attribute-definitions AttributeName=title,AttributeType=S \
    --key-schema AttributeName=title,KeyType=HASH \
    --provisioned-throughput ReadCapacityUnits=5,WriteCapacityUnits=5

