---
title: "Accessing User Data (Visual Basic) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "domain names, retrieving"
  - "data [Visual Basic], accessing user data"
  - "My.User object, tasks"
  - "user data, domain"
  - "user names, retrieving"
  - "user data, accessing"
  - "login names"
  - "examples [Visual Basic], accessing user data"
ms.assetid: 32492a15-ee59-4a63-a1f1-9b24cc13140a
caps.latest.revision: 17
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 17
---
# Accessing User Data (Visual Basic)
[!INCLUDE[vs2017banner](../../../visual-basic/includes/vs2017banner.md)]

Cette section contient des rubriques abordant l'objet `My.User` et les tâches qu'il vous permet d'accomplir.  
  
 L'objet `My.User` fournit l'accès aux informations sur l'utilisateur connecté en retournant un objet qui implémente l'interface <xref:System.Security.Principal.IPrincipal>.  
  
## Tâches  
  
|Pour|Consultez|  
|----------|---------------|  
|Obtenir le nom de connexion de l'utilisateur|<xref:Microsoft.VisualBasic.ApplicationServices.User.Name%2A>|  
|Obtenir le nom de domaine de l'utilisateur si l'application utilise l'authentification Windows|<xref:Microsoft.VisualBasic.ApplicationServices.User.CurrentPrincipal>|  
|Déterminer le rôle de l'utilisateur|<xref:Microsoft.VisualBasic.ApplicationServices.User.IsInRole%2A>|  
  
## Voir aussi  
 <xref:Microsoft.VisualBasic.ApplicationServices.User>