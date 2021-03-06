---
title: "Count Documents (Azure Search Service REST API) | Microsoft Docs"
description: Return a count of total number of documents in an Azure Search index.
ms.date: "2016-11-09"
services: search
ms.service: search
ms.topic: "language-reference"
author: "Brjohnstmsft"
ms.author: "brjohnst"
ms.manager: cgronlun
translation.priority.mt:
  - "de-de"
  - "es-es"
  - "fr-fr"
  - "it-it"
  - "ja-jp"
  - "ko-kr"
  - "pt-br"
  - "ru-ru"
  - "zh-cn"
  - "zh-tw"
---
# Count Documents (Azure Search Service REST API)
  The **Count Documents** operation retrieves a count of the number of documents in a search index. The `$count` syntax is part of the OData protocol.  

```  
GET https://[service name].search.windows.net/indexes/[index name]/docs/$count?api-version=[api-version]  
Accept: text/plain   
api-key: [admin key]  
```  

## Request  
 HTTPS is required for service requests. The **Count Documents** request can be constructed using the GET method.  

 The `[index name]` in the request URI tells the service to return a count of all items in the docs collection of the specified index.  

 The `api-version` parameter is required. See [API versions in Azure Search](https://docs.microsoft.com/azure/search/search-api-versions) for a list of available versions.  

### Request Headers  
 The following table describes the required and optional request headers.  

|Request Header|Description|  
|--------------------|-----------------|  
|*Accept:*|This value must be set to text/plain.|  
|*api-key:*|The `api-key` is used to authenticate the request to your Search service. It is a string value, unique to your service URL. The **Count Documents** request can specify either an admin key or query key for the `api-key`.|  

 You will also need the service name to construct the request URL. You can get the service name and `api-key` from your service dashboard in the Azure classic portal. See [Create an Azure Search service in the portal](https://azure.microsoft.com/documentation/articles/search-create-service-portal/) for page navigation help.  

### Request Body  
 None.  

## Response  
 Status Code: 200 OK is returned for a successful response.  

 The response body contains the count value as an integer formatted in plain text.  

## See also  
 [Azure Search Service REST](index.md)   
 [HTTP status codes &#40;Azure Search&#41;](http-status-codes.md)   
 [OData Expression Syntax for Azure Search](odata-expression-syntax-for-azure-search.md)   
 [API versions in Azure Search](https://docs.microsoft.com/azure/search/search-api-versions)  
