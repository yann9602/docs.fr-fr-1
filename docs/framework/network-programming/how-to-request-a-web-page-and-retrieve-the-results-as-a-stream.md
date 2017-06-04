---
title: "Comment&#160;: demander une page web et r&#233;cup&#233;rer les r&#233;sultats sous forme de flux | Microsoft Docs"
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
ms.assetid: d32b7f35-29d8-4fb7-ad71-d219edc5e359
caps.latest.revision: 12
author: "mcleblanc"
ms.author: "markl"
manager: "markl"
caps.handback.revision: 12
---
# Comment&#160;: demander une page web et r&#233;cup&#233;rer les r&#233;sultats sous forme de flux
Cet exemple montre comment demander une page Web et récupérer les résultats dans un flux.  
  
## Exemple  
  
```csharp  
WebClient myClient = new WebClient();  
Stream response = myClient.OpenRead("http://www.contoso.com/index.htm");  
// The stream data is used here.  
response.Close();  
```  
  
```vb  
Dim myClient As WebClient = New WebClient()  
Dim response As Stream = myClient.OpenRead("http://www.contoso.com/index.htm")  
' The stream data is used here.  
response.Close()  
```  
  
## Compilation du code  
 Cet exemple nécessite :  
  
-   des références aux espaces de noms <xref:System.IO> et <xref:System.Net>.  
  
## Voir aussi  
 [Demande de données](../../../docs/framework/network-programming/requesting-data.md)