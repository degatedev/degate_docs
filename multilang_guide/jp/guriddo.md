---
description: DeGate DEXにおける分散型グリッド戦略
---

# 分散型グリッド戦略

### **グリッド戦略とは？**&#x20;

グリッド戦略またはグリッドトレーディングは、指定されたレンジ内での自動売買を行うトレーディングメカニズムです。指定された価格範囲内で一連の買い注文および売り注文を配置し、買い注文が実行されると、即座により高いグリッドレベルで別の売り注文が配置され、その逆も行われます。グリッド戦略は、価格が定期的に変動する横ばい市場で最も効果的に機能し、小さな価格の変化で利益を得ることができます。

[DeGate DEX](https://app.degate.com/?utm_source=gridguidebook)では、手数料なしで、自己管理方式による分散型[グリッド戦略を実行できます](https://app.degate.com/?utm_source=gridguidebook)。

{% embed url="https://youtu.be/uvkBgcWa6zc" %}



#### **グリッド戦略の利点**

グリッド戦略は、常に画面を注視する余裕がないトレーダーに人気があります。グリッド戦略の主な利点には以下のようなものがあります。

自動化 - 上限価格と下限価格を最初に定義し、その後のグリッド買い/売り注文が、基礎資産の価格変動に応じて自動的に配置および実行されます。グリッド戦略は24時間365日稼働し（つまり低価格で買って高価格で売る）、トレーダーに受動的な利益を生成します。

適応性 - グリッドの密度は様々な状況に合わせて最適化できます。短期では、一日の価格変動からミクロの利益を得るために何百ものグリッドを設定することができ、長期では、全体としての横ばいトレンドから利益を得るためにより大きな範囲を選択することができます。

収益性 - グリッドトレーディングは、明確なトレンドを示していない横ばい市場で最も効果的に機能します。トレーダーは、対象資産の価格が上昇か下落かを予測する必要はなく、グリッド戦略を開始した後は、結果を監視する以外の入力は必要ありません。



### **グリッド戦略の設計上の課題（分散型）**

グリッド戦略機能は、中央集権型取引所（CEX）で一般的に見られます。CEXでは、ユーザーが資金を管理していないため、取引実行が容易です。現状の市場では、いくつかの課題から分散型グリッドトレーディングプロトコルは存在しません。

**ウォレット署名**

典型的なグリッドトレーディングの設定は、ユーザーの入力に応じて2から200のグリッドレベルで構成されることがあり、すべてのグリッドレベルは買いまたは売りの指値注文を表し、ユーザーのウォレット署名が必要です。それに加え、署名の認証には数秒かかることがあり、取引がミリ秒単位で動く市場ではグリッド注文の実行に影響が出る可能性があります。

**ライブ・オンデマンド署名**

ライブ市場のシナリオでは、価格が短期間に急上昇または急下降することがあります。これによりグリッド注文が影響を受け、買い注文が売り注文に、またはその逆に切り替わることがあります。これらの反転注文には、ユーザーからのライブ署名認証が必要となるため、ユーザーがパソコンから離れていると取得が難しくなります。

**分散型グリッド戦略の導入**

分散型グリッド戦略機能を構築するために、まず標準的なグリッド戦略設定の定数を特定および定義します。

**定数**

レベル量 - ユーザーの入力により決定された、各グリッドレベルに割り当てられた資産。

グリッドオフセット - 価格範囲とグリッドレベルの数で決定される、各グリッドレベル間の差。

注文オフセット - 反転注文の計算のために作成された、各注文間の差。グリッドオフセットに相当。

**買い/売りグリッド**

基本的に、標準的なグリッド戦略の設定は、双方向のトレーディングボットです。ユーザー署名に関する複雑さを簡単にするために、グリッド戦略セットアップは買いグリッドと売りグリッドの2つのカテゴリに分けられます。

買いグリッド - 買いグリッド注文の設定

売りグリッド - 売りグリッド注文の設定

**グリッド署名**

次のステップは、各買い/売りグリッドのトランザクション署名を設定します。前述した定数は、各グリッドトランザクション署名にバンドルされます。特に、トランザクション署名は、現在の市場価格に最も近いグリッドとして定義された最初のグリッド注文に結び付けられ、その後のグリッド注文は最初のグリッド注文の署名認証に従って設定されます。

{% hint style="info" %}
例えば、ETHの現在の市場価格が2000の場合、買いグリッド−最初のグリッド注文（「買い1」）は2000の場合、買いグリッド−最初のグリッド注文（「買い1」）は2000未満の最も近いグリッドレベルで定義され、

売りグリッド - 最初のグリッド注文（「売り1」）は$2000を超える最も近いグリッドレベルで定義されます。

基本的に、これによりユーザーがグリッド戦略がライブで稼働中に複数の取引を署名する必要がなくなります。
{% endhint %}



**例: ETH/USDC**

1.ユーザーAは、ETH/USDCの手動グリッド戦略を1800−2300の範囲で、ETHの現在価格が$2050であるときに設定します。 10本のグリッドラインが追加され、0.5 ETHおよび950 USDCの資産が割り当てられます。

2.その結果、入力パラメータに基づいて、5つの売りグリッドと5つの買いグリッドが設定されます。

3.売りグリッドについては、最初の売りグリッドレベル（つまり「売り1」）で「売りグリッドトランザクション署名」を承認および署名する必要があります。これにより、グリッド戦略メカニズムがその後の売りグリッド注文を設定できるようになります。

4.買いグリッドについては、最初の買いグリッドレベル（つまり「買い1」）で「買いグリッドトランザクション署名」を承認および署名する必要があります。これにより、グリッド戦略メカニズムがその後の買いグリッド注文を設定できるようになります。

5.ユーザーは単にリラックスして、グリッド戦略がさまざまなグリッド注文を実行し（基本的には安く買って高く売り）、自己利益を生み出すのを見るだけです！

{% hint style="info" %}
この革新的な技術設計を通じて、ユーザーはグリッドトレーディングの利点を享受しつつ、自分の資産を完全に管理することができます。
{% endhint %}

<figure><img src="../.gitbook/assets/1.gif" alt=""><figcaption><p>分散型グリッド戦略の革新的な技術設計</p></figcaption></figure>



### **グリッドトレーディングの戦略**

市場トレンドおよび基礎資産のパフォーマンスに大きく依存する3つの一般的な戦略があります。



#### **通常のグリッド戦略**

原資産が統合またはレンジングしている変動市場で最も適しています。通常のグリッド戦略を通じて、トレーダーは事前に定義された価格範囲内で買い注文および売り注文を設定し、資産の価格変動からパッシブな利益を効果的に得ることができます。

<figure><img src="../.gitbook/assets/2 (1).gif" alt=""><figcaption><p>通常のグリッド戦略の実践</p></figcaption></figure>

\


#### **買いグリッド戦略**

この戦略は、基礎トークン価格がさらに下落する可能性がある下降トレンド市場で最も適しています。買いグリッド戦略を通じて、トレーダーは市場価格より下に一連の買い注文を設定し、安い価格で資産を購入できるようにします。さらに、価格が反発した場合、グリッド注文は売り注文に切り替わり、グリッド範囲内でトレーダーに利益をもたらします。

買いグリッド戦略の主な前提は、基礎トークンが良好な将来性を持ち、長期的な保有に適しているということです。したがって、トークン価格がグリッド範囲外に下落しても、トレーダーはドル平均法でトークンに投資する利益を得ることができます。

<figure><img src="../.gitbook/assets/3 (1).gif" alt=""><figcaption></figcaption></figure>

#### **売りグリッド戦略**

これは買いグリッド戦略と似ていますが、異なる方向に向かいます。売りグリッド戦略は、基礎トークンがさらに上昇する可能性がある上昇トレンド市場で最も適しています。売りグリッド戦略を通じて、トレーダーは市場価格より上に一連の売り注文を設定し、高値で資産を売却できます。さらに、価格が下降した場合、グリッド注文は買い注文に切り替わり、グリッド範囲内でトレーダーに利益をもたらします。

売りグリッド戦略の主な利益はこれです：トレーダーは、基礎トークンの価格が上昇するにつれて利益を徐々に得ることができ、トークン価格が下降する際に買い戻すことで利益を最大化できます。

<figure><img src="../.gitbook/assets/4 (1).gif" alt=""><figcaption></figcaption></figure>

### **結論**

グリッドトレーディングは、人間の感情に影響されず、完全にコードによって決定される自動化されたトレーディング戦略です。この戦略は、横ばい市場で最も適しており、ユーザーが常に画面を注視する必要なく、パッシブな収入を生成します。

その上、DeGateの非集権的な設計をグリッド戦略機能に活用することで、ユーザーは資金の完全な管理をしながら、自動売買の利便性を享受できるようになります。DeGateのような様々な特徴で、リミット注文や分散型グリッドトレーディングが活用できることで、ユーザーは市場の状態に関係なく安心して休むことができます。



### **グリッド戦略ガイドブック**

グリッド戦略、またはグリッド取引は、定義された価格範囲内で自動的に売買を行う強力な取引ツールです。グリッド戦略では、価格が下落すると自動的に買い注文が、上昇すると売り注文が実行されるため、市場の変動を利用して利益を生み出すことができます。



### **DeGateでグリッド戦略を設定する方法**

ETH/USDCペアを使用したガイド例を用いて説明します。

![](<../.gitbook/assets/0 (1).png>)

#### **グリッド戦略モードを選択する**

2つのグリッド戦略モードから選択できます。

**自動**: システムが推奨する自動生成されたパラメータを使用してグリッド戦略を設定します。

**手動**: 好みに合わせてグリッド戦略パラメータをカスタマイズします。

{% hint style="info" %}
グリッド戦略を初めて使用する場合は、\*\*\[自動]\*\*モードから開始することをお勧めします。
{% endhint %}

![](<../.gitbook/assets/1 (2).png>)

![](<../.gitbook/assets/2 (2).png>)

#### **グリッド戦略\[自動]を設定する**

1.\*\*\[自動]\*\*タブをクリックします。

2.グリッド戦略\[ETH/USDC]に割り当てる金額を入力します。ETHまたはUSDCのいずれかの金額を入力すると、システムがグリッド戦略に対応する金額を計算します。

{% hint style="info" %}
DeGateの残高に十分なETHとUSDCがあることを確認してください。
{% endhint %}

![](<../.gitbook/assets/3 (2).png>)

3.推奨パラメータが表示されます。

4.\*\*「グリッド戦略を作成」\*\*をクリックして設定を完了し、収益の獲得を開始します。

![](<../.gitbook/assets/4 (2).png>)

![](<../.gitbook/assets/5 (1).png>)

#### **グリッド戦略\[手動]を設定する**

1.\*\*\[手動]\*\*タブをクリックします。カスタマイズしたグリッド戦略のパラメータを変更できます。

2.価格範囲: グリッド戦略を実行する価格帯の上限と下限を定義します。

3.初期割り当て: グリッド戦略に割り当てる資金の額。ETHまたはUSDCのいずれかの金額を入力すると、システムが対応する金額を計算します。

4.グリッド数: グリッド戦略が価格範囲内に配置する買い注文と売り注文の数。

5.グリッドあたりの数量（50ドル以上）: 各グリッド注文に割り当てるETHの金額。

6.\*\*「グリッド戦略を作成」\*\*をクリックして設定を完了し、収益の獲得を開始します。

{% hint style="info" %}
各グリッド注文には50ドル以上の最低注文額の要件があります。
{% endhint %}

![](<../.gitbook/assets/6 (1).png>)

最適な収益性を得るには、現在の市場価格が価格範囲内に入るようにグリッド戦略を設定することをお勧めします。