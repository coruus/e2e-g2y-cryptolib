# Yahoo End-To-End

A fork of Google's [End-to-End](https://github.com/google/end-to-end) for Yahoo mail.

## Build instructions

### Install prerequisites

End-to-End depends on the following:
* bash
* git
* curl
* unzip
* ant
* JDK 1.7
* Python

On OSX with Homebrew:

    brew install ant git

Or, MacPorts:

    port install apache-ant git

### Build the extension

The extension requires a keyserver implementing [this API](docs/keyserver.md)
to fetch keys for other users.

We do not currently provide a publicly-exposed keyserver. So you'll need to run your own for now. (We will provide an open source vagrantfile or node package for this soon.)

Once that's done:

1. Edit `src/javascript/crypto/e2e/extension/manifest.json` and replace
   `https://keyshop.paranoids.corp.yahoo.com:25519` with the origin of your
   keyserver.
2. Edit `src/javascript/crypto/extension/config.js` with your keyserver
   parameters. Most likely you will want to set `AUTH_ENABLED` to false, in
   which case you can put anything for `AUTH_COOKIE` and `AUTH_DEFAULT_ORIGIN`.

Then to build the extension:

    ./do.sh build_extension_debug

## Installation instructions

Go to chrome://extensions, check the "developer mode" checkbox, click on "Load
unpacked extension" and selected `file:///path/to/this/repo/build/extension`.


## Development

We use Github's built-in issue tracker for tracking issues. The general
End-to-End mailing list is
[e2e-discuss](https://groups.google.com/forum/#!forum/e2e-discuss). Please put
[YAHOO] at the start of the subject line if your email is specifically about
this project.

We generally ask that you follow Google's [End-to-End Contributing
Guidelines](docs/CONTRIBUTING.md) for submitting to this repo.

## Docs

See [docs](docs) for current documentation.

## Acknowledgements

The committers would like to thank the following current and former Yahoo employees for their help with this project:
* Doug DePerry
* Juan Garay
* Marty Garvin
* Jackie Goldberg
* Christopher Harrell
* Stuart Larsen
* Jonathan Pierce
* Payman Mohassel
* Binu Ramakrishnan
* Chris Rolhf
* Markandey Singh
* Alex Stamos
* Regina Wallace-Jones
* Gil Yehuda
* Albert Yu

We would also like to thank the [folks at google](CONTRIBUTORS) for starting this project.

## Licensing

Code licensed under the Apache Version 2.0 license. See LICENSE file for terms.
