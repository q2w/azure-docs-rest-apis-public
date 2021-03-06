---
title: "Get Share ACL"
ms.custom: na
ms.date: 2016-06-29
ms.prod: azure
ms.reviewer: na
ms.service: storage
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: reference
ms.assetid: 9316b0ba-e1a4-43f1-b991-e321fbaea7ab
caps.latest.revision: 7
author: tamram
manager: carolz
translation.priority.mt: 
  - de-de
  - es-es
  - fr-fr
  - it-it
  - ja-jp
  - ko-kr
  - pt-br
  - ru-ru
  - zh-cn
  - zh-tw
---
# Get Share ACL
**Get Share ACL** returns information about stored access policies specified on the share. For more information, see [Establishing a Stored Access Policy](Establishing-a-Stored-Access-Policy.md).  
  
## Request  
 The **Get Share ACL** request may be constructed as follows. HTTPS is recommended. Replace `myaccount` with the name of your storage account:  
  
|Method|Request URI|HTTP Version|  
|------------|-----------------|------------------|  
|GET/HEAD|`https://myaccount.file.core.windows.net/myshare?restype=share&comp=acl`|HTTP/1.1|  
  
### URI Parameters  
 The following additional parameters may be specified on the request URI.  
  
|Parameter|Description|  
|---------------|-----------------|  
|`timeout`|Optional. The `timeout` parameter is expressed in seconds. For more information, see [Setting Timeouts for File Service Operations](Setting-Timeouts-for-File-Service-Operations.md).|  
  
### Request Headers  
 The following table describes required and optional request headers.  
  
|Request Header|Description|  
|--------------------|-----------------|  
|`Authorization`|Required. Specifies the authentication scheme, account name, and signature. For more information, see [Authentication for the Azure Storage Services](http://msdn.microsoft.com/en-us/library/azure/dd179428.aspx).|  
|`Date or x-ms-date`|Required for all authenticated requests. Specifies the version of the operation to use for this request. This operation is available only in versions 2015-02-21 and later.<br /><br /> For more information, see [Versioning for the Azure Storage Services](https://msdn.microsoft.com/en-us/library/azure/dd894041.aspx).|  
|`x-ms-version`|Required for all authenticated requests. Specifies the version of the operation to use for this request. For more information, see [Versioning for the Azure Storage Services](http://msdn.microsoft.com/en-us/library/azure/dd894041.aspx).|  
  
### Request Body  
 None.  
  
## Response  
 The response includes an HTTP status code, a set of response headers, and a response body.  
  
### Status Code  
 A successful operation returns status code **200 (OK)**.  
  
 For information about status codes, see [Status and Error Codes](http://msdn.microsoft.com/en-us/library/azure/dd179382.aspx).  
  
### Response Headers  
 The response for this operation includes the following headers. The response may also include additional standard HTTP headers. All standard headers conform to the [HTTP/1.1 protocol specification](http://go.microsoft.com/fwlink/?linkid=150478).  
  
|Response header|Description|  
|---------------------|-----------------|  
|`ETag`|The ETag contains a value that you can use to perform operations conditionally, in quotes.|  
|`Last-Modified`|Any operation that modifies the share or its properties or metadata updates the last modified time. Operations on files do not affect the last modified time of the share.|  
|`x-ms-request-id`|This header uniquely identifies the request that was made and can be used for troubleshooting the request. For more information, see [Troubleshooting API Operations](http://msdn.microsoft.com/en-us/library/azure/dd573365.aspx).|  
|`x-ms-version`|Indicates the version of the Blob service used to execute the request. This header is returned for requests made against version 2009-09-19 and later.|  
|`Date`|A UTC date/time value generated by the service that indicates the time at which the response was initiated.|  
  
### Response Body  
 If a share-level access policy has been specified for the share, **Get Share ACL** returns the signed identifier and access policy in the response body.  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<SignedIdentifiers>  
  <SignedIdentifier>  
    <Id>unique-value</Id>  
    <AccessPolicy>  
      <Start>start-time</Start>  
      <Expiry>expiry-time</Expiry>  
      <Permission>abbreviated-permission-list</Permission>  
    </AccessPolicy>  
  </SignedIdentifier>  
</SignedIdentifiers>  
  
```  
  
### Sample Response  
  
```  
Response Status:  
HTTP/1.1 200 OK  
  
Response Headers:  
Transfer-Encoding: chunked  
Date: <date>  
ETag: "0x8CAFB82EFF70C46"  
Last-Modified: <date>  
x-ms-version: 2015-02-21  
Server: Windows-Azure-File/1.0 Microsoft-HTTPAPI/2.0  
  
<?xml version="1.0" encoding="utf-8"?>  
<SignedIdentifiers>  
  <SignedIdentifier>   
    <Id>MTIzNDU2Nzg5MDEyMzQ1Njc4OTAxMjM0NTY3ODkwMTI=</Id>  
    <AccessPolicy>  
      <Start>2015-07-01T08:49:37.0000000Z</Start>  
      <Expiry>2015-07-02T08:49:37.0000000Z</Expiry>  
      <Permission>rwd</Permission>  
    </AccessPolicy>  
  </SignedIdentifier>  
</SignedIdentifiers>  
  
```  
  
## Authorization  
 Only the account owner may call this operation.  
  
## Remarks  
 The Access policy of the share applies to all of its share snapshots also. An access policy cannot be set or retrieved for a share snapshot. If an attempt is made to retrieve an access policy, then the service returns status code 400 (InvalidQueryParameterValue). 
