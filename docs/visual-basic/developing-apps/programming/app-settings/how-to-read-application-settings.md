---
title: "How to: Read Application Settings in Visual Basic | Microsoft Docs"
ms.custom: ""
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "reading application settings"
  - "My.Settings object, reading application settings"
  - "application settings, reading"
ms.assetid: eb3428ef-115e-49a8-a878-e0613183fee0
caps.latest.revision: 12
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 12
---
# How to: Read Application Settings in Visual Basic
[!INCLUDE[vs2017banner](../../../../visual-basic/includes/vs2017banner.md)]

Vous pouvez lire un paramètre utilisateur en accédant à la propriété du paramètre de l'objet `My.Settings`.  
  
 L'objet `My.Settings` expose chaque paramètre comme une propriété.  Le nom de la propriété et celui du paramètre sont identiques, de même que le type de propriété et le type de paramètre.  La **Portée** du paramètre détermine si la propriété est en lecture seule : la propriété d'un paramètre de portée **Application** est en lecture seule, tandis que la propriété d'un paramètre de portée **Utilisateur** est en mode lecture\-écriture.  Pour plus d’informations, consultez [My.Settings Object](../../../../visual-basic/language-reference/objects/my-settings-object.md).  
  
## Exemple  
 Cet exemple affiche la valeur du paramètre `Nickname`.  
  
 [!code-vb[VbVbalrMyResources#14](../../../../visual-basic/developing-apps/programming/app-settings/codesnippet/visualbasic/VbVbalrMyResources2/Form1.vb#14)]  
  
 Pour que cet exemple fonctionne, votre application doit avoir un paramètre `Nickname` de type `String`.  Pour plus d’informations, consultez [Gestion des paramètres d'une application \(.NET\)](/visual-studio/ide/managing-application-settings-dotnet).  
  
## Voir aussi  
 [My.Settings Object](../../../../visual-basic/language-reference/objects/my-settings-object.md)   
 [How to: Change User Settings in Visual Basic](../../../../visual-basic/developing-apps/programming/app-settings/how-to-change-user-settings.md)   
 [How to: Persist User Settings in Visual Basic](../../../../visual-basic/developing-apps/programming/app-settings/how-to-persist-user-settings.md)   
 [How to: Create Property Grids for User Settings in Visual Basic](../../../../visual-basic/developing-apps/programming/app-settings/how-to-create-property-grids-for-user-settings.md)   
 [Gestion des paramètres d'une application \(.NET\)](/visual-studio/ide/managing-application-settings-dotnet)