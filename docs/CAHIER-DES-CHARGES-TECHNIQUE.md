# Cahier des charges technique — JIGEENINDEX
Version 1.1

## 1. Finalité
JIGEENINDEX est un observatoire numérique national porté par JEADER. Il collecte, structure, documente, vérifie, analyse et diffuse des informations statistiques sur les conditions des femmes et des filles au Sénégal. Il doit soutenir la compréhension des réalités territoriales, le suivi des évolutions et l'élaboration de politiques publiques fondées sur des données probantes.

Distinguer explicitement les statistiques officielles, les résultats d'études/enquêtes, les données de contributeurs, les calculs produits par JIGEENINDEX et les contenus éditoriaux.

## 2. Territoire et piliers
Couverture nationale : 14 régions. Départements et communes seulement si les nomenclatures et données sont disponibles et cohérentes.

Piliers administrables :
1. Inclusion sociale et pauvreté.
2. Alimentation et sécurité alimentaire.
3. Santé et protection sociale.
4. Éducation de qualité.
5. Inclusion politique et gouvernance.
6. Eau, assainissement et énergie.
7. Travail décent et croissance économique.
8. Innovation et infrastructures.
9. Justice et réduction des inégalités.

Le site existant a mentionné 55 indicateurs. Leur inventaire, définition, disponibilité, qualité et validation sont à auditer ; ce nombre ne constitue pas une validation scientifique.

## 3. Publics
Décideurs et institutions ; chercheurs et analystes ; organisations de femmes et société civile ; partenaires techniques et financiers ; organisations contributrices ; équipe JEADER.

## 4. Site public
- Portail institutionnel : mission, présentation, piliers, partenaires, actualités, publications, contact.
- Dashboard national : indicateurs validés, tendances, filtres, comparaisons, périodes, sources, unités, notes méthodologiques et exports.
- Carte interactive des 14 régions : données disponibles par région, période et source ; absence de données clairement indiquée.
- Catalogue : recherche et filtres par pilier, indicateur, territoire, période, population et source.
- Fiches indicateurs : définition, formule, unité, désagrégations, limites, méthode, source et historique.
- Publications, études, rapports PDF, actualités, événements et partenaires.
- Contribution : dépôt sécurisé, accusé de réception, suivi ; aucune contribution publiée automatiquement.
- Signalement confidentiel : uniquement après validation du mandat, cadre légal, protocole, personnes habilitées et dispositif de prise en charge. Ne pas promettre une urgence ou intervention inexistante.

## 5. Back-office
Administrer sans code : pages, sections, navigation, SEO, médias, piliers, catégories, indicateurs, définitions, métadonnées, observations, sources, datasets, connecteurs, imports, validations, publications, actualités, partenaires, événements, utilisateurs, invitations, rôles, permissions, contributions, signalements habilités, paramètres, notifications, journaux et historique.

Fonctions éditoriales : brouillon, aperçu, programmation, publication, dépublication, archivage, restauration et versionnage. Les suppressions irréversibles doivent être limitées et auditées.

Imports CSV/XLSX : dépôt, mapping colonnes, aperçu, validation des types, unités, périodes, territoires, doublons, anomalies, rapport d'erreurs et annulation avant publication.

## 6. Rôles et permissions
Rôles de référence : super administrateur, administrateur général, responsable scientifique, gestionnaire de données, validateur scientifique, éditeur, gestionnaire partenaires, responsable signalements, analyste, contributeur.

Créer un RBAC granulaire : lecture, création, modification, suppression, validation, publication, export, gestion utilisateurs, gestion paramètres et accès restreint aux signalements. Vérifier les droits côté serveur et dans les politiques RLS ; cacher un bouton ne protège pas une ressource.

## 7. Ingestion des données
Deux modes : connecteurs automatiques (API/SDMX/synchronisation) et import manuel (CSV/XLSX/saisie contrôlée).

Pipeline : source qualifiée → collecte brute → conservation de la provenance → mapping/normalisation → contrôles → rapport d'anomalies → revue humaine → validation scientifique → publication versionnée → exposition publique.

Une synchronisation ne doit jamais écraser silencieusement une valeur publiée. Chaque job a un statut, des dates, des logs et une stratégie de reprise. Les secrets de connecteurs restent côté serveur.

