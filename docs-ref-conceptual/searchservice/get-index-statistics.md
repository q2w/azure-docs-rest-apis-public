---
title: "Get Index Statistics (Azure Search Service REST API) | Microsoft Docs"
description: Return documents counts, index counts, and resource usage metrics for an Azure Search service.
ms.date: "04/20/2018"
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
# Get Index Statistics (Azure Search Service REST API)
  The **Get Index Statistics** operation returns from Azure Search a document count for the current index, plus storage usage. You can also get this information from the portal.  

```  
GET https://[service name].search.windows.net/indexes/[index name]/stats?api-version=[api-version]  
api-key: [admin key]  

```  
 > [!NOTE] 
 > Statistics on document count and storage size are collected every few minutes, not in real time. Therefore, the statistics returned by this API may not reflect changes caused by recent indexing operations.


## Request  
 HTTPS is required for all services requests. The **Get Index Statistics** request can be constructed using the GET method.  

 The `[index name]` in the request URI tells the service to return index statistics for the specified index.  

 The `api-version` parameter is required. The current version is `api-version=2017-11-11`. See [API versions in Azure Search](https://docs.microsoft.com/azure/search/search-api-versions) for a list of available versions.  

### Request Headers  
 The following table describes the required and optional request headers.  

|Request Header|Description|  
|--------------------|-----------------|  
|*api-key:*|The `api-key` is used to authenticate the request to your Search service. It is a string value, unique to your service. The **Get Index Statistics** request must include an `api-key` set to an admin key (as opposed to a query key).|  

 You will also need the service name to construct the request URL. You can get the service name and `api-key` from your service dashboard in the Azure Preview Portal. See [Create an Azure Search service in the portal](https://azure.microsoft.com/documentation/articles/search-create-service-portal/) for page navigation help.  

### Request Body  
 None.  

## Response  
 Status Code: "200 OK" is returned for a successful response.The response body is in the following format:  

```  
{  
  "documentCount": number,  
  "storageSize": number (size of the index in bytes)  
}  
```  

## See also  
 [Azure Search Service REST](index.md)   
 [API versions in Azure Search](https://docs.microsoft.com/azure/search/search-api-versions)
