page_main_title: Hipchat
main_section: Platform
sub_section: Integrations
page_title: Hipchat integration
page_description: How to create and use a Hipchat Integration in Shippable

# Hipchat Key Integration

## Note

The **Hipchat Key** Integration is used to connect Shippable DevOps Assembly Lines platform so that you can send notifications to channels or rooms.

## Creating an Account Integration

* Sign in to your HipChat account using [this link to generate a token](https://www.hipchat.com/account/api).
    * Provide credentials to your HipChat account, if prompted.
* Create a token with `Send Message` and `Send Notification` scopes. Copy the token.
* To add your account integration, follow steps on the [Adding an account integration](/platform/tutorial/integration/howto-crud-integration/) page. Here is the information you need to create this integration:
    * **Integration type** -- **Hipchat**
    * **Name** -- choose a friendly name for the integration
    * **Token** -- HipChat account token

More about Hipchat tokens is explained in [Hipchat documentation](https://developer.atlassian.com/hipchat/guide/hipchat-rest-api/api-access-tokens).

## Usage

After you create the account integration, it can be used in the following scenarios:

### CI

* [Sending Hipchat notifications](/ci/hipchat-notifications/)

### Assembly Lines

The Hipchat integration can be used in the following [resources](/platform/workflow/resource/overview/):

* [integration](/platform/workflow/resource/integration)
* [notification](/platform/workflow/resource/notification)

## Default Environment Variables
When you create a resource with this integration, and use it as an `IN` or `OUT` for a `runSh` or `runCI` job, a set of environment variables is automatically made available that you can use in your scripts.

`<NAME>` is the the friendly name of the resource with all letters capitalized and all characters that are not letters, numbers or underscores removed. Any numbers at the beginning of the name are also removed to create a valid variable. For example, `my-key-1` will be converted to `MYKEY1`, and `my_key_1` will be converted to `MY_KEY_1`.

| Environment variable						| Description                         |
| ------------- 								|------------------------------------ |
| `<NAME>`\_INTEGRATION\_TOKEN			| The Token used to connect to HipChat |

## Shippable Utility Functions
The platform also provides a command line utility called [`shipctl`](/platform/tutorial/workflow/using-shipctl/) that can be used to retrieve the values of these environment variables.

The specific function that can be used in the jobs yml is: `shipctl get_integration_resource_field <resource name> <field name>`.

Here is a table that provides the mapping from the environment variable to the field name.

| Environment variable						| Field Name        |
| ------			 							|----------------- |
| `<NAME>`\_INTEGRATION\_TOKEN			| token |

More information on other utility functions is [documented here](/platform/tutorial/workflow/using-shipctl).

## Further Reading
* [Quick Start to CI](/getting-started/ci-sample)
* [RunSh Job](/platform/workflow/job/runsh)
* [Jobs](/platform/workflow/job/overview)
* [Resources](/platform/workflow/resource/overview)
