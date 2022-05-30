# Lint Factory

<picture>
  <source media="(prefers-color-scheme: dark)" srcset="https://raw.githubusercontent.com/innFactory/branding/main/styles/README/innfactory_logo_white.png">
  <img src="https://raw.githubusercontent.com/innFactory/branding/main/styles/README/innfactory_logo_black.png">
</picture>

Developed by [innFactory GmbH][innfactory_link] ⚙️

[![ci][ci_badge]][ci_badge_link]
[![pub package][pub_badge]][pub_badge_link]
[![License: MIT][license_badge]][license_badge_link]
[![style: lint factory][badge]][badge_link]

---

Flutter & Dart lint rules as well as [dart_code_metrics][dart_code_metrics_link] configuration used internally at [innFactory GmbH][innfactory_link].

**Note:** This package was heavily inspired by [very_good_analysis][very_good_analysis_link].

## Usage

To use the lints, add a dependency in your `pubspec.yaml`:

```yaml
# If you use `package:lint_factory/lint_factory.dart`, add a normal dependency.
dependencies:
  lint_factory: ^1.0.0

# Or, if you just want `lint_options.yaml`, it can be a dev dependency.
dev_dependencies:
  lint_factory: ^1.0.0
```

Then, add an include in `lint_options.yaml`:

```yaml
include: package:lint_factory/lint_options.yaml
```

This will ensure you always use the latest version of the lints. If you wish to restrict the lint version, specify a version of `lint_options.yaml` instead:

```yaml
include: package:lint_factory/lint_options.1.0.0.yaml
```

## Suppressing Lints

There may be cases where specific lint rules are undesirable. Lint rules can be suppressed at the line, file, or project level.

An example use case for suppressing lint rules at the file level is suppressing the `prefer_const_constructors` in order to achieve 100% code coverage. This is due to the fact that const constructors are executed before the tests are run, resulting in no coverage collection.

### Line Level

To suppress a specific lint rule for a specific line of code, use an `ignore` comment directly above the line:

```dart
// ignore: public_member_api_docs
class A {}
```

### File Level

To suppress a specific lint rule of a specific file, use an `ignore_for_file` comment at the top of the file:

```dart
// ignore_for_file: public_member_api_docs

class A {}

class B {}
```

### Project Level

To suppress a specific lint rule for an entire project, modify `lint_options.yaml`:

```yaml
include: package:lint_factory/lint_options.yaml
linter:
  rules:
    public_member_api_docs: false
```

## Badge

To indicate your project is using `lint_factory` → [![style: lint_factory][badge]][badge_link]

```md
[![style: lint_factory](https://img.shields.io/badge/style-lint__factory-e32028.svg)](https://pub.dev/packages/lint_factory)
```

[lint_options_yaml]: https://github.com/innFactory/lint_factory/blob/main/lint_options.yaml
[ci_badge]: https://github.com/innFactory/lint_factory/workflows/ci/badge.svg
[ci_badge_link]: https://github.com/innFactory/lint_factory/actions
[badge]: https://img.shields.io/badge/style-lint__factory-e32028.svg
[badge_link]: https://pub.dev/packages/lint_factory
[license_badge]: https://img.shields.io/badge/license-MIT-blue.svg
[license_badge_link]: https://opensource.org/licenses/MIT
[pub_badge]: https://img.shields.io/pub/v/lint_factory.svg
[pub_badge_link]: https://pub.dartlang.org/packages/lint_factory
[dart_code_metrics_link]: https://github.com/dart-code-checker/dart-code-metrics
[very_good_analysis_link]: https://github.com/VeryGoodOpenSource/very_good_analysis
[innfactory_link]: https://innfactory.de