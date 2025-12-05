# Readme
## Pràctiques (reptes) i projecte de Docker i Apache HTTP Server
# Índex
## Introducció i Objectius
## Part 1: Fonaments de Docker
## Part 2: Dockerfile - Creant les Nostres Pròpies Imatges
## Part 3: Apache HTTP Server - Configuració Bàsica
## Part 4: Configuració Avançada d'Apache
## Part 5: Docker Compose - Orquestració de Contenidors
## Part 6: Projecte Final

# Introducció i Objectius

# Part 1: Fonaments de Docker
<img width="683" height="685" alt="image" src="https://github.com/user-attachments/assets/2c5ff8f0-53ea-4617-8c21-b95c9802912e" />
<img width="886" height="138" alt="image" src="https://github.com/user-attachments/assets/bce90dd2-7263-4503-bbe0-8d6d90edb279" />
<img width="886" height="795" alt="image" src="https://github.com/user-attachments/assets/21f3f9b4-ae58-42c9-ae3f-471676bed004" />
<img width="886" height="574" alt="image" src="https://github.com/user-attachments/assets/70d135fc-7c25-4026-801d-c47e19295ffa" />
<img width="777" height="824" alt="image" src="https://github.com/user-attachments/assets/65d2a9cb-9efe-4cd4-86d9-40bb9b70140e" />
  
# Part 2: Dockerfile - Creant les Nostres Pròpies Imatges
<img width="756" height="491" alt="image" src="https://github.com/user-attachments/assets/c4654da9-0897-43d2-ac94-66296a8757fb" />
<img width="644" height="394" alt="image" src="https://github.com/user-attachments/assets/8882fbbf-8894-4b87-9010-d4c45a541d02" />
<img width="598" height="466" alt="image" src="https://github.com/user-attachments/assets/734d0f26-d07c-4271-b2e7-2120d0fdd2e3" />
<img width="599" height="473" alt="image" src="https://github.com/user-attachments/assets/de46c252-ac4a-43ae-9225-980f12fc811e" />
<img width="849" height="234" alt="image" src="https://github.com/user-attachments/assets/a8215e98-dac3-4bc0-af72-9cd7e0abc697" />
 
# Part 3: Apache HTTP Server - Configuració Bàsica
<img width="791" height="388" alt="image" src="https://github.com/user-attachments/assets/6014e5a3-9541-40ea-a628-663da2010f1a" />
<img width="806" height="154" alt="image" src="https://github.com/user-attachments/assets/c2bd5854-6fa2-445c-96ac-705f812b1a21" />
<img width="810" height="630" alt="image" src="https://github.com/user-attachments/assets/b4a831cc-2a11-48a4-b41d-fbb211d13863" />
<img width="886" height="538" alt="image" src="https://github.com/user-attachments/assets/14369dc1-88cd-4301-a364-6b9e057fc47f" />
<img width="1029" height="333" alt="image" src="https://github.com/user-attachments/assets/9f510847-e5de-424b-ad54-79e7a85ff97f" />
### Parem el servei y eliminem totes les copies dels exemples d’abans i fem la redirecció.

# Part 4: Configuració Avançada d'Apache
<img width="886" height="402" alt="image" src="https://github.com/user-attachments/assets/faa9fb7c-e3de-42b2-b414-0507b111410e" />
<img width="886" height="381" alt="image" src="https://github.com/user-attachments/assets/7ab9083c-6fb6-4aa5-8d50-bc0d4b1e163c" />
<img width="886" height="595" alt="image" src="https://github.com/user-attachments/assets/9600cf09-8762-4908-bfdd-ef746ccded7f" />

# Part 5: Docker Compose - Orquestració de Contenidors
<img width="886" height="882" alt="image" src="https://github.com/user-attachments/assets/779929f4-4f21-4697-87f2-80db26569f3b" />
<img width="886" height="226" alt="image" src="https://github.com/user-attachments/assets/afcc8510-5988-48b2-8044-04721b7e939f" />
<img width="886" height="278" alt="image" src="https://github.com/user-attachments/assets/1ac30038-30de-4ca4-9b6b-80791c052693" />
<img width="886" height="531" alt="image" src="https://github.com/user-attachments/assets/f8d288c5-e4a5-42f7-b670-4f432bb97801" />
 
# Part 6: Projecte Final

He muntat un stack complet amb Apache, MySQL, Redis i phpMyAdmin tot integrat amb Docker Compose.

## Què he fet?

Bàsicament he creat una aplicació web amb:
- Un **frontend** amb PHP que mostra articles i compta les visites
- Una **API REST** per gestionar els articles
- Base de dades **MySQL** per guardar la info
- **Redis** per al comptador de visites (caché)
- **phpMyAdmin** per poder mirar la BD fàcilment

## Com funciona l'arquitectura

He separat tot en dues xarxes:
- `frontend-network`: on està Apache exposat al públic
- `backend-network`: on estan MySQL, Redis i phpMyAdmin (més segur)

Apache és l'únic que està a les dues xarxes perquè ha de poder parlar amb tot.

## Instruccions per arrancar-ho

### Primer: configurar els hosts

