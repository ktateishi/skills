# 図の描き方

図はインライン SVG で描き、`<figure>` で囲む。色・線・フォントは `fig-` で始まるクラスで指定し、デザイントークンの配色に任せる。

## 骨組み

```html
<figure>
  <svg viewBox="0 0 640 200" role="img" aria-labelledby="fig1-title">
    <title id="fig1-title">図の内容を説明する一文</title>
    <defs>
      <marker id="fig1-arrow" viewBox="0 0 10 10" refX="9" refY="5" markerWidth="7" markerHeight="7" orient="auto">
        <path class="fig-arrowhead" d="M0,0 L10,5 L0,10 z"/>
      </marker>
    </defs>
    <rect class="fig-node" x="20" y="70" width="140" height="56" rx="6"/>
    <text x="90" y="98">要素の名前</text>
    <line class="fig-edge" x1="160" y1="98" x2="250" y2="98" marker-end="url(#fig1-arrow)"/>
  </svg>
  <figcaption>図1　図の題名</figcaption>
</figure>
```

## クラス

| クラス | 対象 | 用途 |
|---|---|---|
| `fig-node` | `rect` など | 通常の要素の箱 |
| `fig-node-accent` | `rect` など | 図の主役の箱。1つの図に1〜2個 |
| `fig-edge` | `line`、`path` | 矢印や線 |
| `fig-edge-dashed` | `line`、`path` | 非同期・任意・補助的な流れ |
| `fig-arrowhead` | `marker` 内の `path` | 矢印の先端 |
| `fig-label` | `text` | 線に添える小さな説明 |
| `fig-strong` | `text` | 太字にする |
| `fig-accent` | `text` | `fig-node-accent` の中の名前 |

クラスのない `<text>` は本文色・13px で、`x`、`y` の位置が文字の中心になる。

## 決まりごと

- `viewBox` の幅は640に固定し、高さは内容に合わせる。表示幅は CSS が合わせる。
- 箱の中の文字は、箱の中心座標に置く。1つの箱の文字は全角10字程度までにする。
- `id`（`title` と `marker`）はドキュメント内で一意にするため、`fig1-title`、`fig1-arrow` のように図の番号を付ける。
- `<title>` に図の内容を一文で書く（スクリーンリーダー向け）。
- 要素は7個程度までにする。多いときは図を分ける。
- 流れは左から右、または上から下に向ける。
- 色の指定（`fill`、`stroke`）と `style` 属性はクラスに任せ、SVG に直接書かない。
