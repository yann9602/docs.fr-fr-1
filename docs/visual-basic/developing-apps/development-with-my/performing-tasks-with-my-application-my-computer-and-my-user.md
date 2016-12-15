---
title: "Performing Tasks with My.Application, My.Computer, and My.User (Visual Basic) | Microsoft Docs"
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
  - "My.Application object, developing applications"
  - "rapid application development (RAD), My.Application"
  - "rapid application development (RAD), My.Computer"
  - "rapid application development (RAD), My.User"
  - "My.Computer object, developing applications"
  - "My.User object, developing applications"
ms.assetid: c8af61bd-4dd3-4a0f-9af5-795b594b240b
caps.latest.revision: 7
caps.handback.revision: 7
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Performing Tasks with My.Application, My.Computer, and My.User (Visual Basic)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Les trois objets centraux `My` qui permettent d'accéder aux informations et aux fonctionnalités couramment utilisées sont `My.Application` \(<xref:Microsoft.VisualBasic.ApplicationServices.ApplicationBase>\), `My.Computer` \(<xref:Microsoft.VisualBasic.Devices.Computer>\) et `My.User` \(<xref:Microsoft.VisualBasic.ApplicationServices.User>\).  Vous pouvez utiliser ces objets pour accéder aux informations liées à l'application actuelle, à l'ordinateur sur lequel est installée l'application, ou l'utilisateur actuel de l'application, respectivement.  
  
## My.Application, My.Computer et My.User  
 Les exemples suivants montrent comment les informations peuvent être récupérées à l'aide de `My`.  
  
 [!code-vb[VbVbcnMy#1](../../../visual-basic/developing-apps/development-with-my/codesnippet/VisualBasic/performing-tasks-with-my-application-my-computer-and-my-user_1.vb)]  
  
 [!code-vb[VbVbcnMy#2](../../../visual-basic/developing-apps/development-with-my/codesnippet/VisualBasic/performing-tasks-with-my-application-my-computer-and-my-user_2.vb)]  
  
 Outre la récupération d'informations, les membres exposés à travers ces trois objets vous permettent également d'exécuter des méthodes en rapport avec cet objet.  Par exemple, vous pouvez accéder à diverses méthodes destinées à la manipulation de fichiers ou à la mise à jour du Registre par le biais de `My.Computer`.  
  
 Les E\/S de fichiers sont considérablement plus faciles et rapides avec `My`, qui inclut diverses méthodes et propriétés pour la manipulation de fichiers, répertoires et lecteurs.  L'objet <xref:Microsoft.VisualBasic.FileIO.TextFieldParser> vous permet de lire des fichiers volumineux structurés qui sont dotés de champs délimités ou à largeur fixe.  Cet exemple ouvre `TextFieldParser` `reader` et l'utilise pour lire `C:\TestFolder1\test1.txt`.  
  
 [!code-vb[VbVbalrTextFieldParser#23](../../../visual-basic/developing-apps/development-with-my/codesnippet/VisualBasic/performing-tasks-with-my-application-my-computer-and-my-user_3.vb)]  
  
 `My.Application` vous permet de modifier la culture de votre application.  L'exemple de code suivant montre comment appeler cette méthode.  
  
 [!code-vb[VbVbcnMy#3](../../../visual-basic/developing-apps/development-with-my/codesnippet/VisualBasic/performing-tasks-with-my-application-my-computer-and-my-user_4.vb)]  
  
## Voir aussi  
 <xref:Microsoft.VisualBasic.ApplicationServices.ApplicationBase>   
 <xref:Microsoft.VisualBasic.Devices.Computer>   
 <xref:Microsoft.VisualBasic.ApplicationServices.User>   
 [How My Depends on Project Type](../../../visual-basic/developing-apps/development-with-my/how-my-depends-on-project-type.md)