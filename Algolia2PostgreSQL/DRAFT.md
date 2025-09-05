# Article 1 – Migration Algolia → PostgreSQL pour plus de flexibilité

Cet article décrit la mise en place d’une double indexation afin de conserver Algolia pour la recherche front rapide tout en utilisant PostgreSQL pour obtenir plus de flexibilité sur les filtres, notamment OR NULL.

Les points abordés :

- Architecture de la double indexation avec le pattern CompositeGateway.
- Utilisation d’un normalizer commun pour Algolia et PostgreSQL.
- Conception d’une table PostgreSQL à partir du JSON avec JSONB GENERATED ALWAYS AS.
- Création des indexes nécessaires.
- Intégration applicative via un gateway spécifique, une entité Doctrine et un fichier de migration.

---

# Article 2 – Analyse et optimisation des requêtes PostgreSQL

Cet article présente les méthodes pour analyser et optimiser les requêtes afin de vérifier l’utilisation effective des indexes.

Les points abordés :

- Lecture et interprétation des plans d’exécution avec EXPLAIN et EXPLAIN ANALYZE.
- Consultation des tables de statistiques PostgreSQL (pg_stat_all_tables, pg_stat_user_indexes, etc.).
- Identification des indexes inutilisés et analyse des causes.
- Ajustements possibles : création, suppression ou modification d’indexes.
- Bonnes pratiques pour maintenir la performance des requêtes.

---

# Article 3 – Configurer correctement les indexes avec Doctrine

Cet article détaille les limites rencontrées lors de la génération d’indexes avec Doctrine dans PostgreSQL, en particulier pour les cas avancés.

Les points abordés :

- Déclaration d’indexes dans le mapping Doctrine (XML ou annotations).
- Écarts entre l’index configuré et l’index généré.
- Exemple concret avec des colonnes JSONB GENERATED ALWAYS AS.
- Contournement des limites : migrations SQL manuelles, gestion séparée des indexes spécifiques.
- Workflow recommandé combinant Doctrine et SQL manuel, avec validation via doctrine:schema:validate.
