## Python

These settings apply only when `--python` is specified on the command line.
Please also specify `--python-sdks-folder=<path to the root directory of your azure-sdk-for-python clone>`.
Use `--python-mode=update` if you already have a setup.py and just want to update the code itself.
These settings apply only when `--track2` is specified on the command line.

``` yaml $(track2)
azure-arm: true
license-header: MICROSOFT_MIT_NO_VERSION
package-name: azure-mgmt-rdbms
package-version: 1.0.0b1
no-namespace-folders: true
```

### Python multi-api

Generate all API versions currently shipped for this package

```yaml $(track2)
clear-output-folder: true
batch:
  - tag: package-flexibleserver-2021-06
  - tag: package-flexibleserver-2021-06-preview
  - tag: package-flexibleservers-2020-11-05-preview
  - tag: package-flexibleservers-2021-03-31-privatepreview
  - multiapiscript-flexibleservers: true
  - tag: package-postgresql-2020-01-01
  - multiapiscript-postgresql: true
```

```yaml $(multiapiscript-flexibleservers)
package-name: azure-mgmt-rdbms#postgresql_flexibleservers
multiapiscript: true
output-folder: $(python-sdks-folder)/rdbms/azure-mgmt-rdbms/azure/mgmt/rdbms/postgresql_flexibleservers
clear-output-folder: false
perform-load: false
```

```yaml $(multiapiscript-postgresql)
package-name: azure-mgmt-rdbms#postgresql
multiapiscript: true
output-folder: $(python-sdks-folder)/rdbms/azure-mgmt-rdbms/azure/mgmt/rdbms/postgresql
clear-output-folder: false
perform-load: false
```

### Tag: package-flexibleserver-2021-06 and python

These settings apply only when `--tag=package-flexibleserver-2021-06 --python` is specified on the command line.
Please also specify `--python-sdks-folder=<path to the root directory of your azure-sdk-for-python clone>`.

``` yaml $(tag) == 'package-flexibleserver-2021-06' && $(python)
namespace: azure.mgmt.rdbms.postgresql_flexibleservers.v2021_06_01
output-folder: $(python-sdks-folder)/rdbms/azure-mgmt-rdbms/azure/mgmt/rdbms/postgresql_flexibleservers/v2021_06_01
```

### Tag: package-flexibleserver-2021-06-preview and python

These settings apply only when `--tag=package-flexibleserver-2021-06 --python` is specified on the command line.
Please also specify `--python-sdks-folder=<path to the root directory of your azure-sdk-for-python clone>`.

``` yaml $(tag) == 'package-flexibleserver-2021-06-preview' && $(python)
namespace: azure.mgmt.rdbms.postgresql_flexibleservers
output-folder: $(python-sdks-folder)/rdbms/azure-mgmt-rdbms/azure/mgmt/rdbms/postgresql_flexibleservers
```

### Tag: package-flexibleservers-2021-03-31-privatepreview and python

These settings apply only when `--tag=package-flexibleservers-2021-03-31-privatepreview --python` is specified on the command line.
Please also specify `--python-sdks-folder=<path to the root directory of your azure-sdk-for-python clone>`.

``` yaml $(tag) == 'package-flexibleservers-2021-03-31-privatepreview' && $(python)
namespace: azure.mgmt.rdbms.postgresql_flexibleservers
output-folder: $(python-sdks-folder)/rdbms/azure-mgmt-rdbms/azure/mgmt/rdbms/postgresql_flexibleservers
```

### Tag: package-postgresql-2020-01-01 and python

These settings apply only when `--tag=package-postgresql-2020-01-01 --python` is specified on the command line.
Please also specify `--python-sdks-folder=<path to the root directory of your azure-sdk-for-python clone>`.

``` yaml $(tag) == 'package-postgresql-2020-01-01' && $(python)
namespace: azure.mgmt.rdbms.postgresql
output-folder: $(python-sdks-folder)/rdbms/azure-mgmt-rdbms/azure/mgmt/rdbms/postgresql
```

### Tag: package-flexibleservers-2020-11-05-preview and python

These settings apply only when `--tag=package-flexibleservers-2020-11-05-preview --python` is specified on the command line.
Please also specify `--python-sdks-folder=<path to the root directory of your azure-sdk-for-python clone>`.

``` yaml $(tag) == 'package-flexibleservers-2020-11-05-preview' && $(python)
namespace: azure.mgmt.rdbms.postgresql_flexibleservers
output-folder: $(python-sdks-folder)/rdbms/azure-mgmt-rdbms/azure/mgmt/rdbms/postgresql_flexibleservers
```
