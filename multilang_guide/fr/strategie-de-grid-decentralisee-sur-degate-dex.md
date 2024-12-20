---
description: Stratégie de Grid Décentralisée sur DEX
---

# Stratégie de Grid Décentralisée sur DeGate DEX

**Qu'est-ce que la stratégie de Grid ?**

La Stratégie de Grid Trading est une méthode qui automatise les ordres d'achat et de vente dans une plage de prix prédéfinie. Elle place une série d'ordres limités, où chaque exécution déclenche automatiquement un ordre opposé à un niveau supérieur ou inférieur. Cette stratégie est idéale pour les marchés latéraux avec des fluctuations régulières, permettant de capter des profits sur des variations de prix limitées..

Sur [DeGate DEX](https://app.degate.com/?utm_source=gridguidebook), la stratégie de [Grid Trading](https://app.degate.com/en/grid/USDC/ETH/?utm_source=gridguidebook) est sans frais, de manière décentralisée et en gardant le contrôle total sur vos clés de cryptomonnaie, c'est-à-dire en mode self-custody.

{% embed url="https://www.youtube.com/watch?v=uvkBgcWa6zc&t=3s" %}

### **Avantages de la stratégie de Grid**

La stratégie de Grid est prisée par les traders qui n'ont ni le temps ni l'énergie pour surveiller les écrans en permanence. Parmi ses avantages notables :

**Automatisation** - Les limites de prix supérieures et inférieures sont d'abord définies, après quoi les ordres d'achat/vente en grille sont placés et exécutés automatiquement en fonction des mouvements de prix de l'actif sous-jacent. La stratégie de Grid fonctionne 24/7 (achats à bas prix, ventes à prix élevé), générant ainsi des profits passifs pour les traders.

**Adaptabilité** - La densité de la grille peut être optimisée en fonction des circonstances. À court terme, des centaines de grilles peuvent être configurées pour capturer des micro-profits sur les variations de prix quotidiennes ; à long terme, le choix d'une plage plus large permet de profiter de la tendance latérale globale.

**Rentabilité** - Le trading en grille est particulièrement performant sur des marchés latéraux où aucune tendance claire ne se dégage. Le trader n'a pas besoin de prédire si le prix de l'actif va monter ou descendre, et aucune intervention n'est nécessaire une fois la stratégie de grille mise en place, en dehors de la surveillance des résultats.



### **Défis de conception de la Stratégie de Grid (Décentralisée)**

La fonctionnalité de stratégie de Grid se trouve couramment sur les plateformes d'échanges centralisées (CEX). L'exécution des transactions est facilitée sur les CEX car les utilisateurs n'ont pas la garde de leurs fonds. Actuellement, il n'existe pas de protocoles de trading en grille décentralisés en raison de quelques défis :

**Autorisation de signature du portefeuille**

Une configuration typique de trading en grille peut comporter de 2 à 200 niveaux de grille, en fonction des paramètres définis par l'utilisateur. Chaque niveau de grille représente un ordre limite d'achat ou de vente qui nécessite l'autorisation de signature de l'utilisateur. De plus, cette autorisation de signature prend généralement quelques secondes, ce qui peut affecter l'exécution des ordres en grille sur des marchés où les mouvements se produisent en microsecondes.

**Signature en direct à la demande**

Dans un scénario de marché en temps réel, les prix peuvent fluctuer rapidement en peu de temps. Cela affecte les ordres en grille, qui peuvent passer d'un ordre d'achat à un ordre de vente ou vice versa. Ces ordres inversés nécessitent une autorisation de signature en temps réel de la part de l'utilisateur, ce qui peut être difficile à obtenir si l'utilisateur est loin de son ordinateur.

### **Introduction à la Stratégie de Grille Décentralisée**

Afin d'atteindre l'objectif de construction d'une fonctionnalité de stratégie de grille décentralisée, nous devons d'abord identifier et définir les constantes dans une configuration standard de stratégie de grille.

#### **Constantes**

* **Montant par Niveau** - Actifs alloués pour chaque niveau de grille, tels que déterminés par les informations saisies par l'utilisateur.
* **Décalage de Grille** - Différence entre chaque niveau de grille, déterminée par la fourchette de prix et le nombre de niveaux de grille.
* **Décalage d'Ordre** - La différence entre chaque ordre, créée pour le calcul des ordres inverses. Équivalent au décalage de grille.

#### **Grilles d'Achat/Vente**&#x20;

Essentiellement, la configuration standard de la stratégie de grille est un robot de trading bidirectionnel. Pour simplifier les complications liées à la signature de l'utilisateur, la configuration de la stratégie de grille est décomposée en deux catégories de grilles, à savoir :

* **Grille d'Achat** - Configuration des ordres d'achat de grille.
* **Grille de Vente** - Configuration des ordres de vente de grille.

#### **Signatures de Grille**&#x20;

L'étape suivante consiste à configurer les signatures de transaction pour chaque grille d'achat/vente. Les constantes définies précédemment sont regroupées dans chaque signature de transaction de grille. De manière critique, la signature de transaction sera liée au premier ordre de grille, qui est défini comme étant la grille la plus proche du prix de marché actuel, et les ordres de grille suivants seront configurés en conséquence avec l'autorisation de signature du premier ordre de grille.

{% hint style="info" %}
Par exemple, si le prix de marché actuel de l'ETH est à 2000 $ :

* Pour la Grille d'Achat - le premier ordre de grille ("Achat 1") est défini au niveau de grille le plus proche en dessous de 2000 $.
* Pour la Grille de Vente - le premier ordre de grille ("Vente 1") est défini au niveau de grille le plus proche au-dessus de 2000 $.
{% endhint %}

Cela résout en gros la nécessité pour l'utilisateur de signer plusieurs transactions pendant que la stratégie de grille est en cours d'exécution.

**Exemple : ETH/USDC**&#x20;

L'utilisateur A configure une stratégie de grille manuelle pour ETH/USDC dans la fourchette de 1800 $ à 2300 $, tandis que le prix actuel de l'ETH est de 2050 $. 10 lignes de grille sont ajoutées avec des actifs alloués de 0,5 ETH et 950 USDC.

En conséquence, 5 grilles de vente et 5 grilles d'achat sont configurées en fonction des paramètres saisis.

Pour la Grille de Vente, l'utilisateur devra approuver et signer la "Signature de Txn Grille de Vente" au premier niveau de grille de vente (alias "Vente 1"), permettant au mécanisme de stratégie de grille de configurer les ordres de grille de vente suivants.

Pour la Grille d'Achat, l'utilisateur devra approuver et signer la "Signature de Txn Grille d'Achat" au premier niveau de grille d'achat (alias "Achat 1"), permettant au mécanisme de stratégie de grille de configurer les ordres de grille d'achat suivants.

L'utilisateur peut simplement s'asseoir, se détendre et regarder la stratégie de grille exécuter les différents ordres de grille (essentiellement acheter bas et vendre haut), générant des profits passifs pour l'utilisateur !

{% hint style="info" %}
_Grâce à ce design technique innovant, les utilisateurs peuvent désormais profiter des avantages du trading de grille tout en conservant la pleine garde de leurs actifs._
{% endhint %}

<figure><img src="../.gitbook/assets/grid gif1 (1).gif" alt=""><figcaption></figcaption></figure>



### **Stratégies pour le Grid Trading**

Il existe 3 stratégies courantes utilisées dans le Grid Trading qui dépendent largement des tendances du marché et de la performance de l'actif sous-jacent.

#### **Stratégie de Grille Normale**

Celle-ci est mieux déployée dans un marché turbulent où l'actif sous-jacent se consolide ou évolue dans une fourchette de prix. Grâce à une stratégie de grille normale, le trader peut placer à la fois des ordres d'achat et de vente dans une fourchette de prix prédéfinie, réalisant ainsi des profits passifs à partir des fluctuations de prix de l'actif.

<figure><img src="../.gitbook/assets/Normal-Grid-EN-v2m (1) (1).gif" alt=""><figcaption></figcaption></figure>

#### **Stratégie de Grille d'Achat**

Cette stratégie est mieux déployée dans un marché en tendance baissière où le prix du token sous-jacent pourrait encore chuter. Grâce à une stratégie de grille d'achat, le trader peut placer une série d'ordres d'achat en dessous du prix du marché, lui permettant d'acquérir l'actif à bas prix. De plus, les ordres de grille seront inversés en ordres de vente si le prix rebondit, ce qui permet au trader de réaliser des profits dans la fourchette de la grille.

Le principe fondamental de la stratégie de grille d'achat est le suivant : le token sous-jacent a un bon potentiel et est adapté à une détention à long terme, ce qui permet au trader de profiter de l'achat progressif du token, même si son prix tombe en dehors de la fourchette de la grille.

<figure><img src="../.gitbook/assets/Buy-Grid-v20m (1).gif" alt=""><figcaption></figcaption></figure>

**Stratégie de Grille de Vente**

Ceci est similaire à la stratégie de grille d'achat, mais dans une direction opposée. La stratégie de grille de vente est mieux déployée dans un marché en tendance haussière où le prix du token sous-jacent continuera probablement à augmenter. Grâce à une stratégie de grille de vente, le trader peut placer une série d'ordres de vente au-dessus du prix du marché, lui permettant de vendre l'actif à un prix élevé. De plus, les ordres de grille seront inversés en ordres d'achat si le prix baisse, permettant au trader de réaliser des profits dans la fourchette de la grille.

Le principal avantage de la stratégie de grille de vente est le suivant : le trader peut prendre des profits de manière incrémentale à mesure que le prix du token sous-jacent augmente, maximisant ainsi les gains tout au long de la montée, tout en rachetant lorsque le prix du token redescend.

<figure><img src="../.gitbook/assets/Sell-Grid-v3m (1).gif" alt=""><figcaption></figcaption></figure>

**Conclusion**

La stratégie de trading en Grille est une stratégie de trading automatisée qui n'est pas affectée par les émotions humaines et qui est entièrement déterminée par un code. Cette stratégie est particulièrement efficace dans un marché latéral, générant des revenus passifs pour les utilisateurs sans avoir besoin de surveiller constamment l'écran.

De plus, en s'appuyant sur la conception décentralisée de DeGate pour sa fonctionnalité de trading par grille, les utilisateurs auront désormais la pleine maîtrise de leurs fonds tout en profitant des avantages du trading automatisé. Avec la gamme de fonctionnalités de DeGate, telles que les ordres à cours limité et le trading par grille décentralisé, les utilisateurs peuvent enfin dormir sur leurs deux oreilles, quelle que soit la condition du marché.



### **Guide Stratégique de Trading en Grille**

Le trading en grille est un outil puissant qui automatise l'achat et la vente dans une plage de prix définie. Une stratégie en grille place automatiquement des ordres d'achat lorsque les prix baissent et des ordres de vente lorsqu'ils augmentent, vous permettant ainsi de capitaliser sur les fluctuations du marché et de générer des profits.

#### **Comment configurer une stratégie de trading en grille sur DeGate ?** <a href="#id-35mavrbg2mg3" id="id-35mavrbg2mg3"></a>

Prenons l'exemple ci-dessous, en utilisant la paire ETH/USDC.

<figure><img src="../.gitbook/assets/image (23).png" alt=""><figcaption></figcaption></figure>

#### **Sélectionnez le mode de stratégie en grille**

Il existe deux modes de stratégie en grille parmi lesquels choisir.

* **Auto** : Configurez la stratégie de trading en grille en utilisant les paramètres auto-générés recommandés par le système.
* **Manuel** : Personnalisez les paramètres de la stratégie de trading en grille pour correspondre à vos préférences.

{% hint style="info" %}
Pour les nouveaux utilisateurs de la stratégie en grille, il est recommandé de commencer par le mode \[Auto].
{% endhint %}

<figure><img src="../.gitbook/assets/image (24).png" alt=""><figcaption></figcaption></figure>

<figure><img src="../.gitbook/assets/image (25).png" alt=""><figcaption></figcaption></figure>

#### **Configurer la stratégie en grille \[AUTO]** <a href="#id-8lri8p8dgxyf" id="id-8lri8p8dgxyf"></a>

1. Cliquez sur l'onglet \[Auto].
2. Entrez le montant à allouer pour la stratégie de trading en grille \[ETH/USDC]. Saisissez soit le montant en ETH, soit en USDC, et le système calculera le montant correspondant pour la stratégie de trading en grille.

{% hint style="info" %}
_Assurez-vous d'avoir suffisamment d'ETH et d'USDC dans votre solde DeGate._
{% endhint %}

<figure><img src="../.gitbook/assets/image (26).png" alt=""><figcaption></figcaption></figure>

3. Les paramètres recommandés seront affichés.
4. Cliquez sur "Créer une stratégie en grille" pour finaliser la configuration et commencer à gagner.

<figure><img src="../.gitbook/assets/image (27).png" alt=""><figcaption></figcaption></figure>

<figure><img src="../.gitbook/assets/image (28).png" alt=""><figcaption></figcaption></figure>

#### **Configurer la stratégie en grille \[MANUEL]** <a href="#lwre7rj2zysg" id="lwre7rj2zysg"></a>

1. Cliquez sur l'onglet \[Manuel]. Vous pouvez modifier les paramètres pour personnaliser votre stratégie de trading en grille.
2. Plage de prix : Les limites supérieures et inférieures définissent la plage de prix dans laquelle la stratégie en grille sera exécutée.
3. Allocation initiale : Le montant des fonds à allouer pour la stratégie de trading en grille. Saisissez soit le montant en ETH, soit en USDC, et le système calculera le montant correspondant.
4. Nombre de grilles : Le nombre d'ordres d'achat et de vente que la stratégie en grille placera dans la plage de prix.
5. Quantité par grille (≥ 50 $) : Le montant d'ETH alloué pour chaque ordre de grille.
6. Cliquez sur "Créer une stratégie en grille" pour finaliser la configuration et commencer à gagner.

{% hint style="info" %}
_Il existe une exigence de taille de commande minimale de 50 $ pour chaque ordre de grille._
{% endhint %}

<figure><img src="../.gitbook/assets/image (29).png" alt=""><figcaption></figcaption></figure>

Pour une rentabilité optimale, il est recommandé de configurer la stratégie en grille de manière à ce que le prix actuel du marché se situe dans la plage de prix définie.
