## Python

These settings apply only when `--python` is specified on the command line.
Please also specify `--python-sdks-folder=<path to the root directory of your azure-sdk-for-python clone>`.
Use `--python-mode=update` if you already have a setup.py and just want to update the code itself.

``` yaml $(python) && $(track2)
python-mode: create
azure-arm: true
license-header: MICROSOFT_MIT_NO_VERSION
namespace: azure.mgmt.policyinsights
package-name: azure-mgmt-policyinsights
package-version: 1.0.0b1
clear-output-folder: true
```

``` yaml $(python) && $(python-mode) == 'update' && $(track2)
no-namespace-folders: true
output-folder: $(python-sdks-folder)/policyinsights/azure-mgmt-policyinsights/azure/mgmt/policyinsights
```
``` yaml $(python) && $(python-mode) == 'create' && $(track2)
basic-setup-py: true
output-folder: $(python-sdks-folder)/policyinsights/azure-mgmt-policyinsights
```

``` yaml $(python) && $(track2)
modelerfour:
  lenient-model-deduplication: true
directive:
  - from: policyEvents.json
    where: $.parameters.fromParameter
    transform: $['x-ms-client-name'] = 'FromProperty'

  - from: policyStates.json
    where: $.parameters.fromParameter
    transform: $['x-ms-client-name'] = 'FromProperty'

  - from: policyStates.json
    where: $.paths
    transform: delete $["/{nextLink}"]

  - from: policyEvents.json
    where: $
    transform: >
      $["x-ms-paths"] = {
                            "{nextLink}?Next paging op for policy events": {
                              "post": {
                                "operationId": "PolicyEvents_NextLink",
                                "description": "Subsequent post calls to the next link",
                                "parameters": [
                                  {
                                    "$ref": "#/parameters/apiVersionParameter"
                                  },
                                  {
                                    "$ref": "#/parameters/skipTokenParameter"
                                  },
                                  {
                                    "name": "nextLink",
                                    "in": "path",
                                    "required": true,
                                    "type": "string",
                                    "description": "Next link for list operation.",
                                    "x-ms-skip-url-encoding": true
                                  }
                                ],
                                "responses": {
                                  "200": {
                                    "description": "Query results.",
                                    "schema": {
                                      "$ref": "#/definitions/PolicyEventsQueryResults"
                                    }
                                  },
                                  "default": {
                                    "description": "Error response describing why the operation failed.",
                                    "schema": {
                                      "$ref": "#/definitions/QueryFailure"
                                    }
                                  }
                                },
                                "x-ms-examples": {
                                  "Query latest at resource group level policy assignment scope with next link": {
                                    "$ref": "./examples/PolicyEvents_QueryManagementGroupScopeNextLinkSkipToken.json"
                                  }
                                }
                              }
                            }
                        };
```
