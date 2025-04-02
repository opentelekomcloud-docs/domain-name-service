:original_name: dns_usermanual_0051.html

.. _dns_usermanual_0051:

Creating Custom Policies
========================

You can create custom policies to supplement system-defined policies and implement more refined access control.

You can create custom policies in either of the following two ways:

-  Visual editor: Select cloud services, actions, resources, and request conditions without the need to know policy syntax.
-  JSON: Edit JSON policies from scratch or based on an existing policy.

The following describes how to create a custom policy that allows users to modify DNS zones in the visual editor and JSON view.

For details, see `Creating a Custom Policy <https://docs.otc.t-systems.com/usermanual/iam/iam_01_0016.html>`__. The following provides examples of common DNS custom policies.

Example Custom Policies
-----------------------

-  Example 1: Authorize users to create zones, add record sets, and view the zones and record sets.

   .. code-block::

      {
          "Version": "1.1",
          "Statement": [
              {
                  "Effect": "Allow",
                  "Action": [
                      "dns:zone:create",
                      "dns:recordset:create",
                      "dns:zone:list"
              "dns:recordset:list"
                  ]
              },
              {
                  "Effect": "Allow",
                  "Action": [
                      "vpc:*:get*,
                      "vpc:*:list*"
                  ]
              }
          ]
      }

-  Example 2: Disallow users to delete DNS resources.

   A deny policy must be used together with other policies. If the permissions assigned to a user contain both "Allow" and "Deny", the "Deny" permissions take precedence over the "Allow" permissions.

   The following method can be used if you need to assign permissions of the **DNS FullAccess** policy to a user but also forbid the user from deleting DNS resources. Create a custom policy to disallow resource deletion and assign both policies to the group the user belongs to. Then the user can perform all operations on DNS except deleting resources. The following is an example deny policy:

   .. code-block::

      {
            "Version": "1.1",
            "Statement": [
                  {
                "Effect": "Deny",
                        "Action": [
                              "dns:*:delete*"
                        ]
                  }
            ]
      }

-  Example 3: Defining permissions for multiple services in a policy

   A custom policy can contain actions of multiple services that are all of the global or project-level type. The following is a policy with multiple actions:

   .. code-block::

      {
          "Version": "1.1",
          "Statement": [
              {
                  "Effect": "Allow",
                  "Action": [
                      "dns:zone:update",
                      "dns:zone:list"
                  ]
              },
              {
                  "Effect": "Allow",
                  "Action": [
                      "vpc:subnets:create",
                      "vpc:vips:update"
                  ]
              }
          ]
      }
