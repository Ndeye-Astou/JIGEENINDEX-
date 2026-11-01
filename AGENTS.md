# Instructions communes — Codex, Claude Code et agents

## Mission
Construire JIGEENINDEX comme une véritable plateforme institutionnelle et statistique portée par JEADER. Ce n'est ni une maquette, ni un simple CRUD, ni un prototype rempli de chiffres inventés.

## Avant chaque intervention
1. Lire README.md, CLAUDE.md et tous les documents de docs/.
2. Inspecter le dépôt, la branche, l'historique Git, les dépendances et les fichiers existants.
3. Vérifier git status avant toute modification ; ne jamais écraser un travail existant.
4. Présenter un plan concret et les critères d'acceptation du lot.
5. Travailler par modules et tranches verticales complètes.

## Interdictions absolues
- Ne jamais inventer de statistiques, de sources, de résultats de tests, de secrets ou de paramètres de production.
- Ne jamais affirmer qu'une API est connectée, qu'un test passe ou qu'un déploiement est fait sans preuve.
- Ne jamais exposer SUPABASE_SERVICE_ROLE_KEY ou un secret dans le navigateur, Git ou les logs.
- Ne jamais considérer un contrôle d'interface comme un contrôle d'autorisation suffisant.
- Ne jamais publier une observation sans validation.
- Ne jamais écraser silencieusement une donnée publiée lors d'une synchronisation.
- Ne jamais publier des données individuelles ou ré-identifiantes.
- Ne jamais rendre les signalements accessibles aux rôles ordinaires.
- Ne jamais inventer des pondérations ou indices composites sans méthode approuvée.
- Ne pas masquer les erreurs par des any, ts-ignore ou catch silencieux.

## Stack et architecture
Next.js App Router, TypeScript strict, Tailwind CSS, Supabase PostgreSQL/Auth/Storage, RLS, Vercel, Zod, Vitest et Playwright. Server Components par défaut ; composants client uniquement si nécessaires. Les services métier, autorisations et connecteurs doivent être indépendants de l'interface. Ne pas ajouter un backend séparé sans justification.

Structure cible à adapter au projet réel :
- src/app : routes publiques et administration
- src/components : composants réutilisables
- src/features : domaines fonctionnels
- src/lib : clients, validation et utilitaires
- src/server : services métier, autorisations, connecteurs
- src/types : types partagés
- supabase/migrations : migrations SQL versionnées
- supabase/seed : références vérifiées et non sensibles
- tests : tests unitaires, intégration et E2E
- docs : architecture, API, données, sécurité et exploitation

## Domaines fonctionnels
Portail institutionnel/CMS ; piliers et indicateurs ; observations et dimensions ; sources et datasets ; connecteurs API/SDMX ; import CSV/XLSX ; workflow de revue, validation et publication ; dashboards ; carte des 14 régions ; publications, actualités, partenaires et médias ; comptes, rôles, permissions et audit ; contributions ; signalements confidentiels ; exports et notifications.

## Traçabilité statistique obligatoire
Chaque observation conserve l'indicateur et sa définition, valeur originale, valeur normalisée si transformation, unité, période, territoire, population/dénominateur, dimensions disponibles, source, dataset, date d'import, méthode/version, statut de validation et historique de publication. Les valeurs manquantes ne deviennent jamais zéro par défaut. Ne pas agréger des observations incompatibles.

## Rôles indicatifs
Super administrateur, administrateur général, responsable scientifique, gestionnaire de données, validateur scientifique, éditeur, gestionnaire partenaires, responsable signalements, analyste et contributeur. Définir des permissions granulaires telles que content.publish, datasets.import, observations.validate, observations.publish, users.manage et reports.read_restricted. Contrôler les droits côté serveur et par RLS.

## Sécurité et protection des personnes
RLS restrictive par défaut ; validation serveur ; contrôle de propriété ; rate limiting ; validation MIME/taille des fichiers ; journalisation sans contenu confidentiel inutile ; secrets serveur ; minimisation des données personnelles ; politique de conservation ; sauvegardes et restauration testée. Les obligations sénégalaises doivent être validées par JEADER et les personnes compétentes. La CDP est une autorité de protection des données, pas une source statistique. Ne pas présenter un signalement comme un service d'urgence ou de prise en charge sans mandat réel.

## UX et direction artistique
Interface naturelle, sobre, crédible, authentique et institutionnelle. Français au lancement, architecture prête pour wolof et anglais. Responsive, accessible, contrastes vérifiés, navigation clavier, états chargement/vide/erreur. Graphiques accompagnés de leurs unités, périodes, sources et notes. Aucun chiffre décoratif, template générique surchargé, animation gadget ou logo inventé. Utiliser la charte approuvée par JEADER.

## Méthode de livraison
Pour chaque lot : inspecter, planifier, implémenter, ajouter migrations et tests, exécuter lint/typecheck/tests/build, corriger, documenter et fournir un bilan factuel. Lister les fichiers changés, commandes et résultats exacts, tests non exécutés, variables nécessaires, limites et risques.

## Git et collaboration
Une branche dédiée par lot et une Pull Request vers main. Ne pas travailler simultanément sur les mêmes fichiers avec un autre agent. Avant de reprendre, inspecter les commits et changements récents. Ne pas pousser directement sur main sans demande explicite. Ne jamais fusionner une PR dont les tests requis échouent.

## Critères d'acceptation globaux
Installation reproductible ; migrations applicables sur base vierge ; RLS testée positivement et négativement ; parcours d'administration testés par rôle ; données publiques traçables ; import avec aperçu et erreurs ; aucun secret dans Git ; aucun faux contenu officiel ; tests et build consignés ; guides de déploiement, sauvegarde et restauration disponibles.
