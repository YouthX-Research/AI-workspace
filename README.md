# GençTek AI Workspace

A starting point for training a model that spots security vulnerabilities in Python code. It holds a small labeled dataset, the prompt used to generate it and a one-page site that explains the project. It was made during the GençTek program in Kahramanmaraş.

*Python kodundaki güvenlik açıklarını tespit edecek bir model için başlangıç çalışması: etiketli küçük bir veri seti, onu üreten prompt ve projeyi anlatan bir web sayfası. GençTek programı sırasında hazırlandı.*

## Status

This is the data stage. There is no trained model in this repository yet.

## Dataset

[`dataset.json`](dataset.json) has 30 Python snippets: 15 vulnerable and 15 safe. The vulnerable ones cover five types, three snippets each:

- SQL Injection
- Cross-Site Scripting (XSS)
- Command Injection
- Path Traversal
- Insecure Deserialization

Each entry looks like this:

| Field | Meaning |
| --- | --- |
| `id` | Unique ID, for example `SQLI_001` |
| `code_language` | Always `Python` for now |
| `code_snippet` | The code |
| `is_vulnerable` | `true` or `false` |
| `vulnerability_type` | Empty for safe snippets |
| `description` | Why the code is or isn't vulnerable |
| `remediation_suggestion` | How to fix it |
| `source` | Reference, such as an OWASP page or CVE |

The snippets were generated with an LLM using the template in [`Prompt.md`](Prompt.md) (in Turkish). Treat them as teaching examples, not as a benchmark.

## Website

`index.html`, `styles.css` and `script.js` make a static page that explains the idea. Serve the folder and open it in a browser:

```sh
python3 -m http.server 8000
```

## Next steps

- Grow the dataset past a few hundred examples and check each label by hand.
- Train and evaluate a first classifier.

Pull requests that add reviewed examples are welcome. See the organization's [contributing guide](https://github.com/YouthX-Research/.github/blob/main/CONTRIBUTING.md).

## License

[GPL-3.0](LICENSE). Part of [YouthX Research](https://github.com/YouthX-Research).
