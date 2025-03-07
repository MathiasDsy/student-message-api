API Messages pour Système de Gestion des Effectifs Étudiants

Cette API permet de gérer les messages des étudiants dans un système de gestion des effectifs. Elle permet la création, la mise à jour, la suppression et la récupération des messages associés aux étudiants.
Table des matières

Installation
Configuration
Utilisation
    Créer un message
    Récupérer un message spécifique
    Mettre à jour un message
    Supprimer un message
    Récupérer les messages d'un étudiant
Structure de l'API
Licence

Installation

Clonez ce repository sur votre machine locale :

git clone https://github.com/ton-username/gestion-messages-etudiants.git
cd gestion-messages-etudiants

Installez les dépendances nécessaires :

npm install

Configuration

Assurez-vous d'avoir une base de données MongoDB configurée pour le stockage des messages. Si vous utilisez un environnement de développement local, vous pouvez utiliser MongoDB Atlas ou un serveur local MongoDB.

Modifiez le fichier .env pour ajouter votre URI MongoDB et d'autres configurations :

MONGODB_URI=mongodb://localhost:27017/messages
PORT=3000

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
