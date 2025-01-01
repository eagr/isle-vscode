We prefer using YAML rather than JSON to specify the grammar for readability.
Unfortunately, VS Code only supports the JSON format, so we need to convert YAML to JSON for it to be effective.
We use [js-yaml](https://github.com/nodeca/js-yaml) for that purpose.

```sh
brew install fswatch
npm i
```

```sh
# or use whatever working for you
fswatch ./syntaxes/*.yaml | while read -r changed; do
	filename=$(basename "${changed%.*}")
	npx js-yaml "./syntaxes/$filename.yaml" > "./syntaxes/$filename.json"
done
```