## 8. Sources à qualifier
- ANSD : https://www.ansd.sn/bases-de-donnees — source nationale prioritaire ; vérifier catalogue, formats, API éventuelle, licence, accès et métadonnées.
- ODP régional : https://odpregional.statsenegal.sn/ — territoire, exports, SDMX/API éventuels ; vérifier documentation, accès, fréquence, licence et nomenclature.
- Banque mondiale : https://donnees.banquemondiale.org/pays/senegal et https://api.worldbank.org/v2/ — séries socio-économiques ; conserver codes, périodes, unités et limites.
- ONU Femmes Sénégal : https://africa.unwomen.org/fr/where-we-are/west-and-central-africa/senegal_africa — études et ressources ; vérifier réutilisation et méthode.
- CDP : https://www.cdp.sn/ — référence réglementaire de protection des données personnelles, pas source statistique.

Aucune API n'est présumée connectée. Ne pas scraper sans autorisation. Si API indisponible, documenter la limite et maintenir un import manuel contrôlé.

## 9. Architecture
Next.js App Router, TypeScript strict, Tailwind, Supabase PostgreSQL/Auth/Storage, RLS, Vercel, Zod, Vitest et Playwright. Server Components par défaut ; Route Handlers/Server Actions pour les opérations serveur ; services métier séparés des composants ; connecteurs externes côté serveur. Pas de backend Node distinct sans justification.

Couches : présentation publique/admin ; services métier et autorisations ; PostgreSQL/Storage/audit/versionnage ; intégrations et imports ; CI, logs, monitoring, sauvegardes et déploiement.

## 10. Modèle de données indicatif
Sécurité : profiles, roles, permissions, user_roles, role_permissions, audit_logs.
Territoires : regions, departments, communes.
Statistiques : pillars, indicator_categories, indicators, indicator_dimensions, statistical_periods, indicator_observations, indicator_metadata.
Sources : data_sources, datasets, dataset_documents, data_connectors, sync_jobs, sync_logs, data_versions.
Validation : submissions, validation_workflows, validation_steps, validation_comments.
CMS : pages, page_sections, news, publications, publication_categories, partners, media_assets, navigation_menus, navigation_items.
Contributions : organizations, organization_members, contributions, contribution_documents.
Signalements isolés : confidential_reports, report_status_history, report_access_logs.
Administration : system_settings, content_revisions, notification_logs, scheduled_tasks.

Le schéma final doit être normalisé, documenté et migré par SQL versionné, avec clés, contraintes, index, horodatages et règles de suppression. JSONB seulement si justifié.

## 11. Métadonnées minimales d'une observation
Indicateur et version de définition ; valeur brute ; valeur normalisée si transformation ; unité ; période ; territoire ; population/dénominateur ; dimensions disponibles ; source et dataset ; date d'import ; méthode/version ; statut de validation ; validateur ; version publiée et historique.

## 12. Moteur statistique
Calculs possibles si les entrées sont compatibles et la formule documentée : taux, proportions, agrégations, comparaisons temporelles/régionales, écarts femmes-hommes. Documenter numérateur, dénominateur, exclusions, valeurs manquantes, période et version de méthode. Aucun indice composite ou pondération sans approbation scientifique.

## 13. Sécurité et données personnelles
Supabase Auth, RBAC et RLS en défense en profondeur ; validation serveur ; contrôle MIME/taille des fichiers ; rate limiting ; protection XSS/CSRF/injection ; secrets serveur ; audit des opérations sensibles ; minimisation ; conservation définie ; sauvegardes et restauration testée. Données publiques agrégées, sans risque de ré-identification. Cloisonnement strict des signalements. Faire valider le cadre sénégalais applicable par JEADER et ses conseils.

## 14. Design et accessibilité
Design institutionnel, sobre, crédible, authentique et responsive. Français au lancement, architecture prête pour wolof et anglais. Viser WCAG 2.2 AA : clavier, contraste, focus, libellés, alternatives textuelles et graphiques compréhensibles. Utiliser la charte et le logo fournis ou approuvés par JEADER.

## 15. Exigences non fonctionnelles
Maintenabilité par une développeuse ; performance mobile et réseau limité ; traçabilité ; logs sans fuite ; environnements séparés ; tests automatisés ; déploiements réversibles ; sauvegardes et restauration vérifiée.

## 16. Livrables
Site public ; back-office ; schéma et migrations ; Auth/RBAC/RLS ; sources et imports ; validation/versionnage ; catalogue et moteur statistique ; dashboards/carte/exports ; CMS ; contributions ; signalements selon cadre validé ; tests unitaires/intégration/E2E/RLS ; README, architecture, API, dictionnaire de données, guides admin/utilisateur/déploiement, sauvegarde/restauration et rapport de tests.

## 17. Décisions et éléments à obtenir de JEADER
Logo et charte ; inventaire des indicateurs et définitions ; rapports et fichiers sources avec droits ; responsables de validation scientifique ; accès et autorisations aux sources ; protocole de signalement ; propriété des comptes domaine/Supabase/Vercel/GitHub ; propriété du code, maintenance, budget, support et recette.
