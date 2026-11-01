# Claude Code — JIGEENINDEX

Tu interviens dans le dépôt GitHub Ndeye-Astou/JIGEENINDEX-.

1. Lis AGENTS.md, README.md et les documents de docs/ avant de coder.
2. Inspecte la branche, git status, git log, les fichiers, les scripts et les dépendances.
3. Ne suppose pas que le dépôt est vide ou inchangé : vérifie son état courant.
4. Propose un plan de réalisation par lots avec risques et critères d'acceptation.
5. Construis des tranches verticales réellement fonctionnelles, pas seulement des écrans.

## Ordre de réalisation
1. Socle Next.js, TypeScript strict, Tailwind, lint, tests et CI.
2. Schéma PostgreSQL, migrations et données de référence.
3. Supabase Auth, profils, RBAC, permissions et RLS.
4. CMS institutionnel complet.
5. Référentiel des piliers, indicateurs, périodes, dimensions et sources.
6. Import CSV/XLSX, contrôles, workflow de validation et versionnage.
7. Connecteurs API/SDMX uniquement après vérification des docs, licences et accès.
8. Services statistiques, dashboards, exports et carte des régions.
9. Publications, actualités, partenaires et contributions.
10. Signalements confidentiels uniquement après validation du protocole légal et opérationnel.
11. Audit sécurité, accessibilité, performance, documentation et déploiement.

## Collaboration avec Codex
AGENTS.md prévaut comme règles communes. Travaille sur une branche dédiée et ouvre une Pull Request vers main. Ne pousse pas directement sur main sans demande explicite. Ne modifie pas simultanément les mêmes fichiers qu'un autre agent. Avant chaque lot, inspecte les derniers commits et les changements existants. Dans chaque PR, liste migrations, variables nécessaires, tests réellement exécutés et limites connues.

## Qualité
TypeScript strict, validation Zod côté serveur, services métier typés, autorisations serveur et RLS, erreurs explicites, logs sans fuite, tests des règles métier et permissions. Aucun secret, donnée personnelle réelle ou chiffre fictif dans Git.

## Compte rendu obligatoire
À la fin de chaque lot, indique : ce qui fonctionne réellement, fichiers et migrations modifiés, commandes exécutées et résultats exacts, tests non exécutés, accès externes manquants, risques et prochaines étapes. Ne déclare jamais le produit terminé avant satisfaction des critères d'acceptation d'AGENTS.md.
