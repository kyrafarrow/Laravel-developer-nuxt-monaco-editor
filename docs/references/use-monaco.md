# useMonaco
Get `monaco` namespace, the same as to do `import * as monaco from 'monaco-editor'`.

This composable can run everywhere you want, but if called on:
- Client-side: Returns `monaco` namespace after loaded.
- Server-side: Returns `null`

If you want to import types or interfaces from monaco-editor, you should do type-only import. For example:
```ts
import type { ISelection } from 'monaco-editor'
```

## Example
```ts
const monaco = useMonaco()!
const editorEl = ref<HTMLDivElement>()
monaco.editor.create(editorEl.value, { language: 'typescript' })
```
