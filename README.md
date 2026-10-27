# mbsh: study-material automation prototype

mbsh is a Python shell prototype for organizing study material from a MeuBernoulli account. Its mENEM utility implements a workflow for selecting questions, collecting question and solution images, and assembling them into a PDF.

## 1. Components

- Interactive shell with configuration and command history.
- Browser login and page interaction through pyppeteer.
- Question-selection logic using subject, answer correctness, and difficulty indicators.
- Image downloads with Requests and PDF assembly with Pillow.

## 2. Structure

`main.py` provides the entry points. `mbsh.py` contains the main shell and mENEM utility. `utils.py` holds shared prompts, output controls, and browser helpers. `docs.py` supplies command help, and `requirements.txt` lists the Python dependencies.

## 3. Entry point and workflow

Dependencies are listed in `requirements.txt`. The interactive entry point is:

```sh
python3 main.py --foreground
```

`--foreground` displays the browser. Startup initializes browser pages and runs configured startup commands; the defaults include login, so account credentials may be requested. Access requires an authorized account.

After login, the mENEM workflow defines three stages: `get_data`, `download_images`, and `gen_pdf`. Questions are collected before their solutions in the resulting page sequence. Consult built-in command help alongside the limitations below.

## 4. Limitations

- Platform navigation relies on page selectors and account access, not a stable public API.
- Command-file execution skips browser initialization. Batch command allowlists also exclude the mENEM workflow.
- Configuration can store plaintext credentials, and history records command arguments. Do not commit configuration/history files or put credentials in command arguments.
