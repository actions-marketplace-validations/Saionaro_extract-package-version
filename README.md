# extract-package-version

Allows you to get the npm version of the package in your Github Actions workflow

## Usage

### Inputs

- `path`: The directory where package.json can be found (defaults to root of repo)

### Outputs

- `version`: The version of current NPM package

### Example workflow - get NPM version

```yaml
on: push

name: Create Build

jobs:
  build:
    name: Create Build
    runs-on: ubuntu-latest
    steps:
      - name: Checkout code
        uses: actions/checkout@master

      - name: Extract version
        id: extract_version
        uses: Saionaro/extract-package-version@v1.2.1
      # From now you can access the version
      - name: Print version
        run: echo ${{ steps.extract_version.outputs.version }}
```

### Example workflow - get NPM version of subdirectory (useful in monorepos)

```yaml
on: push

name: Create Build

jobs:
  build:
    name: Create Build
    runs-on: ubuntu-latest
    steps:
      - name: Checkout code
        uses: actions/checkout@master

      - name: Extract version
        id: extract_version
        uses: Saionaro/extract-package-version@v1.2.1
        with:
          path: mysubdir
      # From now you can access the version
      - name: Print version
        run: echo ${{ steps.extract_version.outputs.version }}
```
