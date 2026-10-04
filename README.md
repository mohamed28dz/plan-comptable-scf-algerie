# Plan Comptable SCF (Système Comptable Financier)

Ce dépôt contient le Plan Comptable SCF (Système Comptable Financier), mis à disposition dans des formats de données structurés et lisibles par machine. Il est conçu pour être facilement intégré dans des applications logicielles, des scripts d'analyse financière ou des bases de données.

## 📂 Contenu du dépôt

*   **`plan_comptable_scf.json`** : Le plan comptable complet au format JSON. Idéal pour les applications web et les API.
*   **`plan_comptable_scf.yaml`** : Le plan comptable complet au format YAML. Idéal pour les fichiers de configuration et une lecture humaine facilitée.
*   **`LICENSE`** : Les termes de la licence sous laquelle ce projet est distribué.
*   **`README.md`** : Ce fichier de documentation.

## 🏗️ Structure des données

*(Note : Adaptez cette section selon la structure réelle de vos fichiers)*

Les fichiers contiennent une liste d'objets représentant les comptes. Voici un exemple de la structure attendue :

### Exemple JSON
```json
[
  {
    "code": "101",
    "libelle": "Capital social",
    "classe": "1",
    "type": "Passif"
  },
  {
    "code": "512",
    "libelle": "Banque",
    "classe": "5",
    "type": "Actif"
  }
]
```

Exemple YAML

```yaml
- code: "101"
  libelle: "Capital social"
  classe: "1"
  type: "Passif"
- code: "512"
  libelle: "Banque"
  classe: "5"
  type: "Actif"
```

🚀 Utilisation

Ces fichiers peuvent être utilisés pour :

· Alimenter des logiciels de comptabilité ou de gestion financière.
· Créer des validateurs de saisie comptable.
· Effectuer des analyses de données et des rapports automatisés.
· Servir de référence pour des projets de développement (Python, JavaScript, Java, etc.).

Exemple rapide en Python (JSON) :

```python
import json

with open('plan_comptable_scf.json', 'r', encoding='utf-8') as f:
    plan_comptable = json.load(f)

for compte in plan_comptable:
    print(f"{compte['code']} - {compte['libelle']}")
```

🤝 Contribution

Les contributions sont les bienvenues ! Si vous souhaitez corriger une erreur, ajouter des comptes manquants ou améliorer la structure des fichiers :

1. Forkez le projet.
2. Créez une branche pour votre modification (git checkout -b amelioration/plan-comptable).
3. Committez vos changements (git commit -m 'Ajout de nouveaux comptes').
4. Pushez la branche (git push origin amelioration/plan-comptable).
5. Ouvrez une Pull Request.

📄 Licence

Ce projet est sous licence [Insérez le type de licence ici, ex: MIT]. Veuillez consulter le fichier LICENSE pour plus de détails.


