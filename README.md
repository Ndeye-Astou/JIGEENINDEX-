# JIGEENINDEX

**Observatoire numérique national des conditions des femmes et des filles au Sénégal**  
Porté par l'association JEADER — https://jigeenindex.org/

JIGEENINDEX collecte, structure, documente, vérifie, analyse et diffuse des données fiables sur les conditions de vie, les droits, les opportunités et les inégalités vécues par les femmes et les filles au Sénégal. La plateforme doit produire une information utile aux institutions, chercheurs, organisations et partenaires.

> **État initial :** dépôt initialisé avec les documents de cadrage et les règles de développement. Le produit applicatif n'est pas encore implémenté. Aucune donnée, API, validation scientifique ou mise en production ne doit être considérée comme acquise sans preuve vérifiable.

## Principes fondamentaux

- Priorité statistique aux femmes et aux filles ; les comparaisons femmes-hommes sont complémentaires.
- Couverture des 14 régions du Sénégal.
- Toute valeur publiée doit être sourcée, datée, contextualisée et méthodologiquement documentée.
- Aucune donnée fictive ne doit être présentée comme officielle.
- Toute donnée suit un circuit de contrôle et de validation avant publication.
- Le back-office doit permettre la gestion des contenus et données sans modification du code.
- Les permissions sont contrôlées côté serveur et par PostgreSQL RLS.
- Les signalements confidentiels sont isolés du système statistique public.
- Les décisions scientifiques sont validées par les personnes compétentes désignées par JEADER.

## Stack cible

Next.js App Router, TypeScript strict, Tailwind CSS, Supabase (PostgreSQL, Auth, Storage), Supabase RLS, Vercel, GitHub, Zod, Vitest et Playwright.

## Documents à lire avant de coder

1. AGENTS.md — règles communes pour Codex et les agents de code.
2. CLAUDE.md — consignes spécifiques Claude Code.
3. docs/CAHIER-DES-CHARGES-TECHNIQUE.md — exigences produit et architecture.
4. docs/PLAN-DE-REALISATION.md — phases, tests et critères de réception.

Le premier travail de développement consiste à établir le socle, les migrations, les permissions et les tests. Ne pas commencer par une landing page isolée.

## Sources à qualifier

- ANSD : https://www.ansd.sn/bases-de-donnees
- ODP régional : https://odpregional.statsenegal.sn/
- Banque mondiale Sénégal : https://donnees.banquemondiale.org/pays/senegal
- API Banque mondiale : https://api.worldbank.org/v2/
- ONU Femmes Sénégal : https://africa.unwomen.org/fr/where-we-are/west-and-central-africa/senegal_africa
- CDP Sénégal : https://www.cdp.sn/ — référence réglementaire sur les données personnelles, pas une source statistique.

Disponibilité des API, formats, licences, autorisations et fréquences restent à vérifier. Ne jamais scraper sans vérifier les conditions d'utilisation.

## Environnements et propriété

Prévoir développement, staging et production. Les secrets ne doivent jamais être committés. Les comptes de production devraient appartenir à JEADER, avec des accès techniques attribués selon les responsabilités convenues. La propriété du code, la maintenance, le budget et les modalités de réception doivent être formalisés.

## Qualité

Une fonctionnalité n'est terminée que si ses parcours, erreurs, validations serveur, permissions, politiques RLS et tests sont vérifiés ; si la documentation est à jour ; et si aucune donnée fictive n'est présentée comme officielle.
