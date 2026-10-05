# Plan comptable SCF algérien

Plan bilingue français/arabe du Système Comptable Financier algérien, distribué en JSON et YAML. Les deux fichiers décrivent les mêmes données et utilisent les mêmes noms de variables.

- Version : `1.01`
- Date : `2026-10-05`

## Fichiers

- `plan_comptable_scf.json` : format adapté aux applications et aux API.
- `plan_comptable_scf.yaml` : format lisible et facile à modifier.
- `LICENSE` : licence du projet.

## Structure et variables

Les deux formats ont la même structure. Les codes de classe et de compte sont des entiers (`code`) ; leurs intitulés français et arabes restent dans les champs `titre`, `titre_ar`, `libelle` et `label_ar`.

| Niveau | Variable | Type | Description |
| --- | --- | --- | --- |
| Racine | `metadata` | objet | Informations sur le plan et sa version. |
| Racine | `classes` | liste | Classes comptables du plan. |
| Métadonnées | `titre` | texte | Nom du plan comptable. |
| Métadonnées | `reference_legale` | texte | Référence réglementaire indiquée par le document. |
| Métadonnées | `autorite` | texte | Autorité associée à la référence. |
| Métadonnées | `devise` | texte | Devise indiquée. |
| Métadonnées | `version` | texte | Version du fichier, au format `majeure.mineure`. |
| Métadonnées | `date` | texte | Date de version au format ISO `AAAA-MM-JJ`. |
| Métadonnées | `auteur` | objet | Informations d'auteur : `nom`, `email`, `mobile`. |
| Classe | `code` | entier | Numéro de classe. |
| Classe | `titre`, `titre_ar` | texte | Intitulés français et arabe de la classe. |
| Classe | `comptes` | liste | Comptes de la classe. |
| Compte | `code` | entier | Code du compte. |
| Compte | `libelle`, `label_ar` | texte | Intitulés français et arabe. |
| Compte | `sous_comptes` | liste | Sous-comptes, avec les mêmes champs de libellé. |
| Compte | `disponible` | booléen | Présent et `true` lorsqu'un numéro est disponible. Champ facultatif. |

### Exemple JSON

```json
{
  "metadata": {
    "titre": "Plan Comptable SCF Algérien",
    "version": "1.01",
    "date": "2026-10-05"
  },
  "classes": [
    {
      "code": 1,
      "titre": "Comptes de capitaux",
      "titre_ar": "حسابات رؤوس الأموال",
      "comptes": [
        {
          "code": 10,
          "libelle": "Capital, réserves et assimilées",
          "label_ar": "رأس المال، الاحتياطات وما يماثلها",
          "sous_comptes": [
            {
              "code": 101,
              "libelle": "Capital émis",
              "label_ar": "رأس المال الاجتماعي الصادر"
            }
          ]
        }
      ]
    }
  ]
}
```

### Exemple YAML

```yaml
metadata:
  titre: "Plan Comptable SCF Algérien"
  version: "1.01"
  date: "2026-10-05"

classes:
  - code: 1
    titre: "Comptes de capitaux"
    titre_ar: "حسابات رؤوس الأموال"
    comptes:
      - code: 10
        libelle: "Capital, réserves et assimilées"
        label_ar: "رأس المال، الاحتياطات وما يماثلها"
        sous_comptes:
          - code: 101
            libelle: "Capital émis"
            label_ar: "رأس المال الاجتماعي الصادر"
```

## Utilisation en Python

```python
import json

with open("plan_comptable_scf.json", encoding="utf-8") as fichier:
    plan = json.load(fichier)

for classe in plan["classes"]:
    for compte in classe["comptes"]:
        print(f"{compte['code']} - {compte['libelle']}")
        for sous_compte in compte["sous_comptes"]:
            print(f"  {sous_compte['code']} - {sous_compte['libelle']}")
```

## Licence

Ce projet est distribué sous licence MIT. Consultez le fichier `LICENSE` pour les conditions applicables.


