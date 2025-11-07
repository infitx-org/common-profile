# Common Profile

This profile enables the deployment of a Mojaloop switch
and automated onboarding of payment managers.

## Usage

1. Add it to `submodules.yaml`:

    ```yaml
    profiles/common:
        url: https://github.com/infitx-org/common-profile.git
        ref: main # replace this with a tag for production use
    ```

1. Configure `custom-config/cluster-config.yaml`:

    ```yaml
    currency: XTS # the currency code for the switch deployment
    switch: xts # the switch name to be used in domain names
    ```

1. Enable the needed test payment managers in `custom-config/pm4ml-vars.yaml`:

   ⚠️ **IMPORTANT**

   This can only be done only before the initial deployment,
   otherwise the payment managers need to be manually added to Keycloak.

   ```yaml
   pm4mls:
       test-${switch}-dfsp1:
           currency: ${currency} # this line enables the PM
       test-${switch}-dfsp2:
           currency: ${currency} # this line enables the PM
       perf-${switch}-dfsp1:
           currency: ${currency} # this line enables the PM
       perf-${switch}-dfsp2:
           currency: ${currency} # this line enables the PM
   ```
