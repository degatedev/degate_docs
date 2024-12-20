---
description: Grid Strategy su DeGate DEX
---

# Strategia a Griglia su DeGate DEX

### Che cosa è la Strategia a Griglia (Grid Strategy)?

La Strategia a Griglia, o grid trading, è un meccanismo di trading che automatizza l'acquisto e la vendita entro un intervallo di prezzo definito. Consente di posizionare una serie di ordini di acquisto e vendita all'interno di un intervallo di prezzo stabilito; quando un ordine di acquisto viene eseguito, viene immediatamente posizionato un altro ordine di vendita a un livello di griglia superiore, e viceversa. Questa strategia funziona meglio in mercati laterali, dove i prezzi fluttuano regolarmente, permettendo di trarre profitto da piccoli cambiamenti di prezzo.

Su [DeGate DEX](https://app.degate.com/?utm_source=gridguidebook), puoi fare una strategia a [griglia](https://app.degate.com/en/grid/USDC/ETH/?utm_source=gridguidebook) decentralizzata senza commissioni in modalità self-custody.

{% embed url="https://youtu.be/uvkBgcWa6zc" %}

### **Benefici della Strategia a Griglia (Grid Strategy)**:

La Strategia a Griglia è popolare tra i trader che non hanno il tempo o l’energia per monitorare costantemente il mercato. I vantaggi principali includono:

• Automazione: una volta definiti i limiti di prezzo, gli ordini di acquisto/vendita vengono eseguiti automaticamente in base al movimento dei prezzi dell’asset, generando profitti passivi.

• Adattabilità: la densità della griglia può essere ottimizzata per diverse circostanze, consentendo di ottenere profitti sia a breve che a lungo termine.

• Redditività: funziona meglio in mercati laterali, permettendo di trarre profitto senza dover prevedere le tendenze.

### **Sfide di progettazione della Strategia a Griglia (Grid Strategy) Decentralizzata:**

La funzione della Strategia a Griglia è comune negli exchange centralizzati (CEX), dove l’esecuzione delle operazioni è facilitata poiché gli utenti non hanno la custodia dei loro fondi. Tuttavia, nei protocolli decentralizzati, ci sono alcune sfide:

• **Firma del Wallet**: Ogni livello di griglia richiede la firma del wallet dell’utente, rallentando l’esecuzione degli ordini.

• **Firma in tempo reale**: In un mercato attivo, gli ordini potrebbero richiedere l’autorizzazione immediata, difficile da ottenere se l’utente è lontano.

### Introduzione alla Strategia a Griglia Decentralizzata:

Per sviluppare una funzione di strategia a griglia decentralizzata, è essenziale identificare e definire le costanti in un setup standard. Queste includono:

#### **Costanti**

* **Livello di Importo**: Risorse allocate per ogni livello di griglia, determinate dall'input dell'utente.
* **Offset della Griglia**: Differenza tra ogni livello di griglia, determinata dall'intervallo di prezzo e dal numero di livelli.
* **Offset degli Ordini**: Differenza tra ogni ordine, creata per il calcolo degli ordini inversi. Equivalente all'offset della griglia.

#### **Griglie di Acquisto/Vendita**

Fondamentalmente, la configurazione standard della strategia a griglia è un bot di trading bidirezionale. Per semplificare le complicazioni relative alla firma dell’utente, la configurazione della strategia a griglia è suddivisa in due categorie:

• Griglia di Acquisto: configurazione degli ordini di acquisto nella griglia.

• Griglia di Vendita: configurazione degli ordini di vendita nella griglia.

#### **Firme delle Griglie**:

Il passo successivo consiste nell'impostare le firme delle transazioni per ogni griglia di acquisto/vendita. Le costanti precedentemente definite vengono incluse in ogni firma di transazione della griglia. Criticamente, la firma della transazione sarà legata al primo ordine di griglia, definito come quello più vicino al prezzo di mercato attuale. Gli ordini di griglia successivi saranno impostati di conseguenza, con l'autorizzazione della firma proveniente dal primo ordine di griglia.

{% hint style="info" %}
Ad esempio, se il prezzo di mercato attuale di ETH è di $2000:

* **Per la Griglia di Acquisto**: il primo ordine di griglia ("Buy 1") è definito al livello di griglia più vicino inferiore a $2000.
* **Per la Griglia di Vendita**: il primo ordine di griglia ("Sell 1") è definito al livello di griglia più vicino superiore a $2000.
{% endhint %}

Fondamentalmente, questo risolve la necessità per l'utente di firmare più transazioni mentre la strategia a griglia è attiva. Grazie all'associazione della firma con il primo ordine di griglia, gli ordini successivi vengono eseguiti automaticamente senza richiedere ulteriori autorizzazioni, semplificando l'intero processo e migliorando l'efficienza operativa.

**Esempio: ETH/USDC**

1. L’utente A imposta una strategia a griglia manuale per ETH/USDC nell’intervallo di $1800 - $2300, mentre il prezzo attuale di ETH è di $2050. Vengono aggiunte 10 linee di griglia con asset allocati di 0,5 ETH e 950 USDC.
2. Di conseguenza, vengono impostate 5 griglie di vendita e 5 griglie di acquisto in base ai parametri di input.
3. Per la griglia di vendita, l’utente dovrà approvare e firmare la “Firma della transazione della griglia di vendita” sul primo livello della griglia di vendita (ovvero “Sell 1”), abilitando il meccanismo della strategia a griglia per impostare i successivi ordini di vendita della griglia.
4. Per la griglia di acquisto, l’utente dovrà approvare e firmare la “Firma della transazione della griglia di acquisto” sul primo livello della griglia di acquisto (ovvero “Buy 1”), abilitando il meccanismo della strategia a griglia per impostare i successivi ordini di acquisto della griglia.
5. L’utente deve semplicemente rilassarsi e guardare la strategia a griglia eseguire i vari ordini di griglia (essenzialmente comprando a un prezzo basso e vendendo a un prezzo alto), generando profitti passivi per l’utente!

{% hint style="info" %}
Grazie a questo design tecnico innovativo, gli utenti possono ora godere dei benefici del grid trading mantenendo al contempo la piena custodia dei propri asset.&#x20;
{% endhint %}

<figure><img src=".gitbook/assets/grid gif1 (1).gif" alt=""><figcaption><p>Design tecnico innovativo della Strategia a Griglia Decentralizzata</p></figcaption></figure>

### **Strategie per il Grid Trading**

Esistono tre strategie comuni nel Grid Trading, che dipendono principalmente dalle tendenze di mercato e dalla performance dell'asset sottostante.

#### **Strategia a Griglia Normale**&#x20;

Questa strategia è ideale in mercati turbolenti in cui l'asset sottostante si sta consolidando o è in fase laterale. Attraverso la Strategia a Griglia Normale, il trader può impostare ordini di acquisto e vendita all'interno di un intervallo di prezzo predefinito, ottenendo profitti passivi dal movimento dei prezzi dell'asset.

<figure><img src=".gitbook/assets/Normal-Grid-EN-v2m (1) (1).gif" alt=""><figcaption><p>Strategia a Griglia Normale in azione</p></figcaption></figure>

#### **Strategia a Griglia di Acquisto**

Questa strategia è ideale in un mercato in tendenza ribassista, dove il prezzo del token potrebbe scendere ulteriormente. Con la Strategia a Griglia di Acquisto, il trader imposta una serie di ordini di acquisto al di sotto del prezzo di mercato, permettendogli di acquistare l'asset a un prezzo basso. Se il prezzo rimbalza, gli ordini di acquisto si trasformano in ordini di vendita, generando profitti all'interno dell'intervallo di griglia.

Il principio base di questa strategia è investire in un token con un buon potenziale a lungo termine, approfittando della mediazione del prezzo anche se scende al di fuori dell'intervallo di griglia.

<figure><img src=".gitbook/assets/Buy-Grid-v20m (1).gif" alt=""><figcaption></figcaption></figure>

#### **Strategia a Griglia di Vendita**

Questa strategia è simile alla Strategia a Griglia di Acquisto, ma si applica in direzione opposta. È ideale in un mercato in tendenza rialzista, dove il prezzo del token potrebbe aumentare ulteriormente. Con la Strategia a Griglia di Vendita, il trader imposta una serie di ordini di vendita al di sopra del prezzo di mercato, permettendogli di vendere l'asset a prezzi elevati. Se il prezzo scende, gli ordini di vendita si trasformano in ordini di acquisto, generando profitti all'interno dell'intervallo di griglia.

Il vantaggio principale di questa strategia è che il trader può realizzare profitti incrementali man mano che il prezzo del token aumenta, massimizzando i guadagni durante la salita e riacquistando l'asset quando il prezzo si ritrae.

<figure><img src=".gitbook/assets/Sell-Grid-v3m (1).gif" alt=""><figcaption></figcaption></figure>

### **Conclusione**

La strategia a griglia è una strategia di trading automatizzata che non è influenzata dalle emozioni umane ed è interamente determinata dal codice. Questa strategia è più efficace in mercati laterali, generando reddito passivo senza la necessità di monitorare costantemente il mercato.

Grazie al design decentralizzato di DeGate, gli utenti possono mantenere la piena custodia dei loro fondi, beneficiando al contempo del trading automatizzato. Con le funzionalità di DeGate, come ordini limite e grid trading decentralizzato, gli utenti possono dormire tranquilli, indipendentemente dalle condizioni di mercato.



### **Come impostare la Strategia a Griglia su DeGate DEX?**

Usiamo l'esempio guidato qui sotto, utilizzando la coppia ETH/USDC.

<figure><img src=".gitbook/assets/image (54).png" alt=""><figcaption></figcaption></figure>

#### **Seleziona la modalità Strategia a Griglia**

Ci sono 2 modalità di Strategia a Griglia tra cui scegliere:

* **Auto**: Imposta la Strategia a Griglia utilizzando i parametri generati automaticamente e consigliati dal sistema.
* **Manuale**: Personalizza i parametri della Strategia a Griglia in base alle tue preferenze.

{% hint style="info" %}
Per i nuovi utenti della Strategia a Griglia, è consigliato iniziare con la modalità \[Auto].
{% endhint %}

<figure><img src=".gitbook/assets/image (55).png" alt=""><figcaption></figcaption></figure>

<figure><img src=".gitbook/assets/image (56).png" alt=""><figcaption></figcaption></figure>

#### **Imposta la Strategia a Griglia \[AUTO]**

1. Clicca sulla scheda \[Auto].
2. Inserisci l'importo da allocare per la Strategia a Griglia \[ETH/USDC]. Inserisci l'importo in ETH o USDC e il sistema calcolerà l'importo corrispondente per la Strategia a Griglia.

{% hint style="info" %}
Assicurati di avere sufficiente ETH e USDC nel tuo saldo su DeGate.
{% endhint %}

<figure><img src=".gitbook/assets/image (57).png" alt=""><figcaption></figcaption></figure>

3. I parametri consigliati verranno visualizzati.
4. Clicca su "Crea Strategia a Griglia" per completare la configurazione e iniziare a guadagnare.

<figure><img src=".gitbook/assets/image (58).png" alt=""><figcaption></figcaption></figure>

<figure><img src=".gitbook/assets/image (59).png" alt=""><figcaption></figcaption></figure>

#### Configura Strategia a Griglia \[MANUALE]

Clicca sulla scheda \[Manuale]. Puoi modificare i parametri per la tua Strategia a Griglia personalizzata.

Fascia di Prezzo: I prezzi limite superiore e inferiore definiscono l'intervallo di prezzo in cui opererà la Strategia a Griglia.

Allocazione Iniziale: L'importo di fondi da destinare alla Strategia a Griglia. Inserisci l'importo in ETH o USDC e il sistema calcolerà l'importo corrispondente.

Numero di Griglie: Il numero di ordini di acquisto e vendita che la Strategia a Griglia effettuerà all'interno della Fascia di Prezzo.

Quantità per Griglia (≥$50): L'importo di ETH assegnato a ciascun ordine della griglia.

Clicca su "Crea Strategia a Griglia" per completare la configurazione e iniziare a guadagnare.

{% hint style="info" %}
C'è un requisito di ordine minimo di $50 per ciascun ordine della griglia.
{% endhint %}

<figure><img src=".gitbook/assets/image (60).png" alt=""><figcaption></figcaption></figure>

{% hint style="info" %}
Per una redditività ottimale, è consigliato impostare la Strategia a Griglia in modo che il prezzo di mercato attuale rientri nell'intervallo di prezzo.
{% endhint %}
