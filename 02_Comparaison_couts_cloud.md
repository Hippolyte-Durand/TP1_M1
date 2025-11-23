# Exercice : Calcul des coûts d'une Infrastructure Cloud (IaaS)

---

## 1. Hypothèses et Règles de Calcul

Conformément aux consignes de l'exercice :
* **Périodicité :** Mensuelle (base moyenne de 730 heures).
* **Devise :** USD ($) Hors Taxes.
* **Taux de change appliqué :** $1.00 \text{ €} \approx 1.05 \$.
* **Région :** France (Paris) ou Europe.
* **Méthodologie :** Comparatif basé sur des instances **Cloud Public (IaaS)** pour assurer une équivalence technique stricte (stockage, réseau, disponibilité). Pas d'offre VPS.

---

## 2. Infrastructure n°1

**Besoin exprimé :**
* 1 Serveur (16 Go RAM min, 4 vCPU, 100 Go Stockage).
* Usage : 24/7 (730 heures).

### Analyse des coûts

* **OVHcloud :**
    * **Offre :** Instance Public Cloud `b3-16` (4 vCPU, 16 Go RAM).
    * **Tarif :** 0,093 €/heure.
    * **Stockage :** 100 Go NVMe (Inclus dans l'instance).
    * **Calcul :** $0,093 \text{ €} \times 730 \text{ h} \times 1,05 \approx \mathbf{71,28 \$}$.

* **Scaleway :**
    * **Offre :** Instance `COPARM1-4C-16G` (Architecture ARM).
    * **Tarif :** 0,0857 €/heure.
    * **Stockage :** Non inclus. Ajout de 100 Go de Block Storage.
    * **Calcul :** $(0,0857 \text{ €} \times 730 \text{ h} \times 1,05) + (100 \text{ Go} \times 0,11 \$) \approx 65,69 \$ + 11,00 \$ = \mathbf{76,69 \$}$.

* **Azure :**
    * **Offre :** Instance **B4as v2** (4 vCPU, 16 Go RAM).
    * **Compute :** 0,169 $/h.
    * **Stockage :** Disque SSD Standard E10 (128 Go) à **10,50 $**.
    * **Calcul :** $(0,169 \$ \times 730 \text{ h}) + 10,50 \$ = 123,37 \$ + 10,50 \$ = \mathbf{133,87 \$}$.

---

## 3. Infrastructure n°2

**Besoin exprimé :**
* 6 Serveurs (6 Go RAM, 3 vCPU, 20 Go Stockage).
* **Particularité :** 3 serveurs éteints la nuit de 22h à 06h.

### Détail du calcul du volume horaire

Pour optimiser les coûts, nous calculons le nombre exact d'heures facturées pour le compute :

1.  **Serveurs 24/7 (3 serveurs) :**
    * $3 \text{ serveurs} \times 730 \text{ heures} = 2\,190 \text{ heures}$.
2.  **Serveurs Nuit OFF (3 serveurs) :**
    * Ces serveurs fonctionnent 16h par jour (arrêtés 8h la nuit).
    * $3 \text{ serveurs} \times 16 \text{ heures/jour} \times 30,5 \text{ jours/mois} \approx 1\,470 \text{ heures}$.
3.  **Volume Total Compute :**
    * $2\,190 + 1\,470 = \mathbf{3\,660 \text{ heures}}$.
4.  **Volume Total Stockage :**
    * Le stockage est facturé 24/7 pour les 6 serveurs.
    * $6 \text{ serveurs} \times 20 \text{ Go} = 120 \text{ Go}$.

### Analyse des coûts

* **OVHcloud :**
    * **Offre :** Instance Discovery `d2-8` (4 vCPU, 8 Go RAM).
    * **Tarif :** ~0,036 €/heure.
    * **Stockage :** Inclus (0 $).
    * **Calcul :** $3\,660 \text{ h} \times 0,036 \text{ €} \times 1,05 \approx \mathbf{138,35 \$}$.

* **Scaleway :**
    * **Offre :** Instance Development `PLAY2-MICRO` (4 vCPU, 8 Go RAM).
    * **Tarif :** ~0,054 €/heure.
    * **Stockage :** Block Storage (Non inclus).
    * **Calcul Compute :** $3\,660 \text{ h} \times 0,054 \text{ €} \times 1,05 \approx 207,52 \$$.
    * **Calcul Stockage :** $120 \text{ Go} \times 0,08 \$ \approx 9,60 \$$.
    * **Total :** $207,52 + 9,60 = \mathbf{217,12 \$}$.

* **Azure :**
    * **Offre :** Instance **B4als v2** (4 vCPU, 8 Go RAM).
    * **Tarif :** **0,151 $/heure**.
    * **Stockage :** Disques SSD Standard 32 Go (E4) à **2,64 $/mois**.
    * **Calcul Compute :** $3\,660 \text{ h} \times 0,151 \$ = 552,66 \$$.
    * **Calcul Stockage :** $6 \times 2,64 \$ = 15,84 \$$.
    * **Total :** $552,66 + 15,84 = \mathbf{568,50 \$}$.

---

## 4. Infrastructure n°3

**Besoin exprimé :**
* 3 Serveurs Web (4 Go RAM, 2 vCPU, 50 Go Stockage).
* 1 Load Balancer (5 Mb/s).
* 1 Base de données managée (8 Go RAM, 2 vCPU, 10 Go Stockage).

### Analyse des coûts

* **OVHcloud :**
    * **Web (x3) :** Instance `d2-4` (Stockage inclus).
        * $3 \times 730 \text{ h} \times 0,023 \text{ €} \times 1,05 \approx 52,88 \$$.
    * **Load Balancer :** Offre Public Cloud (~16 €) $\approx 16,80 \$$.
    * **Database :** Managed SQL (Discovery 8Go) $\approx 52,12 \$$.
    * **Total :** **121,80 $**.

* **Scaleway :**
    * **Web (x3) :** Instance `PLAY2-NANO` + 50 Go Block Storage par serveur.
        * Compute : $3 \times 730 \text{ h} \times 0,027 \text{ €} \times 1,05 \approx 62,10 \$$.
        * Stockage : $150 \text{ Go} \times 0,08 \$ \approx 12,00 \$$.
    * **Load Balancer :** Forfait $\approx 15,75 \$$.
    * **Database :** Managed DB (Cost optimized) $\approx 63,00 \$$.
    * **Total :** **152,85 $**.

* **Azure :**
    * **Web (x3) :** Instance **B2als v2** (0,043 $/h) + SSD Standard 64Go (5,28 $).
        * Compute : $3 \times 730 \text{ h} \times 0,043 \$ = 94,17 \$$.
        * Stockage : $3 \times 5,28 \$ = 15,84 \$$.
    * **Load Balancer :** Standard $\approx 20,00 \$$.
    * **Database :** MySQL Flexible Server $\approx 75,00 \$$.
    * **Total :** $110,01 + 20,00 + 75,00 = \mathbf{205,01 \$}$.

---

## Conclusion et Synthèse

Voici le tableau comparatif final des coûts mensuels estimés pour les trois infrastructures :

| Cloud Provider | Infra 1 | Infra 2 | Infra 3 | **TOTAL MENSUEL** |
| :--- | :--- | :--- | :--- | :--- |
| **1. OVHcloud** | **71,28 $** | **138,35 $** | **121,80 $** | **331,43 $** |
| **2. Scaleway** | 76,69 $| 217,12$ | 152,85 $ | **446,66 $** |
| **3. Azure** | 133,87 $| 568,50$ | 205,01 $ | **907,38 $** |

Dans cet exemple, **OVHcloud** est systématiquement le fournisseur le plus économique (**~331 $ / mois**), suivi par Scaleway.
L'avantage concurrentiel principal d'OVHcloud réside dans l'inclusion du disque système (NVMe/SSD) dans le prix horaire de ses instances Public Cloud, là où ses concurrents le facturent en supplément, ce qui impacte fortement les coûts lors du passage à l'échelle (Infra 2 et 3).
