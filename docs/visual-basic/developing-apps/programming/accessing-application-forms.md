---
title: "Accessing Application Forms (Visual Basic) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "forms, communicating between"
  - "application forms, accessing"
  - "forms, accessing one from another"
  - "My.Forms object"
  - "forms, accessing all open"
ms.assetid: 9aaf5aaf-2012-4f97-89c7-6e62b9d17863
caps.latest.revision: 16
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 16
---
# Accessing Application Forms (Visual Basic)
[!INCLUDE[vs2017banner](../../../visual-basic/includes/vs2017banner.md)]

L'objet `My.Forms` permet facilement d'accéder à une instance de chaque Windows Form déclaré dans le projet de l'application.  Vous pouvez également utiliser les propriétés de l'objet `My.Application` pour accéder à l'écran de démarrage et au formulaire principal de l'application, et obtenir une liste des formulaires ouverts de l'application.  
  
## Tâches  
 Le tableau suivant répertorie des exemples qui indiquent comment accéder aux formulaires d'une application.  
  
|||  
|-|-|  
|Pour|Consultez|  
|Accéder à un formulaire à partir d'un autre formulaire d'une application.|[My.Forms Object](../../../visual-basic/language-reference/objects/my-forms-object.md)|  
|Afficher les titres de tous les formulaires ouverts de l'application.|<xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.OpenForms%2A>|  
|Mettre à jour l'écran de démarrage avec les informations d'état au démarrage de l'application.|<xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.SplashScreen%2A>|  
  
## Voir aussi  
 <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.OpenForms%2A>   
 <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.SplashScreen%2A>   
 [My.Forms Object](../../../visual-basic/language-reference/objects/my-forms-object.md)