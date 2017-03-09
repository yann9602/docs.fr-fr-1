---
title: "My.Request Object | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
f1_keywords: 
  - "My.MyWebExtension.Request"
  - "My.Request"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "My.Request object"
ms.assetid: 93d5f0e2-6b60-4a2c-8652-d90216f6ad10
caps.latest.revision: 9
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 9
---
# My.Request Object
[!INCLUDE[vs2017banner](../../../visual-basic/includes/vs2017banner.md)]

Obtient l'objet <xref:System.Web.HttpRequest> pour la page demandée.  
  
## Notes  
 L'objet `My.Request` contient des informations sur la demande HTTP actuelle.  
  
 L'objet `My.Request` n'est disponible que pour les applications ASP.NET.  
  
## Exemple  
 L'exemple suivant obtient la collection d'en\-têtes de l'objet `My.Request` et utilise l'objet `My.Response` pour l'écrire dans la page ASP.NET.  
  
 [!code-vb[VbVbalrMyWeb#1](../../../visual-basic/language-reference/objects/codesnippet/visualbasic/my-request-object_1.aspx)]  
  
## Voir aussi  
 <xref:System.Web.HttpRequest>   
 [My.Response Object](../../../visual-basic/language-reference/objects/my-response-object.md)