# receipt-generator

研究会向けの領収書 PDF を、JSON または参加者名簿から生成します。

## Setup

Python 3.10 以上と WeasyPrint を使用します。

### macOS

```bash
brew install weasyprint
python3 -m venv .venv
source .venv/bin/activate
python -m pip install -r requirements.txt
```

### Windows

1. [MSYS2](https://www.msys2.org/) をインストールします。
2. MSYS2 UCRT64 で次を実行します。

   ```bash
   pacman -S mingw-w64-ucrt-x86_64-pango
   ```

3. PowerShell で次を実行します。

   ```powershell
   py -m venv .venv
   .venv\Scripts\Activate.ps1
   python -m pip install -r requirements.txt
   ```

問題がある場合は [WeasyPrint 公式手順](https://doc.courtbouillon.org/weasyprint/stable/first_steps.html#windows) を確認してください。

## Usage

```bash
# JSON
python generate.py input/example.json

# CSV / XLSX
python generate.py input/sheet-example.json --dry-run
python generate.py input/sheet-example.json
```

PDF は `output/YYYYMMDDThhmmss/` に保存されます。`--dry-run` を付けると、PDF を作らず内容だけ確認できます。

## Input

入力方法を選び、リンク先の手順に従ってください。

- JSON から生成する：[`docs/json-input.md`](docs/json-input.md)
- CSV / XLSX から生成する：[`docs/spreadsheet.md`](docs/spreadsheet.md)
- Google Spreadsheet から生成する（Google Colab）：[`docs/colab.md`](docs/colab.md)

税区分と消費税額については [`docs/tax.md`](docs/tax.md) を参照してください。

## Test

```bash
python -m unittest discover -s tests
```
