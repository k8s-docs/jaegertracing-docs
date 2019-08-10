[![Build Status][ci-img]][ci]
[![Netlify Status][netifly-img]][netifly]

# Jaeger website

This repo houses all the assets used to build the Jaeger website, available at https://jaegertracing.io.

The site is built with [Hugo](https://gohugo.io/) and hosted by [Netlify](https://www.netlify.com/).

## Setup

Install the "extended" Hugo binary from [hugo/releases](https://github.com/gohugoio/hugo/releases) (use one of the `hugo_extended_*` binaries) or
use a package manager if it is available for your operating system.

>  The "extended" version of Hugo supports [Sass](https://sass-lang.org), which is necessary to build the site locally.

The currently used version of Hugo is defined in the [`netlify.toml`](./netlify.toml) configuration file.

## Running the site locally

If you want to develop the site locally, you can run a single command (assuming that you've run the [setup](#setup)):

```bash
$ make develop
```

This will start up a local server on localhost port 1313. When you make changes to either the content of the website (in [`content`](content)) *or* to the Sass and JavaScript assets of the page (in [`themes/jaeger-docs/assets`](themes/jaeger-docs/assets)), the browser will automatically update to reflect those changes (usually in under one second).

## Publishing the site

The site is published automatically by [Netlify](https://www.netlify.com/) whenever changes are merged to the `master` branch. The site cannot be published in an ad-hoc way (e.g. through a `make` command or script in the repo).

## Contributing to the site

We strongly encourage you to contribute to this site! For more information, see the [contributing](CONTRIBUTING.md) guide.

## Diagrams

Diagrams included in the documentation are created in the shared [Google Slides document][slides], which supports export to SVG. If you need to make changes to the diagrams as part of a PR, please copy the diagram into a new slide deck and include a shared link to it in the PR along with the exported SVG file. The maintainers will update the master deck with the new version upon merging the PR.

## Publishing new Jaeger version

Each Jaeger version is documented in a separate directory e.g. [content/docs/1.8/](./content/docs/1.8/). A special directory [content/docs/next-release/](./content/docs/next-release/) is reserved for the changes to be published as the next version. If you are adding documentation for features that are not yet released in the main Jaeger repository, add your changes to the `next-release` directory. If you're adding documentation for already released features, you may need to make the same change twice, i.e. in the most recent release (e.g. `1.8`) and in the `next-release` directories.

Before creating a new release:

  - Make sure all outstanding PRs for that version are merged to `next-release` directory.
  - Make sure the actual Jaeger release is done and Docker images for the new version are published.
  - If there are new Jaeger binaries or new storage options added to the release, make sure the CLI docs config file `data/cli/next-release/config.json` is updated accordingly (see below).

Then create a release by pushing a tag `release-X.Y.Z`, e.g.

```shell
git tag release-1.12.0
git push origin release-1.12.0
```

TODO: shouldn't the tag only specify major/minor, not patch? I don't think the process will work twice for the same major.minor

### Auto-generated documentation for CLI flags

The docs for the Jaeger CLI tools are generated by the automated release process described above using the Python script [`travis/gen-cli-data.py`](./travis/gen-cli-data.py). It uses the configuration file `data/cli/next-release/config.json` (automatically copied to `data/cli/${NEXT_VERSION}/config.json`) that describes which Jaeger binaries to include in the documentation, and which storage options each binary supports. The script invokes the `docs` command on the respective Docker images for each  binary and creates a set of YAML files under `data/cli/${NEXT_VERSION}/`, which are then used by the template engine to render the CLI docs.

## Admonitions

There are five admonition types available for the Jaeger docs:

Admonition type | Color
:---------------|:-----
`info` | blue
`success` | green
`danger` | red
`warning` | yellow
`requirement` | purple

Here's an example:

```markdown
{{< danger >}}
We do not recommend that you do this!
{{< /danger >}}
```

You can also add titles:

```markdown
{{< success title="New feature" >}}
Jaeger now supports a new thing that you definitely want.
{{< /success >}}
```

## License

[Apache 2.0 License](./LICENSE).

[slides]: https://docs.google.com/presentation/d/1JuurkQn03z0BbOEAViJBEE_WWMj6JQUML-uJm7zizvI/
[ci-img]: https://travis-ci.org/jaegertracing/documentation.svg?branch=master
[ci]: https://travis-ci.org/jaegertracing/documentation
[netifly-img]: https://api.netlify.com/api/v1/badges/d2b1a1ea-f454-4ba8-990c-cc469c959556/deploy-status
[netifly]: https://app.netlify.com/sites/jaegertracing/deploys
