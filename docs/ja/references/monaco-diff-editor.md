<script setup>
import Stackbiltz from '../../../../components/Stackbiltz.vue'
</script>

# &lt;MonacoDiffEditor&gt;
`<MonacoDiffEditor>` は、2つのファイルの差分を表示するために利用します。

`<MonacoDiffEditor>` の使用方法は、 [`<MonacoEditor>`](monaco-editor) とほとんど同じです。

<Stackbiltz src="nuxt-starter-vf6nfx?embed=1&file=app.vue&hideNavigation=1&view=preview" />

## 値の設定・取得
```vue
<template>
  <MonacoDiffEditor :original="originalValue" v-model="modifiedValue" />
</template>

<script lang="ts" setup>
const originalValue = ref('変更前の値')
const modifiedValue = ref('変更後の値')
</script>
```
`v-model` は**変更後の値**に対応しています。変更前の値は monaco-editor では読み取り専用になっています。

## 代替表示
```vue
<template>
  <MonacoDiffEditor>
    Loading...
  </MonacoDiffEditor>
</template>
```
`<MonacoDiffEditor>` の子要素がエディタの読み込み中に表示されます。

## プロパティ
### `lang`
- デフォルト値: `plaintext`

配色に用いるプログラミング言語です。`options.language` の値を上書きします。

使用可能な言語の一覧は[こちら](https://github.com/microsoft/monaco-editor/tree/main/src/basic-languages)にあります。

### `options`
- デフォルト値: `{}`

`monaco.editor.createDiffEditor`の第2引数として渡される設定です。
エディタが表示された後に変更することもできます。

使用可能な設定の一覧は[こちら](https://microsoft.github.io/monaco-editor/api/interfaces/monaco.editor.IStandaloneDiffEditorConstructionOptions.html)にあります。

## `<MonacoDiffEditor>`の`Ref`の使用
`ref` と `$editor` を用いることで、エディタのインスタンスに直接アクセスできます。
```vue
<template>
  <MonacoDiffEditor ref="editorRef" />
</template>

<script lang="ts" setup>
import { MonacoEditor } from '#build/components'
const editorRef = ref<InstanceType<typeof MonacoDiffEditor>>()

// あいさつアクションを追加するには...
editorRef.value?.$editor.addAction({
  id: 'hello-world',
  label: 'Hello world',
  run: function (ed) {
    alert('Hello world!')
  }
})
</script>
```
