---
title: "How to: Persist User Settings in Visual Basic | Microsoft Docs"
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
  - "My.Settings object, persisting user settings"
  - "persistence, persisting user settings [Visual Basic]"
  - "user settings, persisting"
ms.assetid: 0e5e6415-b6e2-4602-9be0-a65fa167d007
caps.latest.revision: 15
caps.handback.revision: 15
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# How to: Persist User Settings in Visual Basic
[!INCLUDE[vs2017banner](../../../../csharp/includes/vs2017banner.md)]

Vous pouvez utiliser la méthode `My.Settings.Save` pour rendre persistantes les modifications apportées aux paramètres utilisateur.  
  
 En général, les applications sont conçues pour rendre persistantes les modifications apportées aux paramètres utilisateur lorsque l'application s'arrête.  La raison est que l'enregistrement des paramètres peut prendre quelques secondes, en fonction de nombreux facteurs.  
  
 Pour plus d’informations, consultez [My.Settings Object](../../../../visual-basic/language-reference/objects/my-settings-object.md).  
  
> [!NOTE]
>  Même si vous pouvez modifier et enregistrer les valeurs des paramètres de portée utilisateur au moment de l'exécution, les paramètres de portée application sont en lecture seule et ne peuvent pas être modifiés par programme.  Vous pouvez modifier des paramètres de portée application lors de la création de l'application, à l'aide du **Concepteur de projets** ou en modifiant le fichier de configuration de l'application.  Pour plus d’informations, consultez [Gestion des paramètres d'une application \(.NET\)](/visual-studio/ide/managing-application-settings-dotnet).  
  
## Exemple  
 Cet exemple modifie la valeur du paramètre utilisateur `LastChanged` et enregistre cette modification en appelant la méthode `My.Settings.Save`.  
  
 [!code-vb[VbVbalrMyResources#5](../../../../visual-basic/developing-apps/programming/app-settings/codesnippet/VisualBasic/how-to-persist-user-settings_1.vb)]  
  
 Pour que cet exemple fonctionne, votre application doit avoir un paramètre utilisateur `LastChanged` de type `Date`.  Pour plus d’informations, consultez [Gestion des paramètres d'une application \(.NET\)](/visual-studio/ide/managing-application-settings-dotnet).  
  
## Voir aussi  
 [My.Settings Object](../../../../visual-basic/language-reference/objects/my-settings-object.md)   
 [How to: Read Application Settings in Visual Basic](../../../../visual-basic/developing-apps/programming/app-settings/how-to-read-application-settings.md)   
 [How to: Change User Settings in Visual Basic](../../../../visual-basic/developing-apps/programming/app-settings/how-to-change-user-settings.md)   
 [How to: Create Property Grids for User Settings in Visual Basic](../../../../visual-basic/developing-apps/programming/app-settings/how-to-create-property-grids-for-user-settings.md)   
 [Gestion des paramètres d'une application \(.NET\)](/visual-studio/ide/managing-application-settings-dotnet)