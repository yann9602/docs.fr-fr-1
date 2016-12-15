---
title: "Rapid Application Development with My.Resources and My.Settings (Visual Basic) | Microsoft Docs"
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
  - "My.Settings object, developing applications"
  - "rapid application development (RAD), My.Resources"
  - "rapid application development (RAD), My.Settings"
  - "My.Resources object, developing applications"
ms.assetid: 68284ab1-b685-4814-a2a4-01ae40445ff8
caps.latest.revision: 6
caps.handback.revision: 6
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Rapid Application Development with My.Resources and My.Settings (Visual Basic)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

L'objet `My.Resources` fournit l'accès aux ressources de l'application et vous permet de récupérer de manière dynamique des ressources pour votre application.  
  
## Récupération de ressources  
 Plusieurs ressources telles que les fichiers audio, les icônes, les images et les chaînes peuvent être récupérées par le biais de l'objet `My.Resources`.  Par exemple, vous pouvez accéder aux fichiers de ressources spécifiques de la culture de l'application.  L'exemple suivant définit l'icône du formulaire comme étant l'icône nommée `Form1Icon` stockée dans le fichier de ressources de l'application.  
  
 [!code-vb[VbVbcnMy#7](../../../visual-basic/developing-apps/development-with-my/codesnippet/VisualBasic/rapid-application-development-with-my-resources-and-my-settings_1.vb)]  
  
 L'objet `My.Resources` expose uniquement des ressources globales.  Il ne fournit pas l'accès aux fichiers de ressources associés aux formulaires.  Vous devez accéder aux ressources du formulaire à partir du formulaire.  Pour plus d'informations, consultez [Walkthrough: Localizing Windows Forms](http://msdn.microsoft.com/fr-fr/9a96220d-a19b-4de0-9f48-01e5d82679e5).  
  
 De la même façon, l'objet `My.Settings` fournit l'accès aux paramètres de l'application et vous permet de stocker et de récupérer de manière dynamique des paramètres de propriété et d'autres informations pour votre application.  Pour plus d'informations, consultez [My.Resources Object](../../../visual-basic/language-reference/objects/my-resources-object.md) et [My.Settings Object](../../../visual-basic/language-reference/objects/my-settings-object.md).  
  
## Voir aussi  
 [My.Resources Object](../../../visual-basic/language-reference/objects/my-resources-object.md)   
 [My.Settings Object](../../../visual-basic/language-reference/objects/my-settings-object.md)   
 [Accessing Application Settings](../../../visual-basic/developing-apps/programming/app-settings/accessing-application-settings.md)