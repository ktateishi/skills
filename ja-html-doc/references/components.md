# コンポーネント

<!-- 自動生成：src/pages/catalog.html から作られる。直接編集しない -->

ドキュメントで使える部品と、そのまま使える HTML。ここに載っていない独自クラスは使わない。

## ドキュメントヘッダ

すべてのドキュメントの冒頭に置きます。メタ情報はタイトルと更新日だけで、その下に「要点」の見出しを付けた要約を置きます。「要点」のボックス（`note point`）は、要約以外には使いません。

```html
<header class="doc-header">
  <h1>APIゲートウェイの認証フロー</h1>
  <dl class="doc-meta">
    <div><dt>更新日</dt><dd><time datetime="2026-09-29">2026年9月29日</time></dd></div>
  </dl>
  <div class="note point">
    <span class="note-title">要点</span>
    <p>2〜3行の要約。</p>
  </div>
</header>
```

## 見出しと本文

セクションは`<section>`と`<h2>`で作ります。目次は`<h2>`から自動で作られるので、書く必要はありません。セクション内の小見出しには`<h3>`を使います。`<h4>`以下は使いません。

```html
<h3>小見出しの例</h3>
<p>本文の段落です。<strong>特に重要な語句</strong>は太字にします。インラインのコードは<code>gatewayctl apply</code>のように書き、キー操作は<kbd>Ctrl</kbd> + <kbd>S</kbd>のように書きます。リンクは<a href="#usage">このように</a>表示されます。</p>
<ul>
  <li>順序のない箇条書き</li>
  <li>項目は体言止めか、です・ます調の文でそろえる</li>
</ul>
<ol>
  <li>順序のある箇条書き</li>
  <li>手順を表すときはステップを使う</li>
</ol>
```

## 注記

本文から切り出して目立たせたい情報に使います。補足・ヒント・注意・警告の4種があり、重要度に応じて使い分けます。見出しの文言は種類名のままにします。

```html
<div class="note info">
  <span class="note-title">補足</span>
  <p>本文の理解を助ける追加の情報。結論を強調したいときもこれを使います。</p>
</div>
<div class="note tip">
  <span class="note-title">ヒント</span>
  <p>知っていると便利な使い方や近道。</p>
</div>
<div class="note caution">
  <span class="note-title">注意</span>
  <p>見落とすと不具合や手戻りにつながる事項。</p>
</div>
<div class="note warning">
  <span class="note-title">警告</span>
  <p>データの消失やセキュリティ事故など、取り返しのつかない結果につながる事項。</p>
</div>
```

## コードブロック

ヘッダに言語名を書き、`<code>`に`language-xxx`クラスで言語を必ず明示します。コード中の`<`と`&`は`&lt;`、`&amp;`に置き換えます。コピーボタンは自動で付きます。構文の色分けには、コード強調スクリプトの埋め込みが必要です。

```html
<div class="code">
  <div class="code-header"><span>TypeScript</span></div>
  <pre><code class="language-typescript">// アクセストークンの有効期限を確認する
export function isExpired(token: { exp: number }, now = Date.now()): boolean {
  return token.exp * 1000 &lt;= now;
}</code></pre>
</div>
```

## 表

表は`table-wrap`で囲み、スマホで横にスクロールできるようにします。表題は`<caption>`に「表1　…」の形で書きます。数値の列には`num`クラスを付けて右寄せにします。

```html
<div class="table-wrap">
  <table>
    <caption>表1　プラン別の月額費用</caption>
    <thead><tr><th>プラン</th><th>対象</th><th class="num">月額（円）</th></tr></thead>
    <tbody>
      <tr><td>ライト</td><td>個人・検証用</td><td class="num">0</td></tr>
      <tr><td>スタンダード</td><td>小規模チーム</td><td class="num">12,000</td></tr>
      <tr><td>ビジネス</td><td>部門単位での利用</td><td class="num">48,000</td></tr>
    </tbody>
  </table>
</div>
```

## ステップ

手順書の操作手順に使います。各ステップには短い見出しを付け、必要ならコードブロックを含めます。

```html
<ol class="steps">
  <li>
    <span class="step-title">設定ファイルを検証する</span>
    <p>反映する前に、設定ファイルの書式を検証します。</p>
    <div class="code">
      <div class="code-header"><span>Bash</span></div>
      <pre><code class="language-bash">gatewayctl validate --config routes.yaml</code></pre>
    </div>
  </li>
  <li>
    <span class="step-title">ステージング環境に反映する</span>
    <p>検証に成功したら、ステージング環境に反映して動作を確認します。</p>
  </li>
</ol>
```

