---
title: "How to: Change User Settings in Visual Basic | Microsoft Docs"
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
  - "user settings, changing in Visual Basic"
  - "user settings"
  - "My.Settings object, changing user settings"
  - "examples [Visual Basic], changing user settings"
ms.assetid: 41250181-c594-4854-9988-8183b9eb03cf
caps.latest.revision: 18
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 18
---
# How to: Change User Settings in Visual Basic
[!INCLUDE[vs2017banner](../../../../visual-basic/includes/vs2017banner.md)]

Vous pouvez modifier un paramètre utilisateur en assignant une nouvelle valeur à la propriété du paramètre de l'objet `My.Settings`.  
  
 L'objet `My.Settings` expose chaque paramètre comme une propriété.  Le nom de la propriété et celui du paramètre sont identiques, de même que le type de propriété et le type de paramètre.  La **Portée** du paramètre détermine si la propriété est en lecture seule : la propriété d'un paramètre de portée **Application** est en lecture seule, tandis que la propriété d'un paramètre de portée **Utilisateur** est en mode lecture\-écriture.  Pour plus d’informations, consultez [My.Settings Object](../../../../visual-basic/language-reference/objects/my-settings-object.md).  
  
> [!NOTE]
>  Même si vous pouvez modifier et enregistrer les valeurs des paramètres de portée utilisateur au moment de l'exécution, les paramètres de portée application sont en lecture seule et ne peuvent pas être modifiés par programme.  Vous pouvez modifier des paramètres de portée application lors de la création de l'application, à l'aide du **Concepteur de projets** ou en modifiant le fichier de configuration de l'application.  Pour plus d’informations, consultez [Gestion des paramètres d'une application \(.NET\)](/visual-studio/ide/managing-application-settings-dotnet).  
  
## Exemple  
 Cet exemple modifie la valeur du paramètre utilisateur `Nickname`.  
  
 [!code-vb[VbVbalrMyResources#7](../../../../visual-basic/developing-apps/programming/app-settings/codesnippet/VisualBasic/how-to-change-user-settings_1.vb)]  
  
 Pour que cet exemple fonctionne, votre application doit avoir un paramètre utilisateur `Nickname` de type `String`.  
  
 L'application enregistre les paramètres utilisateur lorsqu'elle s'arrête.  Pour enregistrer les paramètres immédiatement, appelez la méthode `My.Settings.Save`.  Pour plus d’informations, consultez [How to: Persist User Settings in Visual Basic](../../../../visual-basic/developing-apps/programming/app-settings/how-to-persist-user-settings.md).  
  
## Voir aussi  
 [My.Settings Object](../../../../visual-basic/language-reference/objects/my-settings-object.md)   
 [How to: Read Application Settings in Visual Basic](../../../../visual-basic/developing-apps/programming/app-settings/how-to-read-application-settings.md)   
 [How to: Persist User Settings in Visual Basic](../../../../visual-basic/developing-apps/programming/app-settings/how-to-persist-user-settings.md)   
 [How to: Create Property Grids for User Settings in Visual Basic](../../../../visual-basic/developing-apps/programming/app-settings/how-to-create-property-grids-for-user-settings.md)   
 [Gestion des paramètres d'une application \(.NET\)](/visual-studio/ide/managing-application-settings-dotnet)