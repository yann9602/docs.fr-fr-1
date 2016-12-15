---
title: "Default Object Instances Provided by My.Forms and My.WebServices (Visual Basic) | Microsoft Docs"
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
  - "My.WebServices object, developing applications"
  - "My.Forms object, developing applications"
  - "rapid application development (RAD), My.Forms"
  - "rapid application development (RAD), My.WebServices"
ms.assetid: de930027-9108-4f0c-b97c-5e7db4d6ef79
caps.latest.revision: 5
caps.handback.revision: 5
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Default Object Instances Provided by My.Forms and My.WebServices (Visual Basic)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Les objets [My.Forms](../../../visual-basic/language-reference/objects/my-forms-object.md) et [My.WebServices](../../../visual-basic/language-reference/objects/my-webservices-object.md) fournissent l'accès aux formulaires, sources de données et services Web XML utilisés par votre application.  Pour ce faire, ils fournissent des collections d'*instances par défaut* de chacun de ces objets.  
  
## Instances par défaut  
 Une instance par défaut est une instance de la classe qui est fournie par le runtime ; elle n'a pas besoin d'être déclarée et instanciée à l'aide des instructions `Dim` et `New`.  L'exemple suivant montre comment déclarer et instancier une instance d'une classe <xref:System.Windows.Forms.Form> appelée `Form1`, et comment obtenir une instance par défaut de ce <xref:System.Windows.Forms.Form> par le biais de `My.Forms`.  
  
 [!code-vb[VbVbcnMy#5](../../../visual-basic/developing-apps/development-with-my/codesnippet/VisualBasic/default-object-instances-provided-by-my-forms-and-my-webservices_1.vb)]  
  
 [!code-vb[VbVbcnMy#6](../../../visual-basic/developing-apps/development-with-my/codesnippet/VisualBasic/default-object-instances-provided-by-my-forms-and-my-webservices_2.vb)]  
  
 L'objet `My.Forms` retourne une collection d'instances par défaut pour chaque classe `Form` qui existe dans votre projet.  De la même façon, `My.WebServices` fournit une instance par défaut de la classe proxy pour chaque service Web auquel vous avez créé une référence dans votre application.  
  
## Voir aussi  
 [My.Forms Object](../../../visual-basic/language-reference/objects/my-forms-object.md)   
 [My.WebServices Object](../../../visual-basic/language-reference/objects/my-webservices-object.md)   
 [How My Depends on Project Type](../../../visual-basic/developing-apps/development-with-my/how-my-depends-on-project-type.md)