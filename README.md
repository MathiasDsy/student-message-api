API Messages pour Système de Gestion des Effectifs Étudiants

Cette API permet de gérer les messages des étudiants dans un système de gestion des effectifs. Elle permet la création, la mise à jour, la suppression et la récupération des messages associés aux étudiants.
La base de données se base sur mongoDB, un docker compose se trouve dans le dossier.


Installation

Clonez ce repository sur votre machine locale :

git clone https://github.com/mathiasdsy/student-message-api.git
cd student-message-api

Créer l'image docker avec docker compose up

Utilisation

L'API expose plusieurs endpoints pour interagir avec les messages des étudiants.
Créer un message

POST /api/messages

Permet de créer un nouveau message pour un étudiant. Vous devez envoyer une requête POST avec les informations du message dans le corps de la requête (format JSON).

Exemple de corps de la requête :

{
  "texte": "Votre demande a été traitée.",
  "sujet": "Mise à jour de votre demande",
  "etudiantId": 12345
}

Réponse :

{
  "id": "60c72b2f5f1b2c001c8f2e2e",
  "texte": "Votre demande a été traitée.",
  "lu": false,
  "dateCreation": "2023-05-20T14:45:00Z",
  "sujet": "Mise à jour de votre demande",
  "etudiantId": 12345
}

Récupérer un message spécifique

GET /api/messages/{id}

Permet de récupérer un message par son ID. Remplacez {id} par l'identifiant du message.

Réponse :

{
  "id": "60c72b2f5f1b2c001c8f2e2e",
  "texte": "Votre demande a été traitée.",
  "lu": false,
  "dateCreation": "2023-05-20T14:45:00Z",
  "sujet": "Mise à jour de votre demande",
  "etudiantId": 12345
}

Mettre à jour un message

PUT /api/messages/{id}

Permet de mettre à jour un message existant, par exemple pour modifier son statut de lecture ou son contenu.

Exemple de corps de la requête :

{
  "texte": "Votre demande a été entièrement traitée.",
  "lu": true,
  "sujet": "Mise à jour de votre demande"
}

Supprimer un message

DELETE /api/messages/{id}

Permet de supprimer un message spécifique par son ID.

Réponse :

{
  "message": "Message supprimé avec succès"
}

Récupérer les messages d'un étudiant

GET /api/messages/etudiants/{id}

Permet de récupérer tous les messages associés à un étudiant par son ID. Vous pouvez également filtrer les messages par statut de lecture (lu/non lu).

Exemple de requête :

/api/messages/etudiants/12345?lu=true

Réponse :

[
  {
    "id": "60c72b2f5f1b2c001c8f2e2e",
    "texte": "Votre demande a été traitée.",
    "lu": true,
    "dateCreation": "2023-05-20T14:45:00Z",
    "sujet": "Mise à jour de votre demande",
    "etudiantId": 12345
  }
]

Structure de l'API

L'API utilise les méthodes HTTP suivantes pour interagir avec les messages :

    POST /api/messages pour créer un message
    GET /api/messages/{id} pour récupérer un message par son ID
    PUT /api/messages/{id} pour mettre à jour un message
    DELETE /api/messages/{id} pour supprimer un message
    GET /api/messages/etudiants/{id} pour récupérer les messages d'un étudiant

Licence

Ce projet est sous licence MIT. Voir le fichier LICENSE pour plus de détails.