Has d'afegir això al fitxer hosts (a Windows està a `C:\Windows\System32\drivers\etc\hosts`):

```
127.0.0.1 frontend.local
127.0.0.1 api.local
```

### Després: arrancar els contenidors

```bash
cd Pica_Alex_ASIX2_Docker_Apache/projecte_final
docker-compose build --no-cache
docker-compose up -d
```

Per comprovar que tot va bé:
```bash
docker-compose ps
```

## On accedir

- **Frontend**: https://frontend.local o http://frontend.local
- **API**: https://api.local o http://api.local
- **phpMyAdmin**: http://localhost:8080 

## Credencials

Per MySQL i phpMyAdmin:
- Usuari: `project_user`
- Password: `project_pass`

Per root de MySQL:
- Usuari: `root`
- Password: `rootpass`

## L'API REST que he creat

| Mètode | Endpoint | Què fa |
|--------|----------|--------|
| GET | /api/articles | Torna tots els articles |
| POST | /api/articles | Crea un article nou |
| GET | /api/stats | Mostra estadístiques |

## Base de dades

He creat dues taules:

**users**: guarda els usuaris (id, username, email, created_at)

**articles**: guarda els articles amb clau forana a users

## Coses de seguretat que he implementat

- HTTPS amb certificats (auto-signats, però funciona)
- Capçaleres de seguretat (HSTS, X-Frame-Options, etc.)
- Variables d'entorn per no posar passwords al codi
- Les dues xarxes separades que he comentat abans

## Estructura del projecte

```
projecte_final/
├── docker-compose.yml      <- aquí defineixo tots els serveis
├── .env                    <- variables d'entorn
├── apache/
│   ├── Dockerfile          <- imatge custom d'Apache+PHP
│   ├── conf/               <- configuracions
│   └── sites/              <- el codi PHP
├── mysql/
│   └── init/               <- script per crear les taules
└── redis/
```

## Problemes que pots tenir

- El navegador es queixarà del certificat perquè és auto-signat, només has d'acceptar-lo
- Si MySQL no va, espera una mica que triga en inicialitzar-se la primera vegada
- Assegura't que els ports 80, 443 i 8080 estan lliures

# Resultats del projecte
## L'aplicació s'inicia correctament amb docker compose up -d
<img width="886" height="421" alt="image" src="https://github.com/user-attachments/assets/a330b1c0-897e-4ed9-a897-c3826fc3024b" />
<img width="799" height="283" alt="image" src="https://github.com/user-attachments/assets/df6a31e3-80e3-4136-93df-e6a3d3531434" />
 
## Es pot accedir als 2 Virtual Hosts configurant /etc/hosts 
<img width="886" height="299" alt="image" src="https://github.com/user-attachments/assets/42d15c68-5844-448e-be8d-29a139cc0e60" />
<img width="821" height="835" alt="image" src="https://github.com/user-attachments/assets/9a8dd8d2-b666-4e4b-9e57-871e8065d7ce" />
<img width="863" height="564" alt="image" src="https://github.com/user-attachments/assets/f0345e8a-3822-41da-8bc8-5b3aaa8d46a6" />
 
## HTTPS funciona correctament (amb avís de certificat auto-signat) 
<img width="711" height="773" alt="image" src="https://github.com/user-attachments/assets/fa6111f2-db03-4ad4-b8c2-102e753dcf10" />
<img width="673" height="607" alt="image" src="https://github.com/user-attachments/assets/04121bc5-2ed8-4400-b561-36c49a53938d" />
<img width="503" height="615" alt="image" src="https://github.com/user-attachments/assets/ed1c8abd-18ca-49fe-9504-b4f7bbd69b98" />
 
## Les peticions HTTP es redirigeixen a HTTPS 
<img width="886" height="368" alt="image" src="https://github.com/user-attachments/assets/87ee24cc-8e39-402a-84c6-c183c4214954" />
 
## La base de dades MySQL conté les taules i dades inicials 
<img width="803" height="609" alt="image" src="https://github.com/user-attachments/assets/f4b106bd-5046-4c44-ab08-c919905f3a44" />
 
## Redis està funcionant i registra visites
<img width="886" height="109" alt="image" src="https://github.com/user-attachments/assets/b92a5e97-687d-427b-bf64-9bdf2b78da49" />
 
## phpMyAdmin permet administrar la base de dades 
<img width="886" height="482" alt="image" src="https://github.com/user-attachments/assets/fcb884ae-50de-4b53-90eb-d7cabe8ec56f" />
  
## L'API retorna JSON vàlid 
<img width="886" height="623" alt="image" src="https://github.com/user-attachments/assets/a2b67b28-656a-419b-8594-64426dfd7b44" />
 
## Els logs es poden consultar des de l'host 
<img width="886" height="285" alt="image" src="https://github.com/user-attachments/assets/4297e133-1d51-45fd-8b48-1c3b7cacbbe7" />

## Implementa un healthcheck personalitzat per a cada servei
<img width="886" height="409" alt="image" src="https://github.com/user-attachments/assets/ad3ac351-af24-46cc-885d-542c3c113d07" />
 
---
Fet per Alex Pica Castro
