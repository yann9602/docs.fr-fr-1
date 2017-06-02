---
title: "Comment&#160;: convertir une classe WebRequest pour acc&#233;der &#224; des propri&#233;t&#233;s sp&#233;cifiques au protocole | Microsoft Docs"
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
ms.assetid: d9a8eae2-7454-46f9-b43b-c98477c5bcde
caps.latest.revision: 6
author: "mcleblanc"
ms.author: "markl"
manager: "markl"
caps.handback.revision: 6
---
# Comment&#160;: convertir une classe WebRequest pour acc&#233;der &#224; des propri&#233;t&#233;s sp&#233;cifiques au protocole
Cet exemple montre comment convertir le rôle d'un WebRequest afin de pouvoir les propriétés spécifiques au protocole d'accès.  
  
## Exemple  
  
```csharp  
HttpWebRequest httpreq =   
   (HttpWebRequest) WebRequest.Create("http://www.contoso.com/");  
```  
  
```vb  
Dim httpreq As HttpWebRequest = _  
   CType(WebRequest.Create("http://www.contoso.com/"), HttpWebRequest)  
```  
  
## Voir aussi  
 [Programmation de protocoles enfichables](../../../docs/framework/network-programming/programming-pluggable-protocols.md)