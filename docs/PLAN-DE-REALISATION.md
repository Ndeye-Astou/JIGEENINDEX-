# Plan de réalisation et critères de réception

## Principe
Développer une tranche fonctionnelle à la fois. Une page visuelle ne constitue pas une fonctionnalité terminée. Les données, autorisations, workflows, erreurs et tests doivent réellement fonctionner.

## Phase 0 — Audit et cadrage
Inspecter dépôt, site existant, documents, charte et indicateurs ; qualifier sources, licences, accès et formats ; désigner responsables scientifiques, éditoriaux et des signalements ; consigner décisions et risques.
**Sorties :** rapport d'audit, backlog priorisé, décisions et critères de réception.

## Phase 1 — Socle
Initialiser Next.js App Router, TypeScript strict, Tailwind, lint, formatage, tests et CI ; préparer gestion d'erreurs, logs et environnements.
**Acceptation :** installation reproductible, lint/typecheck/tests/build exécutables et CI verte.

## Phase 2 — Base et sécurité
Créer migrations, référentiels, Auth, profils, rôles, permissions et RLS ; ajouter tests positifs et négatifs et modèle de menace.
**Acceptation :** migrations applicables sur base vierge ; les utilisateurs ne voient et ne modifient que les ressources autorisées.

## Phase 3 — Design system
Layouts public/admin, composants, formulaires, tableaux, états, responsive et accessibilité.
**Acceptation :** parcours principaux cohérents, accessibles sur mobile et desktop.

## Phase 4 — CMS
Pages, sections, navigation, médias, SEO, aperçu, programmation, publication, dépublication, versions, archivage et restauration.
**Acceptation :** un éditeur autorisé gère le contenu sans code ; les autres rôles ne peuvent pas publier.

## Phase 5 — Référentiel statistique
Territoires, piliers, catégories, indicateurs, périodes, unités, dimensions, métadonnées, sources et datasets.
**Acceptation :** fiches indicateurs traçables et versionnées ; aucune observation non validée n'est publique.

## Phase 6 — Imports et connecteurs
Import CSV/XLSX, mapping, aperçu, contrôles, doublons, rapport d'erreurs, rollback ; connecteurs API/SDMX après vérification de documentation et droits ; logs et reprise ; workflow humain de validation.
**Acceptation :** import de fichier de test documenté et rapport vérifiable ; aucune connexion annoncée sans test réel.

## Phase 7 — Calculs et visualisations
Services de calcul documentés, dashboard, filtres, comparaisons, carte des 14 régions et exports.
**Acceptation :** résultats reproductibles depuis observations validées ; source, période, unité et limites visibles.

## Phase 8 — Contenus et partenaires
Publications, actualités, événements, partenaires et médiathèque.
**Acceptation :** cycle éditorial complet et permissions testées.

## Phase 9 — Contributions et signalements
Espace de contribution ; signalements seulement après validation du mandat, protocole, cadre légal, conservation et personnes habilitées.
**Acceptation :** tests de non-divulgation ; aucun rôle non habilité ne peut lire ou exporter un signalement.

## Phase 10 — Assurance qualité
Tests unitaires, intégration, E2E, RLS, dépendances, secrets, sécurité, performance, accessibilité, sauvegarde/restauration et revue scientifique.
**Acceptation :** rapport de tests réel ; anomalies critiques corrigées ou formellement acceptées.

## Phase 11 — Préproduction et transfert
Déploiement staging, recette JEADER, corrections, validation, production, domaine, sauvegardes, guides, formation et support.
**Acceptation :** recette formelle, accès remis, sauvegarde restaurable, documentation et plan de maintenance.

## Règles Git
Une branche par lot ; Pull Request vers main ; description des changements, migrations, variables, risques et tests exécutés. Ne pas fusionner si les contrôles requis échouent. Ne jamais committer secrets, fichiers .env ou données personnelles.