## チェックリスト

作業の前提条件や、完了時の確認事項を並べるときに使います。

```html
<ul class="checklist">
  <li>管理者権限のアカウントでログインしている</li>
  <li>作業前のバックアップを取得している</li>
  <li>関係者に作業の開始を連絡している</li>
</ul>
```

## 数値カード

報告書で主要な数値を並べて示すときに使います。増減は`up`（良い方向）と`down`（悪い方向）で色分けします。数値が増えることが悪い指標（エラー率など）では、増加でも`down`を使います。

```html
<div class="stats">
  <div class="stat"><span class="stat-label">月間アクティブ利用者</span><span class="stat-value">12,480</span><span class="stat-delta up">前月比 +8.2%</span></div>
  <div class="stat"><span class="stat-label">平均応答時間</span><span class="stat-value">182ms</span><span class="stat-delta up">前月比 −24ms</span></div>
  <div class="stat"><span class="stat-label">エラー率</span><span class="stat-value">0.42%</span><span class="stat-delta down">前月比 +0.11pt</span></div>
</div>
```

## 図

図はインラインSVGで描きます。色やフォントは直接書かず、`fig-`で始まるクラスを使います。`<text>`はx, yの位置が文字の中心になります。`<title>`で図の内容を説明し、キャプションは「図1　…」の形で書きます。

```html
<figure>
  <svg viewBox="0 0 640 170" role="img" aria-labelledby="fig-example-title">
    <title id="fig-example-title">クライアントから内部サービスまでのリクエストの流れ</title>
    <defs>
      <marker id="fig-arrow" viewBox="0 0 10 10" refX="9" refY="5" markerWidth="7" markerHeight="7" orient="auto">
        <path class="fig-arrowhead" d="M0,0 L10,5 L0,10 z"/>
      </marker>
    </defs>
    <rect class="fig-node" x="20" y="55" width="130" height="56" rx="6"/>
    <text x="85" y="83">クライアント</text>
    <rect class="fig-node-accent" x="255" y="45" width="140" height="76" rx="6"/>
    <text class="fig-accent" x="325" y="74">APIゲートウェイ</text>
    <text class="fig-label" x="325" y="97">検証・詰め替え</text>
    <rect class="fig-node" x="490" y="20" width="130" height="50" rx="6"/>
    <text x="555" y="45">注文サービス</text>
    <rect class="fig-node" x="490" y="98" width="130" height="50" rx="6"/>
    <text x="555" y="123">在庫サービス</text>
    <line class="fig-edge" x1="150" y1="83" x2="252" y2="83" marker-end="url(#fig-arrow)"/>
    <text class="fig-label" x="201" y="70">アクセストークン</text>
    <line class="fig-edge" x1="395" y1="72" x2="487" y2="46" marker-end="url(#fig-arrow)"/>
    <line class="fig-edge-dashed" x1="395" y1="94" x2="487" y2="122" marker-end="url(#fig-arrow)"/>
    <text class="fig-label" x="440" y="84">内部 JWT</text>
  </svg>
  <figcaption>図1　リクエストの流れ</figcaption>
</figure>
```

## 折りたたみ

本筋から外れる補足や、長い参考情報を隠しておくときに使います。読み手が開かなくても本文が理解できる内容だけを入れます。

```html
<details class="fold">
  <summary>補足：なぜ内部サービスで検証しないのか</summary>
  <p>検証をゲートウェイに集約することで、ルールの変更を1か所で済ませられます。</p>
</details>
```

## 脚注

本文の流れを止めたくない出典や細かい注釈に使います。脚注の一覧は、そのセクションの末尾に置きます。

```html
<p>JWKSのキャッシュは10分に設定しています<sup class="fnref"><a href="#fn1" id="fnref1">1</a></sup>。</p>
<ol class="footnotes">
  <li id="fn1">認可サーバーの鍵ローテーション間隔（24時間）に対して十分短い値として決めました。<a href="#fnref1" aria-label="本文へ戻る">↩</a></li>
</ol>
```

## 用語集

すべてのドキュメントの最後のセクションとして置きます。見出しは「用語集」で固定です。用語は`dl.terms`で書きます。
