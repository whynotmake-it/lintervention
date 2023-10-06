# lintervention

[![melos][melos_badge]][melos_link]
[![lints by lintervention][badge]][repo_link]

Effective lint rules used internally by [whynotmake.it][website]. Based on [very_good_analysis](https://pub.dev/very_good_analysis), with some customizations, that make more sense for our workflows.

## Installation 💻

**❗ In order to start using Lintervention you must have the [Dart SDK][dart_install_link] installed on your machine.**

Install via `dart pub add`:

```sh
dart pub add dev:lintervention
```
or
```sh
flutter pub add dev:lintervention
```

Then, add an include in `analysis_options.yaml`:
```yaml
include: package:lintervention/analysis_options.yaml
```
if you want to always use the latest version. If not, constrain the version:
```yaml
include: package:lintervention/analysis_options.0.1.0.yaml
```

---

## Why the changes? 🤔

We love the rules from `very_good_analysis`, but we wanted to make some changes to make it more suitable for our workflows. Here are the changes we made:

- **No `prefer_single_quotes`**, since not all of our devs use US keyboard layouts, and it's not easier to type single quotes on most other layouts. Instead, we gain the benefit of never having to think about whether to use single or double quotes. We also don't have to worry about escaping quotes in strings.
- **Allow `one_member_abstracts`**, since sometimes we need to define interfaces in the domain layer that need to be implemented in the data layer. They should be allowed even with one member. Top level functions don't work for this usecase.
- We also exclude a bunch of generated file types from the lint rules.

---

## Use the badge

Show off your cool linting by using the badge in your readme:

```md
[![lints by lintervention](https://img.shields.io/badge/lints_by-lintervention-3A5A40)](https://github.com/whynotmake-it/lintervention)
```

---

[website]: https://whynotmake.it

[dart_install_link]: https://dart.dev/get-dart
[license_badge]: https://img.shields.io/badge/license-MIT-blue.svg
[license_link]: https://opensource.org/licenses/MIT

[melos_badge]: https://img.shields.io/badge/maintained%20with-melos-f700ff.svg?style=flat-square
[melos_link]: https://github.com/invertase/melos

[badge]: https://img.shields.io/badge/lints_by-lintervention-3A5A40
[repo_link]: https://github.com/whynotmake-it/lintervention