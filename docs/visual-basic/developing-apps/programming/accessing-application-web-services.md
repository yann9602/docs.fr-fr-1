---
title: "Accessing Application Web Services (Visual Basic) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "Web services, My.WebServices object"
  - "My.WebServices object"
  - "applications [Visual Basic], Web services"
ms.assetid: 8ad5405b-e771-42b1-82d3-ce97af2cea9e
caps.latest.revision: 12
caps.handback.revision: 12
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Accessing Application Web Services (Visual Basic)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

L'objet `My.WebServices` fournit une instance de chaque service Web référencé par le projet actuel.  Chaque instance est instanciée sur demande.  Vous pouvez accéder à ces services Web via les propriétés de l'objet `My.WebServices`.  La propriété porte le même nom que celui du service Web auquel la propriété accède.  Toute classe qui hérite de <xref:System.Web.Services.Protocols.SoapHttpClientProtocol> est un service Web.  
  
## Tâches  
 Le tableau suivant répertorie les moyens possibles pour accéder aux services Web référencées par une application.  
  
|||  
|-|-|  
|Pour|Consultez|  
|Appeler un service Web|[My.WebServices Object](../../../visual-basic/language-reference/objects/my-webservices-object.md)|  
|Appeler un service Web de façon asynchrone et gérer un événement lorsqu'il s'exécute|[How to: Call a Web Service Asynchronously](../../../visual-basic/developing-apps/programming/how-to-call-a-web-service-asynchronously.md)|  
  
## Voir aussi  
 [My.WebServices Object](../../../visual-basic/language-reference/objects/my-webservices-object.md)