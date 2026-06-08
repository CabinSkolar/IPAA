# IPAA — Indice Progressif Auto-Ajustable

**Pour une gouvernance algorithmique et souveraine du système de retraite français**

> *Cabin Skolar — Independent AI Research — Octobre 2025*
> 
> contact@cabinskolar.fr · cabinskolar.fr · CC BY 4.0

---

## Ce que c'est

L'IPAA est une proposition technique de réforme du financement des retraites françaises. Elle repose sur un mécanisme d'ajustement automatique, progressif et transparent — l'**Algorithme de Convergences AC-IPAA** — qui dépolitise la question du déficit structurel sans recul de l'âge et sans choc tarifaire.

Ce repo contient **tous les outils publics** du projet : working paper, modèle actuariel, simulateur interactif, landing page, note de synthèse. Tout est open source, reproductible, et conçu pour être contesté, amélioré ou rétro-ingénié.

---

## Contenu du repo

```
IPAA/
├── README.md                          # Ce fichier
├── docs/
│   ├── IPAA_Working_Paper_V2.pdf      # Working paper complet (27 700 mots)
│   ├── IPAA_Note_Synthese.pdf         # Note de synthèse 4 pages (pitch élu)
│   └── IPAA_Methodologie.pdf         # Guide méthodologique complet
├── modele/
│   └── IPAA_Modele_Actuariel.xlsx    # Modèle Excel — 1332 formules, 0 erreur
├── web/
│   ├── ipaa_landing_v2.html          # Landing page (charte Cabin Skolar)
│   └── ipaa_simulateur.html          # Simulateur dynamique 30 ans
└── equations/
    └── IPAA_Equations.md             # Formalisation complète des équations
```

---

## Le mécanisme en 4 niveaux

```
EReq(t) = [Σ Δ(k)/(1+r)^(k-t)] / 5 + S_cible   ← Effort requis N+5

Niveau 0 : Péréquation inter-caisses (CCP)
           Transfert = min(excédent_j - besoin_j(N+3), déficit_i)

Niveau 1 : Lissage FRR
           Si EReq ≤ CFРР → ∆τ = 0

Niveau 2 : Ajustement progressif
           ∆τ = (EReq - CFРР) / A_élargie
           ∆τᵢ = ∆τ × βᵢ   (βi=0 pour D1-D4 — Bouclier Social)

Niveau 3 : Clause de sauvegarde parlementaire
           Si ∆τ_brut > plafond → alerte Parlement
```

---

## Utiliser le modèle Excel

Le fichier `IPAA_Modele_Actuariel.xlsx` contient 3 feuilles :

**`Hypothèses`** — toutes les constantes en bleu sont modifiables :
- Paramètres macroéconomiques (croissance, chômage, inflation)
- Démographie (ratio actifs/retraités COR 2025)
- FRR (rendement central 5%, CFРР 10%)
- Coefficients βi par décile
- Nouvelles assiettes de financement

**`Modèle_30ans`** — projection complète 2025-2055 :
- PIB, masse salariale, dépenses, recettes
- Les 4 niveaux AC-IPAA calculés séquentiellement
- Trajectoire FRR (compartiments socle/croissance)
- 5 scénarios de risque (R1 à R5)
- 3 indicateurs de convergence (feux tricolores)

**`Impact_Déciles`** — impact ∆τ en euros par mois par décile, pour n'importe quelle année de projection.

---

## Utiliser le simulateur web

Ouvrir `web/ipaa_simulateur.html` dans un navigateur. 8 curseurs ajustables en temps réel :
- Croissance de productivité, chômage, fécondité
- Rendement FRR, CFРР, plafond ∆τ, βi moyen, nouvelles assiettes

4 graphiques recalculés instantanément :
- Solde du système avec/sans IPAA sur 30 ans
- Trajectoire FRR
- Impact par décile en euros
- Ratio actifs/retraités

---

## Rétro-ingénierie avec Claude

Ce projet est conçu pour être exploré avec Claude ou tout autre LLM. Quelques prompts de départ :

```
"Charge le fichier IPAA_Modele_Actuariel.xlsx et modifie le rendement FRR
à 3% au lieu de 5%. Montre-moi comment la trajectoire change."

"En partant des équations dans IPAA_Equations.md, construis un modèle
équivalent pour le système de retraite belge avec les données Eurostat."

"Identifie les hypothèses les plus sensibles dans le modèle et propose
des stress tests supplémentaires."

"Le Conseil Constitutionnel pourrait-il invalider les βi différenciés
par décile ? Analyse la jurisprudence et propose une formulation alternative."
```

---

## Données sources

| Source | Utilisation | Accès |
|--------|-------------|-------|
| COR Rapport annuel juin 2025 | Projections déficit, solde % PIB | cor-retraites.fr |
| INSEE Projections 2021-2070 | Démographie, ratio actifs/retraités | insee.fr |
| DREES 2024 | Dépenses/recettes protection sociale | drees.solidarites-sante.gouv.fr |
| FRR Rapport annuel 2023 | Actifs initiaux 26,2 Md€ | fondsdereserve.fr |
| Investissements RPC 2025 | Référence internationale | investissementsrpc.com |

---

## Limites assumées

Ce modèle est **simplifié** — il ne remplace pas une modélisation actuarielle complète caisse par caisse. Il démontre la trajectoire de convergence, pas sa précision à 0,1% du PIB près.

Ce qui manque encore :
- Modélisation caisse par caisse (CNAV, AGIRC-ARRCO, MSA, CNRACL...)
- Validation actuarielle indépendante
- Code Python/R open source (le tableur Excel est l'implémentation actuelle)

**Contributions bienvenues** — ouvrir une issue ou une PR.

---

## Licence

CC BY 4.0 — vous pouvez utiliser, modifier et redistribuer ce travail, y compris à des fins commerciales, à condition de citer la source.

*Cabin Skolar · contact@cabinskolar.fr · cabinskolar.fr*
