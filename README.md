# CM COMPANY — Ice Shop

Site web complet pour une entreprise de vente de glaçons alimentaires.

## Stack technique

| Couche | Technologie |
|---|---|
| Frontend | HTML, CSS, JavaScript |
| Backend | Java 17, Spring Boot 4, Spring Security |
| Base de données | PostgreSQL 16 |
| Authentification | JWT (JSON Web Token) |
| Déploiement | Docker, Docker Compose |

## Fonctionnalités

- Inscription et connexion avec JWT
- Pages protégées (Services accessible uniquement aux utilisateurs connectés)
- Catalogue de produits chargé depuis la base de données
- Déconnexion automatique
- API REST sécurisée

## Structure du projet

```
prgice/
├── frontend/          # Pages HTML/CSS/JS
│   ├── index.html
│   ├── login.html
│   ├── services.html
│   ├── about.html
│   ├── gallerie.html
│   └── ...
├── backend/           # API Spring Boot
│   ├── src/
│   │   └── main/java/.../
│   │       ├── auth/          # Inscription & connexion
│   │       ├── products/      # Gestion des produits
│   │       ├── users/         # Entité utilisateur
│   │       └── security/      # JWT, CORS, Spring Security
│   ├── Dockerfile
│   └── pom.xml
├── docker-compose.yml
└── .env.example
```

## Lancer le projet

### Prérequis

- [Docker Desktop](https://www.docker.com/products/docker-desktop/)

### Installation

**1. Clone le projet**
```bash
git clone https://github.com/mehdichaaban/Projet-web-Mohamed-Mehdi-Chaabane.git
cd Projet-web-Mohamed-Mehdi-Chaabane
```

**2. Configure les variables d'environnement**
```bash
cp .env.example .env
```
Ouvre `.env` et remplis les valeurs :
```
DATASOURCE_USERNAME=ice_user
DATASOURCE_PASSWORD=ton_mot_de_passe
JWT_SECRET=une_chaine_aleatoire_minimum_64_caracteres
```

**3. Lance tout avec Docker**
```bash
docker-compose up --build
```

### Accès

| Service | URL |
|---|---|
| Frontend | http://localhost:3000 |
| Backend API | http://localhost:8080 |

## API Endpoints

### Authentification

| Méthode | Route | Description | Auth requise |
|---|---|---|---|
| POST | `/api/auth/register` | Créer un compte | Non |
| POST | `/api/auth/login` | Se connecter | Non |

### Produits

| Méthode | Route | Description | Auth requise |
|---|---|---|---|
| GET | `/api/products` | Liste des produits | Non |
| GET | `/api/products/{id}` | Un produit | Non |
| POST | `/api/products` | Créer un produit | Oui |
| PUT | `/api/products/{id}` | Modifier un produit | Oui |
| DELETE | `/api/products/{id}` | Supprimer un produit | Oui |

### Exemple d'utilisation

**Inscription :**
```bash
curl -X POST http://localhost:8080/api/auth/register \
  -H "Content-Type: application/json" \
  -d '{"email":"user@example.com","password":"123456"}'
```

**Réponse :**
```json
{
  "token": "eyJhbGciOiJIUzI1NiJ9..."
}
```

## Sécurité

- Mots de passe hashés avec **BCrypt**
- Authentification sans session (**Stateless JWT**)
- Protection **CORS** configurée
- Variables sensibles dans `.env` (jamais commitées)
- Routes protégées par **Spring Security**

## Auteur

**Mohamed Mehdi Chaabane**
