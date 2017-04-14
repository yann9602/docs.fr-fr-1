---
title: "Comment&#160;: inscrire un protocole personnalis&#233; &#224; l’aide de WebRequest | Microsoft Docs"
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
ms.assetid: 98ddbdb9-66b1-4080-92ad-51f5c447fcf8
caps.latest.revision: 11
author: "mcleblanc"
ms.author: "markl"
manager: "markl"
caps.handback.revision: 11
---
# Comment&#160;: inscrire un protocole personnalis&#233; &#224; l’aide de WebRequest
Cet exemple montre comment inscrire un protocole le classthat quespécifique est défini ailleurs.  Dans cet exemple, `CustomWebRequestCreator` est l'objet par l'implémentation qui implémente la méthode de **Créer** qui retourne l'objet d' `CustomWebRequest` .  L'exemple de code suppose que vous avez écrit le code d' `CustomWebRequest` qui implémente le fournisseur personnalisé.  
  
## Exemple  
  
```csharp  
WebRequest.RegisterPrefix("custom", new CustomWebRequestCreator());  
WebRequest req = WebRequest.Create("custom://customHost.contoso.com/");  
```  
  
```vb  
WebRequest.RegisterPrefix("custom", New CustomWebRequestCreator())  
Dim req As WebRequest = WebRequest.Create("custom://customHost.contoso.com/")  
```  
  
## Compilation du code  
 Cet exemple nécessite :  
  
 Références à l'espace de noms d' <xref:System.Net> .  
  
## Voir aussi  
 [Programmation de protocoles enfichables](../../../docs/framework/network-programming/programming-pluggable-protocols.md)