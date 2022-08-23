# Tentacle package development

## Tentacle packages

This page covers tentacle package creation.

A tentacle package is a python module that contains one or multiple [tentacles](tentacle-development.md) of the same type.

### The tentacle package folder

A tentacle package is defined by a folder located at :

```bash
tentacles/YOUR_TP_CATEGORY/YOUR_TP_SUB_CATEGORY/YOUR_TENTACLE_PACKAGE_NAME/
```

{% hint style="info" %}
TP is for tentacle package
{% endhint %}

* **YOUR_TP_CATEGORY** can be Backtesting, Evaluator, Services or

  Trading

* **YOUR_TP_SUB_CATEGORY** should be a sub category of

  **YOUR_TP_CATEGORY** in the existing tentacle architecture

* **YOUR_TENTACLE_PACKAGE_NAME** is the name of your tentacle

  package, shouldn't use an existing tentacle package name

### Description file

A tentacle package contains metadata described in the metadata.json file. This file is used to properly install the tentacle and should be carefully written. It's located at the root path of the tentacle package :

```bash
tentacles/YOUR_TP_CATEGORY/YOUR_TP_SUB_CATEGORY/YOUR_TENTACLE_PACKAGE_NAME/metadata.json
```

A tentacle package metadata.json contains :

```javascript
{
  "version": "YOUR_TP_VERSION",
  "origin_package": "YOUR_TP_ORIGIN_PACKAGE",
  "tentacles": ["YOUR_TP_TENTACLE_1", "YOUR_TP_TENTACLE_2"],
  "tentacles-requirements": ["YOUR_TP_TP_REQUIREMENT_1", "YOUR_TP_TP_REQUIREMENT_2"]
}
```

* **YOUR_TP_VERSION** is your tentacle package version
* **YOUR_TP_ORIGIN_PACKAGE** is the author or the origin repository

  of the tentacle package

* **YOUR_TP_TENTACLE_1** and **YOUR_TP_TENTACLE_2** are name of the tentacle classes contained in your tentacle package tentacles (1 or more).

* **YOUR_TP_TP_REQUIREMENT_1** and

  **YOUR_TP_TP_REQUIREMENT_2** are the names of required tentacle

  packages to have installed to run your tentacle package (0

  or more)

{% hint style="info" %}
**YOUR_TP_TENTACLE_X** should match python classes to be exposed in the tentacle
{% endhint %}

Example _DailyTradingMode/metadata.json_ :

```javascript
{
  "version": "1.2.0",
  "origin_package": "OctoBot-Default-Tentacles",
  "tentacles": ["DailyTradingMode"],
  "tentacles-requirements": ["mixed_strategies_evaluator"]
}
```

### Tentacle modules

[Tentacle](tentacle-development.md) python modules should be placed at the root path of the tentacle package (1 or more).

Example with _momentum_evaluator_ : The main python module that contains multiple tentacles is located at

```bash
tentacles/Evaluator/TA/momentum_evaluator/momentum.py
```

Every tentacle classes should be imported in the package root `__init__.py` file.

Example with _momentum_evaluator_'s `__init__.py`.py :

```python
from .momentum import RSIMomentumEvaluator, ADXMomentumEvaluator, RSIWeightMomentumEvaluator, 
BBMomentumEvaluator, MACDMomentumEvaluator, KlingerOscillatorMomentumEvaluator, 
KlingerOscillatorReversalConfirmationMomentumEvaluator
```

### Config

A tentacle package can contain tentacle configurations. Configuration files are located in the _config/_ folder at :

```bash
tentacles/YOUR_TP_CATEGORY/YOUR_TP_SUB_CATEGORY/YOUR_TENTACLE_PACKAGE_NAME/config/
```

Each tentacles config file should be named with the exact case and name as the associated tentacle class. Below an example for _MyAwesomeTentacle_ :

```bash
tentacles/YOUR_TP_CATEGORY/YOUR_TP_SUB_CATEGORY/YOUR_TENTACLE_PACKAGE_NAME/config/MyAwesomeTentacle.json
```

On OctoBot's web interface, tentacle configuration settings are generated using the configuration and its assocaited json schema files using [json-editor](https://github.com/json-editor/json-editor) library. Below an example for _MyAwesomeTentacle_ configuration schema:

```bash
tentacles/YOUR_TP_CATEGORY/YOUR_TP_SUB_CATEGORY/YOUR_TENTACLE_PACKAGE_NAME/config/MyAwesomeTentacle_schema.json
```

{% hint style="info" %}
A tentacle configuration schema file has to be named as your tentacle configuration file with a **_schema** suffix.
{% endhint %}

### Resources

Tentacle resources are located in the **resources** folder of your tentacle package.

Each tentacles documentation should be created for in `resources/YOUR_TP_TENTACLE_1.md`, `resources/YOUR_TP_TENTACLE_2.md` (the file name should match the tentacle class name)

A tentacle package can also contain many resources that can be binary files, images...

Example _DailyTradingMode/resources/DailyTradingMode.md_ :

```text
DailyTradingMode is a **low risk versatile trading mode** that reacts only the its state changes to
a state that is different from the previous one and that is not NEUTRAL.

When triggered for a given symbol, it will cancel previously created (and unfilled) orders
and create new ones according to its new state.

DailyTradingMode will consider every compatible strategy and average their evaluation to create
each state.
```

{% hint style="info" %}
You can use [markdown](https://www.markdownguide.org/cheat-sheet) to format a tentacle documentation.
{% endhint %}

### Tests

Tentacle should be tested. Tests file are usually located in the **tests** folder of the tentacle package.

## Installing and sharing tentacles

Follow the [tentacles installation guide](../guides/customize-your-octobot.md#installing-tentacles) to install or share your custom tentacle package.

