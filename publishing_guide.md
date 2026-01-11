# publishing_guide.md

## Step-by-Step Guide to Publish `LatexPDFSizeOptimizer` to PyPI

Follow these steps to make your package available via `pip install latex-pdf-size-optimizer`.

### 1. Prerequisites

You need a generic account on PyPI (Python Package Index).
- **Register**: Go to [https://pypi.org/account/register/](https://pypi.org/account/register/) and create an account.
- **Enable 2FA**: PyPI requires Two-Factor Authentication. Enable it in account settings.
- **Create API Token**:
    1. Go to "Account settings" > "API tokens".
    2. Click "Add API token".
    3. Scope: "Entire account" (for the first upload).
    4. **Copy the token**. You will need it later (username will be `__token__`).

### 2. Install Build Tools

Make sure you have `build` and `twine` installed in your environment.

```bash
pip install build twine
```

### 3. Prepare the Package

Ensure your `pyproject.toml` has the correct metadata (check `version`, `description`, `dependencies`).
*Important*: If you want to publish a new version later, you must increment the `version = "0.1.0"` in `pyproject.toml`.

### 4. Build the Distribution

Navigate to the `LatexPDFSizeOptimizer` directory (where `pyproject.toml` is) and run:

```bash
python -m build
```

This will create a `dist/` folder containing two files:
- A generic `.tar.gz` (Source Archive)
- A generic `.whl` (Wheel)

### 5. Upload to PyPI

Use `twine` to upload the files in `dist/` to PyPI.

```bash
twine upload dist/*
```

- **Username**: `__token__`
- **Password**: [Your API Token starting with `pypi-`]

### 6. Verify Installation

Once uploaded, you can install your package from anywhere:

```bash
pip install latex-pdf-size-optimizer
```

### 7. Automating Updates

For future updates:
1. Modify your code.
2. Bump the version in `pyproject.toml`.
3. Delete the old `dist/` folder.
4. Run `python -m build`.
5. Run `twine upload dist/*`.
