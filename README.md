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
# If you are working on your own app
include: package:lintervention/app.yaml

# Or, if you are working on a public package that you intend to publish
include: package:lintervention/package.yaml
```

---

## Which rules should I use?

Lintervention comes with two sets of rules:

- `app.yaml` - for your Flutter and Dart applications
- `package.yaml` - for public Dart packages that you intend to publish

The main differences are that `app.yaml` disables some rules that are more suited for public code that can be consumed by anyone.

See the next section for more details on the differences.

## Why the changes? 🤔

We love the rules from `very_good_analysis`, but we wanted to make some changes to make it more suitable for our workflows. Here are the changes we made:

### Both `app.yaml` and `package.yaml`
- **No `prefer_single_quotes`**, since not all of our devs use US keyboard layouts, and it's not easier to type single quotes on most other layouts. Instead, we gain the benefit of never having to think about whether to use single or double quotes. We also don't have to worry about escaping quotes in strings.
- **Allow `one_member_abstracts`**, since sometimes we need to define interfaces in the domain layer that need to be implemented in the data layer. They should be allowed even with one member. Top level functions don't work for this usecase.
- **No `unnecessary_await_in_return`** since it can mess with error catching if not used carefully (see [this issue](https://github.com/dart-lang/linter/issues/2357))
- **No `prefer_int_literals`** since it will lead to you constantly fighting type inference when ommittin variable types (which we prefer).

### `app.yaml` only
- **No const lints** like `flutter_lint`, we decided to remove most of them since their real-world benefit is probably minimal in most cases, and they can lead to unnecessary code changes. See [this discussion](https://github.com/dart-lang/core/issues/833) if you want to learn more.
- **No `public_member_api_docs`** since you should decide yourself which parts of your app need documentation. We don't think it's necessary to document every public member in an app where the code is only consumed by you and your team.

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
