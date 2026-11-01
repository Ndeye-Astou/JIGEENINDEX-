# Prompt d'exécution — réalisation complète de JIGEENINDEX

À utiliser dans Claude Code ou Codex après lecture de AGENTS.md, CLAUDE.md, README.md et des documents de docs/.

Tu es un ingénieur logiciel senior / architecte full-stack responsable de livrer une plateforme institutionnelle complète. Tu ne dois pas produire une simple maquette ni t'arrêter à une page d'accueil.

## Objectif
Réaliser JIGEENINDEX, observatoire numérique national des conditions des femmes et des filles au Sénégal, porté par JEADER. Le résultat doit être crédible pour des institutions nationales, des ministères, des organismes internationaux, des chercheurs et des partenaires. L'interface doit être simple, naturelle, authentique, sobre, distinctive et professionnelle. Le code doit être maintenable par une développeuse seule.

## Première tâche obligatoire
- Vérifie le contenu réel du dépôt et l'historique Git.
- Fais un audit de l'état du projet.
- Établis le plan d'exécution et les dépendances bloquantes.
- Ne supprime aucun fichier sans justification.
- Commence par le socle, le modèle de données, les migrations et la sécurité ; ne commence pas par une landing page isolée.

## Exigences de réalisation
Implémente réellement, avec code, base de données, validations, autorisations et tests :

1. Application Next.js App Router avec TypeScript strict et Tailwind.
2. Configuration qualité : lint, formatage, typecheck, tests, build et CI.
3. Supabase PostgreSQL, Auth, Storage, migrations SQL versionnées et RLS.
4. Profils, rôles, permissions granulaires et journal d'audit.
5. CMS institutionnel : pages, sections, menus, médias, SEO, aperçu, programmation, publication, dépublication, versions, archivage et restauration.
6. Référentiel géographique Sénégal : 14 régions, puis départements/communes seulement avec nomenclature fiable.
7. Neuf piliers thématiques et catalogue d'indicateurs administrable.
8. Sources, jeux de données, métadonnées, documents et provenance.
9. Import CSV/XLSX : upload sécurisé, mapping, aperçu, validations, doublons, erreurs, rollback et journal.
10. Workflow de soumission, contrôle, revue, validation scientifique et publication versionnée.
11. Connecteurs API/SDMX côté serveur, seulement après vérification des documentations, licences, accès et formats. Commencer par une intégration documentée et testée ; ne pas simuler une API.
12. Moteur statistique avec formules reproductibles et documentées.
13. Dashboard national, filtres, comparaisons et exports autorisés.
14. Carte des régions basée sur une géométrie dont la source et la licence sont documentées.
15. Publications, actualités, événements, partenaires et médiathèque.
16. Contributions d'organisations avec suivi.
17. Signalements confidentiels uniquement après définition et validation du mandat, du protocole, du cadre légal et des personnes habilitées.
18. Notifications, logs, tâches planifiées, supervision, sauvegardes et restauration.
19. Documentation technique, dictionnaire de données, guides admin/utilisateur et procédure de déploiement.

## Qualité des données
Ne crée jamais de statistiques fictives pour remplir les graphiques. Si la base ne contient pas encore de données validées, l'interface doit afficher un état vide utile, expliquer les données attendues et montrer les métadonnées disponibles. Toute observation publique doit indiquer source, période, unité, territoire, population/dénominateur, méthode, date de mise à jour et statut de validation. Les valeurs manquantes ne sont pas des zéros. Aucune pondération ou indice composite sans validation scientifique explicite.

## Sécurité
- RLS restrictive par défaut pour toutes les tables exposées.
- Vérification serveur des rôles et permissions.
- Aucun secret dans le navigateur ou dans Git.
- SUPABASE_SERVICE_ROLE_KEY exclusivement côté serveur si son usage est indispensable.
- Validation Zod des entrées, limites de taille et types MIME des fichiers, rate limiting.
- Protection contre accès non autorisé, injection, XSS et CSRF.
- Signalements isolés, accès strictement restreints, audit des accès et politique de conservation.
- Tester les accès autorisés ET interdits.

## Direction produit et design
Créer une expérience institutionnelle et humaine, pas un template SaaS générique. Prioriser la lisibilité, la confiance, la hiérarchie éditoriale, les espaces, la qualité des tableaux et graphiques, la navigation claire et le mobile. Pas de chiffres décoratifs, pas de fausses statistiques, pas d'animations inutiles, pas de gradients tape-à-l'œil. Utiliser les éléments de marque officiels seulement lorsqu'ils sont fournis ou approuvés. Français au lancement, architecture prête pour wolof et anglais.

## Méthode de travail
Travaille par lots courts et verticaux. Pour chaque lot :
1. Annonce les fichiers et domaines concernés.
2. Implémente l'ensemble du parcours, pas seulement l'interface.
3. Ajoute ou mets à jour les migrations.
4. Ajoute tests unitaires, intégration, RLS et E2E adaptés.
5. Exécute lint, typecheck, tests et build.
6. Corrige les régressions.
7. Mets à jour les documents.
8. Donne un bilan factuel des fonctionnalités prouvées, commandes et résultats exacts, limites et dépendances externes.

## Gestion du dépôt
- Une branche par fonctionnalité ou phase.
- Ne pas travailler simultanément sur les mêmes fichiers avec un autre agent.
- Ouvrir une Pull Request vers main.
- Ne pas fusionner si les tests requis échouent.
- Ne jamais pousser directement sur main sans demande explicite.
- Avant de reprendre le travail d'un autre agent, lire ses commits et son diff.
- Ne pas committer .env, clés, exports privés ou données personnelles.

## Critère de fin
La plateforme ne peut être déclarée terminée que lorsque les parcours publics et administratifs sont opérationnels, les migrations applicables, les permissions/RLS testées, les imports et validations fonctionnels, les données traçables, les tests et builds passants, la sécurité auditée, la sauvegarde restaurée en test, la documentation livrée et la recette JEADER obtenue. Les fonctionnalités dépendant d'accès ou de décisions de JEADER doivent être signalées comme bloquées, jamais simulées.

Commence maintenant par l'audit du dépôt puis exécute le premier lot complet. Ne t'arrête pas après avoir proposé un plan : après l'audit, implémente et vérifie le premier lot, puis poursuis les lots suivants jusqu'à ce que les critères de fin soient atteints ou qu'une dépendance externe réelle bloque la suite.
