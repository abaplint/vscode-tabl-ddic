# vscode-tabl-ddic
vscode tabl.ddic syntax highlighting

https://help.sap.com/doc/abapdocu_753_index_htm/7.53/en-US/abenddicddl_define_table.htm

## Development

Press `F5` to launch the extension host and open a `.tabl.ddic` file,
for example [examples/zdemo_syntax.tabl.ddic](examples/zdemo_syntax.tabl.ddic).

## Testing

```
npm install
npm test
```

Two layers, both running the grammar through the same TextMate engine as vscode:

* `npm run test:unit` checks scope assertions in `test/*.test.tabl.ddic`. Each
  assertion points at a range of the preceding line, and a leading `-` requires
  the scope to be absent:

  ```
  key mandt : abap.clnt not null;
//^^^ storage.modifier.key.abap.ddic
//                      ^^^^^^^^ storage.modifier.not-null.abap.ddic
  ```

* `npm run test:snapshot` compares the full tokenization of the files in
  `examples/` against the committed `.snap` files. After an intentional grammar
  change, review the reported diff and run `npm run test:snapshot:update` to
  accept it.
