---
description: Dezentrale Grid-Strategie auf DeGate DEX
---

# Leitfaden zur Grid-Strategie

### Was ist eine Grid-Strategie? <a href="#yf2232bqtdgi" id="yf2232bqtdgi"></a>

Grid-Strategie oder Grid-Trading ist ein Handelsmechanismus, der Kaufen und Verkaufen innerhalb eines definierten Bereichs automatisiert. Sie können damit eine Reihe von Kauf- und Verkaufsaufträgen innerhalb eines festgelegten Preisbereichs platzieren. Wenn ein Kaufauftrag ausgeführt wird, platziert er sofort einen weiteren Verkaufsauftrag auf einer höheren Grid-Ebene und umgekehrt. Die Grid-Strategie funktioniert am besten in Seitwärtsmärkten, wenn die Preise regelmäßig innerhalb eines definierten Bereichs schwanken, sodass Sie auch bei kleinen Preisänderungen Gewinne erzielen können.

Auf [DeGate DEX](https://app.degate.com/?utm_source=gridguidebook) können Sie eine gebührenfreie, dezentrale [Grid-Strategie](https://app.degate.com/en/grid/USDC/ETH/?utm_source=gridguidebook) in Selbstverwahrung umsetzen.

{% embed url="https://www.youtube.com/watch?v=uvkBgcWa6zc" %}

_Grid-Strategie in Praxis, niedrig kaufen und hoch verkaufen_



### **Vorteile der Grid-Strategie**

Die Grid-Strategie ist bei Händlern beliebt, die nicht den Luxus haben, ständig Zeit oder Energie am Bildschirm zu verschwenden. Zu den bemerkenswerten Vorteilen der Grid-Strategie gehören:

Automatisierung – Zuerst werden die oberen und unteren Preisgrenzen definiert, danach werden die Grid-Kauf-/Verkaufsaufträge automatisch entsprechend der Preisbewegung des zugrunde liegenden Vermögenswerts platziert und ausgeführt. Die Grid-Strategie läuft rund um die Uhr (im Wesentlichen niedrig kaufen, hoch verkaufen) und generiert passiven Gewinn für Händler.

Anpassbarkeit – Die Grid-Dichte kann für verschiedene Umstände optimiert werden. Kurzfristig können Hunderte von Grids eingerichtet werden, um Mikrogewinne aus den Preisänderungen des Tages zu erzielen; langfristig kann die Auswahl eines größeren Bereichs es dem Händler ermöglichen, von der allgemeinen Seitwärtsbewegung zu profitieren.

Rentabilität – Grid-Trading funktioniert am besten in Seitwärtsmärkten, wenn der Markt keinen klaren Trend zeigt. Ein Händler muss nicht unbedingt vorhersagen, ob der Preis des betreffenden Vermögenswerts steigen oder fallen wird, und sobald eine Grid-Strategie initiiert wurde, ist außer der Überwachung der Ergebnisse keine Eingabe erforderlich.

### Designherausforderungen der Grid-Strategie (dezentralisiert) <a href="#mb5x8xmyo83l" id="mb5x8xmyo83l"></a>

Die Grid-Strategie-Funktion ist häufig auf zentralisierten Börsen (CEX) zu finden. Die Handelsausführung wird auf CEX erleichtert, da Benutzer keine Kontrolle über ihre Gelder haben. Auf dem aktuellen Markt gibt es aufgrund einiger Herausforderungen keine dezentralen Grid-Trading-Protokolle:

**Wallet-Signatur**

Ein typisches Grid-Trading-Setup kann je nach Benutzereingabe aus 2 bis 200 Grid-Ebenen bestehen. Jede einzelne Grid-Ebene stellt entweder eine Kauf- oder Verkaufslimitorder dar, die die Wallet-Signatur des Benutzers erfordert. Darüber hinaus dauert die Signaturautorisierung normalerweise einige Sekunden, was sich auf die Ausführung der Grid-Order auswirken kann, da sich die Märkte in Mikrosekunden bewegen.

**Live-Signatur auf Abruf**

In einem Live-Marktszenario können die Preise innerhalb kurzer Zeit steigen oder fallen. Dies wirkt sich auf die Grid-Orders aus, die von einer Kauforder -> Verkaufsorder ODER Verkaufsorder -> Kauforder umgedreht werden können. Diese umgekehrten Orders erfordern eine Live-Signaturautorisierung des Benutzers, die schwierig zu erhalten sein kann, wenn der Benutzer nicht an seinem Computer sitzt.

### Einführung in die dezentrale Grid-Strategie <a href="#id-2nxamoaag68g" id="id-2nxamoaag68g"></a>

Um das Ziel zu erreichen, eine dezentralisierte Grid-Strategie-Funktion zu entwickeln, identifizieren und definieren wir zunächst die Konstanten in einem Standard-Grid-Strategie-Setup.

**Konstanten**

Level-Betrag – Zugewiesene Vermögenswerte für jedes Grid-Level, von der Eingabe des Benutzers bestimmt.

Grid-Offset – Differenz zwischen den einzelnen Grid-Leveln, bestimmt durch Preisspanne und Anzahl der Grid-Level.

Order-Offset – Die Differenz zwischen den einzelnen Orders, wurde für die Berechnung von Reverse-Orders erstellt. Entspricht dem Grid-Offset.

**Kauf-/Verkaufs-Grids**

Im Wesentlichen ist das Standard-Grid-Strategie-Setup ein bidirektionaler Trading-Bot. Um die Komplikationen in Bezug auf die Benutzersignatur zu vereinfachen, wird das Grid-Strategie-Setup in zwei Grid-Kategorien unterteilt, nämlich:

Kauf-Grid – Einrichten von Kauf-Grid-Orders

Verkaufs-Grid – Einrichten von Verkaufs-Grid-Orders

**Grid-Signaturen**

Der nächste Schritt besteht darin, die Transaktionssignaturen für jedes Kauf-/Verkaufs-Grid einzurichten. Die zuvor definierten Konstanten werden in jede Grid-Transaktionssignatur gebündelt. Entscheidend ist, dass die Transaktionssignatur an die erste Gridorder gebunden ist, die als das Grid definiert ist, das dem aktuellen Marktpreis am nächsten kommt. Nachfolgende Gridorders werden entsprechend mit der Signaturautorisierung der ersten Gridorder eingerichtet.

{% hint style="info" %}
Beispielsweise liegt der aktuelle Marktpreis von ETH bei 2000 $.

Für das Buy Grid – die erste Grid-Order („Buy 1“) wird auf dem nächstgelegenen Grid-Level <2000 $ definiert.

Für das Sell Grid – die erste Grid-Order („Sell 1“) wird auf dem nächstgelegenen Grid-Level >2000 $ definiert.
{% endhint %}

Grundsätzlich löst dies die Notwendigkeit für den Benutzer, mehrere Transaktionen zu unterzeichnen, während die Grid-Strategie aktiv ist.

**Beispiel: ETH/USDC**

1. Benutzer A richtet eine manuelle Gridstrategie für ETH/USDC im Bereich von 1800 bis 2300 USD ein, während der aktuelle Preis von ETH bei 2050 USD liegt. 10 Gridlinien werden mit zugewiesenen Vermögenswerten von 0,5 ETH und 950 USDC hinzugefügt.
2. Infolgedessen werden 5 Sell Grids und 5 Buy Grids entsprechend den Eingabeparametern eingerichtet.
3. Für das Sell Grid muss der Benutzer die „Sell Grid-Transaktionssignatur“ auf dem ersten Sell Grid Level (aka „Verkauf 1“) genehmigen und unterzeichnen, damit der Gridstrategiemechanismus nachfolgende Sell Grid Orders einrichten kann.
4. Für das Buy Grid muss der Benutzer die „Buy Grid-Transaktionssignatur“ auf dem ersten Buy Grid Level (aka „Kauf 1“) genehmigen und unterzeichnen, damit der Gridstrategiemechanismus nachfolgende Buy Grid Orders einrichten kann.
5. Der Benutzer kann sich einfach zurücklehnen, entspannen und zusehen, wie die Gridstrategie die verschiedenen Grid Orders ausführt (im Wesentlichen niedrig kaufen und hoch verkaufen) und passive Gewinne für den Benutzer generiert!

Durch dieses innovative technische Design können Benutzer nun die Vorteile des Grid-Handels nutzen UND gleichzeitig die volle Kontrolle über ihre eigenen Vermögenswerte haben.

![](<../.gitbook/assets/0 (1).gif>)

_Innovatives technisches Design der dezentralen Grid-Strategie_

### Strategien für Grid Trading <a href="#id-7fe5kmpe0tmr" id="id-7fe5kmpe0tmr"></a>

Beim Grid Trading werden 3 gängige Strategien verwendet, die weitgehend von den Markttrends und der Performance des zugrunde liegenden Vermögenswerts abhängen.

#### **Normale Grid-Strategie**

Diese Strategie wird am besten in einem turbulenten Markt eingesetzt, in dem sich der zugrunde liegende Vermögenswert konsolidiert oder bewegt. Über eine normale Grid-Strategie kann der Händler sowohl Kauf- als auch Verkaufsaufträge innerhalb des vordefinierten Preisbereichs erteilen und so effektiv passive Gewinne aus der Preisbewegung des Vermögenswerts erzielen.

![Normale Grid-Strategie in Aktion](<../.gitbook/assets/1 (3).gif>)



#### **Buy Grid-Strategie**

Diese Strategie wird am besten in einem Abwärtstrendmarkt eingesetzt, in dem der zugrunde liegende Tokenpreis weiter fallen könnte. Über eine Buy Grid-Strategie kann der Händler eine Reihe von Kaufaufträgen unter dem Marktpreis platzieren, sodass er den Vermögenswert zum Tiefstpreis kaufen kann. Darüber hinaus werden die Grid-Aufträge in Verkaufsaufträge umgewandelt, wenn der Preis steigt, wodurch der Händler innerhalb des Grid-Bereichs profitiert.

Die Hauptprämisse der Buy Grid-Strategie ist diese: Der zugrunde liegende Token hat ein gutes Potenzial, das für eine langfristige Anlage geeignet ist, sodass der Händler beim Dollar-Averaging in den Token profitiert, selbst wenn sein Preis außerhalb des Grid-Bereichs liegt.

![](<../.gitbook/assets/2 (3).gif>)

#### **Sell ​​Grid-Strategie**

Dies ist der Buy Grid-Strategie ähnlich, aber in eine andere Richtung. Die Sell Grid-Strategie wird am besten in einem Aufwärtstrendmarkt eingesetzt, in dem der zugrunde liegende Token weiter an Wert gewinnt. Über eine Sell Grid-Strategie kann der Händler eine Reihe von Verkaufsaufträgen über dem Marktpreis platzieren, sodass er den Vermögenswert zum Höchstpreis verkaufen kann. Darüber hinaus werden die Grid-Aufträge in Kaufaufträge umgewandelt, wenn der Preis nach unten ausbricht, wodurch der Händler innerhalb des Grid-Bereichs profitiert.

Der Hauptvorteil der Sell Grid-Strategie besteht darin, dass der Händler schrittweise Gewinne mitnehmen kann, wenn der zugrunde liegende Token-Preis nach oben ausbricht, die Gewinne auf dem Weg nach oben maximiert und zurückkauft, wenn der Token-Preis nach unten zurückgeht.

![](<../.gitbook/assets/3 (3).gif>)

### Fazit <a href="#mty6ujvalx0w" id="mty6ujvalx0w"></a>

Grid-Trading ist eine automatisierte Handelsstrategie, die nicht von menschlichen Emotionen beeinflusst wird und vollständig durch Code bestimmt wird. Diese Strategie lässt sich am besten in einem Seitwärtsmarkt umsetzen und generiert passives Einkommen für Benutzer, ohne ständig auf den Bildschirm schauen zu müssen.

Darüber hinaus haben Benutzer durch die Nutzung des dezentralen Designs von [DeGate](https://app.degate.com/?utm_source=gridguidebook) für die Grid-Strategie-Funktion nun die volle Kontrolle über ihre Gelder und können gleichzeitig die Vorteile des automatisierten Handels genießen. Mit der Reihe von Funktionen von [DeGate](https://app.degate.com/?utm_source=gridguidebook) wie Limit-Orders und dezentralem Grid-Trading können Benutzer endlich ruhig schlafen, unabhängig von den Marktbedingungen.



### Leitfaden zur Grid-Strategie <a href="#z8byqwf0voqm" id="z8byqwf0voqm"></a>

Grid-Strategie oder Grid-Trading ist ein leistungsstarkes Handelstool, das den Kauf und Verkauf innerhalb eines definierten Bereichs automatisiert. Eine Grid-Strategie platziert automatisch Kaufaufträge, wenn die Preise fallen, und Verkaufsaufträge, wenn sie steigen. So können Sie Marktschwankungen ausnutzen und Gewinne erzielen.

### Wie richte ich die Grid-Strategie auf DeGate ein? <a href="#xwo7bpg25a2c" id="xwo7bpg25a2c"></a>

Lassen Sie uns das unten aufgeführte Beispiel mit dem Paar ETH/USDC verwenden.

![](<../.gitbook/assets/0 (13).png>)

#### Grid-Strategie-Modus auswählen <a href="#id-6hpvorbehppi" id="id-6hpvorbehppi"></a>

Es stehen 2 Grid-Strategie-Modi zur Auswahl.

**Auto:** Richten Sie die Grid-Strategie mit automatisch generierten, vom System empfohlenen Parametern ein.

**Manuell:** Passen Sie die Grid-Strategie-Parameter Ihren Wünschen entsprechend an.

Für Grid-Strategie-Neulinge wird empfohlen, mit dem \[Auto]-Modus zu beginnen.

<figure><img src="../.gitbook/assets/image (62).png" alt=""><figcaption></figcaption></figure>

<figure><img src="../.gitbook/assets/image (61).png" alt=""><figcaption></figcaption></figure>



#### Grid-Strategie einrichten \[AUTO] <a href="#eqnltdssxmu0" id="eqnltdssxmu0"></a>

1. Klicken Sie auf den \[Auto] Tab
2. Geben Sie den Betrag ein, der für die Grid-Strategie zugewiesen werden soll \[ETH/USDC]. Geben Sie entweder den ETH- oder den USDC-Betrag ein und das System berechnet den entsprechenden Betrag für die Grid-Strategie.

Stellen Sie sicher, dass Ihr DeGate-Guthaben über ausreichend ETH und USDC verfügt.

<figure><img src="../.gitbook/assets/image (63).png" alt=""><figcaption></figcaption></figure>

3. Die empfohlenen Parameter werden angezeigt.
4. Klicken Sie auf „Gridstrategie erstellen“, um die Einrichtung abzuschließen und mit dem Verdienen zu beginnen.

<figure><img src="../.gitbook/assets/image (64).png" alt=""><figcaption></figcaption></figure>

<figure><img src="../.gitbook/assets/image (65).png" alt=""><figcaption></figcaption></figure>

#### Grid-Strategie einrichten \[MANUELL] <a href="#wwcaivvc8n0z" id="wwcaivvc8n0z"></a>

1. Klicken Sie auf den Tab \[Manuell]. Sie können die Parameter für Ihre individuelle Grid-Strategie ändern.
2. Preisspanne: Die oberen und unteren Preisgrenzen definieren die Preisspanne, in der die Grid-Strategie ausgeführt wird.
3. Anfängliche Zuweisung: Der Betrag, der für die Grid-Strategie zugewiesen werden soll. Geben Sie entweder den ETH- oder den USDC-Betrag ein und das System berechnet den entsprechenden Betrag.
4. Anzahl der Grids: Die Anzahl der Kauf- und Verkaufsaufträge, die die Grid-Strategie innerhalb der Preisspanne erteilt.
5. Menge pro Grid (≥ 50 USD): Der Betrag an ETH, der für jede Grid-Order zugewiesen wird.
6. Klicken Sie auf „Grid-Strategie erstellen“, um die Einrichtung abzuschließen und mit dem Verdienen zu beginnen.

{% hint style="info" %}
Für jede Grid-Order ist eine Mindestauftragsmenge von 25 USD erforderlich.
{% endhint %}

<figure><img src="../.gitbook/assets/image (66).png" alt=""><figcaption></figcaption></figure>

Für eine optimale Rentabilität wird empfohlen, die Gridstrategie so einzurichten, dass der aktuelle Marktpreis innerhalb der Preisspanne liegt.
