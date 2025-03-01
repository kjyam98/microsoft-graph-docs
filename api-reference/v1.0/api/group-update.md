---
title: "Update group"
description: "Update the properties of a group object."
author: "Jordanndahl"
ms.localizationpriority: high
ms.prod: "groups"
doc_type: apiPageType
---

# Update group

Namespace: microsoft.graph

Update the properties of a group object.

## Permissions

One of the following permissions is required to call this API. To learn more, including how to choose permissions, see [Permissions](/graph/permissions-reference).

|Permission type      | Permissions (from least to most privileged)              |
|:--------------------|:---------------------------------------------------------|
|Delegated (work or school account) | Group.ReadWrite.All, Directory.ReadWrite.All, Directory.AccessAsUser.All  |
|Delegated (personal Microsoft account) | Not supported.    |
|Application | Group.ReadWrite.All, Directory.ReadWrite.All |

## HTTP request

<!-- { "blockType": "ignored" } -->

```http
PATCH /groups/{id}
```

## Request headers

| Name       | Type | Description|
|:-----------|:------|:----------|
| Authorization  | string  | Bearer {token}. Required. |

## Request body

In the request body, supply *only* the values for properties that should be updated. Existing properties that are not included in the request body will maintain their previous values or be recalculated based on changes to other property values.

The following table specifies the properties that can be updated.

| Property   | Type |Description|
|:---------------|:--------|:----------|
|allowExternalSenders|Boolean|Default is `false`. Indicates whether people external to the organization can send messages to the group.|
|autoSubscribeNewMembers|Boolean|Default is `false`. Indicates whether new members added to the group will be auto-subscribed to receive email notifications. **autoSubscribeNewMembers** can't be `true` when **subscriptionEnabled** is set to `false` on the group.|
|description|String|An optional description for the group. |
|displayName|String|The display name for the group. This property is required when a group is created and it cannot be cleared during updates. |
|mailNickname|String|The mail alias for the group. This property must be specified when a group is created. |
|preferredDataLocation|String|The preferred data location for the Microsoft 365 group. To update this property, the calling user must be assigned one of the following Azure AD roles: <br><ul><li> Global Administrator <li> User Account Administrator <li> Partner Tier1 or Tier2 Support <li>Directory Writer <li> Exchange Administrator <li> SharePoint Administrator </ul> <br/>For more information about this property, see  [OneDrive Online Multi-Geo](/sharepoint/dev/solution-guidance/multigeo-introduction).|
|securityEnabled|Boolean|Specifies whether the group is a security group. |
|visibility|String|Specifies the visibility of a Microsoft 365 group. The possible values are: **Private**, **Public**, or empty (which is interpreted as **Public**).|

> [!IMPORTANT]
>
> + To update the following properties, you must specify them in their own PATCH request, without including the other properties listed in the table above: **allowExternalSenders**, **autoSubscribeNewMembers**, **hideFromAddressLists**, **hideFromOutlookClients**, **isSubscribedByMail**, **unseenCount**.
>
> + Only a subset of the group API pertaining to core group administration and management support application and delegated permissions. All other members of the group API, including updating  **autoSubscribeNewMembers**, support only delegated permissions. See [known issues](/graph/known-issues#groups) for examples.
>
> + The rules for updating mail-enabled security groups in Microsoft Exchange Server can be complex; to learn more, see [Manage mail-enabled security groups in Exchange Server](/Exchange/recipients/mail-enabled-security-groups?view=exchserver-2019).

## Response

If successful, this method returns a `204 No Content` response code—except a `200 OK` response code when updating the following properties: **allowExternalSenders**, **autoSubscribeNewMembers**, **hideFromAddressLists**, **hideFromOutlookClients**, **isSubscribedByMail**, **unseenCount**.

## Example

The following example shows how to update a group.

### Request

The following is an example of the request.

# [HTTP](#tab/http)
<!-- {
  "blockType": "request",
  "name": "update_group"
}-->

```http
PATCH https://graph.microsoft.com/v1.0/groups/{id}
Content-type: application/json

{
  "description": "Library Assist",
  "displayName": "Library Assist",
  "groupTypes": [
    "Unified"
  ],
  "mailEnabled": true,
  "mailNickname": "library-help"
}
```
# [C#](#tab/csharp)
[!INCLUDE [sample-code](../includes/snippets/csharp/update-group-csharp-snippets.md)]
[!INCLUDE [sdk-documentation](../includes/snippets/snippets-sdk-documentation-link.md)]

# [JavaScript](#tab/javascript)
[!INCLUDE [sample-code](../includes/snippets/javascript/update-group-javascript-snippets.md)]
[!INCLUDE [sdk-documentation](../includes/snippets/snippets-sdk-documentation-link.md)]

# [Objective-C](#tab/objc)
[!INCLUDE [sample-code](../includes/snippets/objc/update-group-objc-snippets.md)]
[!INCLUDE [sdk-documentation](../includes/snippets/snippets-sdk-documentation-link.md)]

# [Java](#tab/java)
[!INCLUDE [sample-code](../includes/snippets/java/update-group-java-snippets.md)]
[!INCLUDE [sdk-documentation](../includes/snippets/snippets-sdk-documentation-link.md)]

---


### Response

The following is an example of the response.

<!-- {
  "blockType": "response"
} -->

```http
HTTP/1.1 204 No Content
```

<!-- uuid: 8fcb5dbc-d5aa-4681-8e31-b001d5168d79
2015-10-25 14:57:30 UTC -->
<!-- {
  "type": "#page.annotation",
  "description": "Update group",
  "keywords": "",
  "section": "documentation",
  "tocPath": "",
  "suppressions": [
  ]
}-->
