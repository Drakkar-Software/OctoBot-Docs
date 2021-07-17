Tentacle package development
============================

Intro
-----

This page covers tentacle package creation.

A tentacle package contains one or multiple
[tentacles](Tentacle-Development.html).

The tentacle package folder
---------------------------

A tentacle package is defined by a folder placed at :

``` bash
tentacles/YOUR_TP_CATEGORY/YOUR_TP_SUB_CATEGORY/YOUR_TENTACLE_PACKAGE_NAME/
```

{% hint style="note" %}
TP is for tentacle package
{% endhint %}

-   **YOUR_TP_CATEGORY** can be Backtesting, Evaluator, Services or
    Trading
-   **YOUR_TP_SUB_CATEGORY** should be a sub category of
    **YOUR_TP_CATEGORY** in the existing tentacle architecture
-   **YOUR_TENTACLE_PACKAGE_NAME** is the name of your tentacle
    package, shouldn't use an existing tentacle package name

Description file
----------------

A tentacle package contains metadata described in metadata.json file.
This file is used to properly install the tentacle and should be
carefully written. It's located at the root path of the tentacle
package :

``` bash
tentacles/YOUR_TP_CATEGORY/YOUR_TP_SUB_CATEGORY/YOUR_TENTACLE_PACKAGE_NAME/metadata.json
```

A tentacle package metadata.json contains :

``` json
{
  "version": "YOUR_TP_VERSION",
  "origin_package": "YOUR_TP_ORIGIN_PACKAGE",
  "tentacles": ["YOUR_TP_TENTACLE_1", "YOUR_TP_TENTACLE_2"],
  "tentacles-requirements": ["YOUR_TP_TP_REQUIREMENT_1", "YOUR_TP_TP_REQUIREMENT_2"]
}
```

-   **YOUR_TP_VERSION** is your tentacle package version
-   **YOUR_TP_ORIGIN_PACKAGE** is the author or the origin repository
    of the tentacle package
-   **YOUR_TP_TENTACLE_1** and **YOUR_TP_TENTACLE_2** are names of
    your tentacle package tentacles (can have 1 or more).
-   **YOUR_TP_TP_REQUIREMENT_1** and
    **YOUR_TP_TP_REQUIREMENT\_2** are the names of required tentacle
    packages to have installed to run your tentacle package (can have 0
    or more)

{% hint style="note" %}

**YOUR\_TP\_TENTACLE\_X** should match python classes to be exposed in
the tentacle
{% endhint %}

Example *DailyTradingMode/metadata.json* :

``` json
{
  "version": "1.2.0",
  "origin_package": "OctoBot-Default-Tentacles",
  "tentacles": ["DailyTradingMode"],
  "tentacles-requirements": ["mixed_strategies_evaluator"]
}
```

Tentacle modules
----------------

[Tentacle](Tentacle-Development.html) python modules should be placed at
the root path of the tentacle package (can be 1 or more).

Example with *momentum\_evaluator* : The main python module that
contains multiple tentacles is located at

``` bash
tentacles/Evaluator/TA/momentum_evaluator/momentum.py
```

Every tentacle classes should be imported in the root
**__init__.py** file.

Example with *momentum\_evaluator*'s \_\_init\_\_.py :

``` python
from .momentum import RSIMomentumEvaluator, ADXMomentumEvaluator, RSIWeightMomentumEvaluator, \
BBMomentumEvaluator, MACDMomentumEvaluator, KlingerOscillatorMomentumEvaluator, \
KlingerOscillatorReversalConfirmationMomentumEvaluator
```

Config
------

A tentacle package can contain tentacle config. Config files are located
in *config/* folder at :

``` bash
tentacles/YOUR_TP_CATEGORY/YOUR_TP_SUB_CATEGORY/YOUR_TENTACLE_PACKAGE_NAME/config/
```

Each tentacles config file should be named with the exact case and name
as the exposed tentacle class(es). Below an example for
*MyAwesomeTentacle* :

``` bash
tentacles/YOUR_TP_CATEGORY/YOUR_TP_SUB_CATEGORY/YOUR_TENTACLE_PACKAGE_NAME/config/MyAwesomeTentacle.json
```

Tentacle configuration interface are generated using configuration
schema files and the
[json-editor](https://github.com/json-editor/json-editor) library. Below
an example for *MyAwesomeTentacle* :

``` bash
tentacles/YOUR_TP_CATEGORY/YOUR_TP_SUB_CATEGORY/YOUR_TENTACLE_PACKAGE_NAME/config/MyAwesomeTentacle_schema.json
```

Resources
---------

Tentacle package resources are located in the [resources]{.title-ref}
folder of your tentacle package.

Tentacles guides can be created for each tentacle in
resources/YOUR\_TP\_TENTACLE\_1.md, resources/YOUR\_TP\_TENTACLE\_2.md
(the file name should match the tentacle class name)

A tentacle package can also contain many resources that can be binary
files, images\...

Example *DailyTradingMode/resources/DailyTradingMode.md* :

```
DailyTradingMode is a **low risk versatile trading mode** that reacts only the its state changes to
a state that is different from the previous one and that is not NEUTRAL.

When triggered for a given symbol, it will cancel previously created (and unfilled) orders
and create new ones according to its new state.

DailyTradingMode will consider every compatible strategy and average their evaluation to create
each state.
```

Tests
-----

Tentacle should be tested. Tests file are usually located in the
[tests]{.title-ref} folder of the tentacle package.

Installation
------------

Follow the [tentacles installation
guide](Customize-your-OctoBot.html#installing-tentacles) to install your
custom tentacle package.
