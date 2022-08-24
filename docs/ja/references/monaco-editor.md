<script setup>
import Stackbiltz from '../../../../components/Stackbiltz.vue'
</script>

# &lt;MonacoEditor&gt;
`<input>` や `<textarea>`と同じように、エディタの表示には `<MonacoEditor>` が簡単に使えます。

<Stackbiltz src="nuxt-starter-dnwsbl?embed=1&file=app.vue&hideNavigation=1&view=preview" />

## 値の設定・取得
```vue
<template>
  <MonacoEditor v-model="value" />
</template>

<script lang="ts" setup>
const value = ref('')
</script>
```

## 代替表示
```vue
<template>
  <MonacoEditor>
    Loading...
  </MonacoEditor>
</template>
```
`<MonacoEditor>` の子要素がエディタの読み込み中に表示されます。

## プロパティ
### `lang`
- デフォルト値: `plaintext`

配色に用いるプログラミング言語です。`options.language` の値を上書きします。

使用可能な言語の一覧は[こちら](https://github.com/microsoft/monaco-editor/tree/main/src/basic-languages)にあります。

### `options`
- デフォルト値: `{}`

`monaco.editor.create`の第2引数として渡される設定です。
エディタが表示された後に変更することもできます。

使用可能な設定の一覧は[こちら](https://microsoft.github.io/monaco-editor/api/interfaces/monaco.editor.IStandaloneEditorConstructionOptions.html)にあります。

## `<MonacoEditor>`の`Ref`の使用
`ref` と `$editor` を用いることで、エディタのインスタンスに直接アクセスできます。
```vue
<template>
  <MonacoEditor ref="editorRef" />
</template>

<script lang="ts" setup>
import { MonacoEditor } from '#build/components'
const editorRef = ref<InstanceType<typeof MonacoEditor>>()

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
