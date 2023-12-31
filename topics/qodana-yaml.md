[//]: # (title: Qodana.yaml)

Qodana runs can be customized with the `qodana.yaml` file stored under your project's root directory.
Note that configuration through `qodana.yaml` is only supported by the Qodana product.
It is not supported by any other JetBrains products like IDEA and PhpStorm.

## Set up profile

Set up a profile by the name:

```yaml
profile:
    name: %name%
```

Set up a profile by the path:

```yaml
profile:
    path: relative/path/in/your/project.xml
```

## Exclude paths

Exclude paths from the analysis scope for all inspections:

```yaml
exclude:
  - name: All
    paths:
      - asm-test/src/main/java/org
      - asm/Visitor.java
      - benchmarks
```

Exclude paths from the analysis scope for all inspections by ID:

```yaml
exclude:
  - name: Annotator
  - name: AnotherInspectionId
    paths:
      - relative/path
      - another/relative/path
  - name: All
    paths:
      - asm-test/src/main/java/org
      - asm
      - benchmarks
      - tools
```

## Fail threshold

Add fail threshold to use as quality gate:

```yaml
failThreshold: <number>
```

When this number of problems is reached, container would do `exit 255`. Can be used to make the CI step fail.

## Full example

```yaml
version: 1.0
failThreshold: 0
profile:
  name: qodana.recommended
exclude:
  - name: Annotator
  - name: AnotherInspectionId
    paths:
      - relative/path
      - another/relative/path
  - name: All
    paths:
      - asm-test/src/main/java/org
      - benchmarks
      - tools
```
