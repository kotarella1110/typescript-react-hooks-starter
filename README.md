<h1 align="center">TypeScript React Hooks Starter</h1>

<h3 align="center">React Hooks template for building with TypeScript</p>

<p align="center">
  <a href="LICENSE">
    <img alt="License" src="https://img.shields.io/badge/License-MIT-blue.svg?style=flat-square">
  </a>
  <a href="https://github.com/kotarella1110/typescript-react-hooks-starter/actions?query=workflow%3ACI">
    <img alt="Actions Status" src="https://github.com/kotarella1110/typescript-react-hooks-starter/workflows/CI/badge.svg">
  </a>
  <a href="https://github.com/semantic-release/semantic-release">
    <img alt="Semantic Release" src="https://img.shields.io/badge/%F0%9F%93%A6%F0%9F%9A%80-semantic--release-e10079.svg?style=flat-square">
  </a>
  <a href="http://commitizen.github.io/cz-cli/">
    <img alt="Commitizen friendly" src="https://img.shields.io/badge/commitizen-friendly-brightgreen.svg?style=flat-square">
  </a>
  <a href="#contributors-">
    <img alt="All Contributors" src="https://img.shields.io/badge/all_contributors-1-orange.svg?style=flat-square">
  </a>
  <a href="CONTRIBUTING.md">
    <img alt="PRs Welcome" src="https://img.shields.io/badge/PRs-welcome-green.svg?style=flat-square">
  </a>
</p>

## Want to publish your Custom Hook to npm?

### 1. Set a secret in an environment variable

The authentication token/credentials have to be made available in the CI service via environment variables. For more information, see "[Authentication for plugins](https://semantic-release.gitbook.io/semantic-release/usage/ci-configuration#authentication-for-plugins)".

### 2. Create Release workflow

```yml
# .github/workflows/release.yml
name: Release
on:
  push:
    branches:
      - "[0-9]+.x"
      - "[0-9]+.[0-9]+.x"
      - master
      - next
      - next-major
      - beta
      - alpha
jobs:
  release:
    runs-on: ubuntu-latest
    steps:
      - name: Checkout
        uses: actions/checkout@v2
      - name: Setup Node.js
        uses: actions/setup-node@v1
        with:
          node-version: 12.x
      - name: Install dependencies
        run: npm ci
      - name: Lint
        run: |
          npm run lint:types
          npm run lint
      - name: Test
        run: npm test
        env:
          CI: true
      - name: Build
        run: npm run build
      - name: Release
        run: npm run release
        env:
          GITHUB_TOKEN: ${{ secrets.GITHUB_TOKEN }}
          NPM_TOKEN: ${{ secrets.NPM_TOKEN }}
```

### 3. Push a new commit to a `master` branch

```bash
npm run cz
git push origin master
```

## Contributing

Contributions are always welcome! Please read the [contributing](./CONTRIBUTING.md) first.

## Contributors

Thanks goes to these wonderful people ([emoji key](https://allcontributors.org/docs/en/emoji-key)):

<!-- ALL-CONTRIBUTORS-LIST:START - Do not remove or modify this section -->
<!-- prettier-ignore-start -->
<!-- markdownlint-disable -->
<table>
  <tr>
    <td align="center"><a href="https://qiita.com/kotarella1110"><img src="https://avatars1.githubusercontent.com/u/12913947?v=4" width="100px;" alt=""/><br /><sub><b>Kotaro Sugawara</b></sub></a><br /><a href="https://github.com/kotarella1110/typescript-react-hooks-starter/commits?author=kotarella1110" title="Code">💻</a> <a href="https://github.com/kotarella1110/typescript-react-hooks-starter/commits?author=kotarella1110" title="Documentation">📖</a> <a href="#ideas-kotarella1110" title="Ideas, Planning, & Feedback">🤔</a> <a href="#infra-kotarella1110" title="Infrastructure (Hosting, Build-Tools, etc)">🚇</a> <a href="https://github.com/kotarella1110/typescript-react-hooks-starter/commits?author=kotarella1110" title="Tests">⚠️</a></td>
  </tr>
</table>

<!-- markdownlint-enable -->
<!-- prettier-ignore-end -->

<!-- ALL-CONTRIBUTORS-LIST:END -->

This project follows the [all-contributors](https://github.com/all-contributors/all-contributors) specification. Contributions of any kind welcome!

## License

[MIT](./LICENSE) © [Kotaro Sugawara](https://twitter.com/kotarella1110)
