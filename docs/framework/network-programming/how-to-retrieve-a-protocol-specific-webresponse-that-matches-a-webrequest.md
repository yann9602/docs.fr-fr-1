---
title: "Comment&#160;: r&#233;cup&#233;rer une classe WebResponse sp&#233;cifique au protocole qui correspond &#224; une classe WebRequest | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
ms.assetid: d8c90785-f16b-42a5-8439-ed2f731b2ba8
caps.latest.revision: 8
author: "mcleblanc"
ms.author: "markl"
manager: "markl"
caps.handback.revision: 8
---
# Comment&#160;: r&#233;cup&#233;rer une classe WebResponse sp&#233;cifique au protocole qui correspond &#224; une classe WebRequest
Cet exemple montre comment récupérer un WebResponse spécifique au fournisseur qui correspond à un WebRequest.  
  
## Exemple  
  
```csharp  
WebRequest req = WebRequest.Create("http://www.contoso.com/");  
WebResponse resp = req.GetResponse();  
```  
  
```vb  
Dim req As WebRequest = WebRequest.Create("http://www.contoso.com")  
Dim resp As WebResponse = req.GetResponse()  
```  
  
## Compilation du code  
 Cet exemple nécessite :  
  
-   Références à l'espace de noms de **System.Net** .  
  
## Voir aussi  
 [Demande de données](../../../docs/framework/network-programming/requesting-data.md)