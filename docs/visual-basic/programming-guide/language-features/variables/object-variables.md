---
title: "Object Variables in Visual Basic | Microsoft Docs"
ms.custom: ""
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "object variables, about object variables"
  - "variables [Visual Basic], object"
  - "objects [Visual Basic], accessing"
  - "object variables"
ms.assetid: 6169a196-2b13-4ba5-a205-154bc1b87844
caps.latest.revision: 14
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 14
---
# Object Variables in Visual Basic
[!INCLUDE[vs2017banner](../../../../visual-basic/includes/vs2017banner.md)]

Outre le stockage direct de valeurs, une variable peut faire référence à un objet.  Vous assignez un objet à une variable pour les mêmes raisons que vous assignez une valeur à une variable :  
  
-   Un nom de variable est souvent plus court et plus facile à se rappeler que le chemin d'accès complet des méthodes et propriétés permettant d'accéder à l'objet lui\-même.  
  
-   L'utilisation d'une variable faisant référence à un objet est souvent plus efficace qu'un accès répété à cet objet via les méthodes ou propriétés nécessaires.  
  
-   Vous pouvez modifier une variable pour faire référence à d'autres objets durant l'exécution de votre code.  
  
## Raccourcissement du code  
 Vous pouvez utiliser des variables objets pour réduire la longueur du code à taper.  L'exemple suivant utilise le chemin d'accès complet de méthodes et de propriétés pour accéder à un objet <xref:System.Windows.Forms.Control>.  
  
```  
' Assume Me is a valid Form, or replace Me with a valid Form.  
Me.ActiveForm.ActiveControl.Text = "Test"  
Me.ActiveForm.ActiveControl.Location = New Point(100, 100)  
Me.ActiveForm.ActiveControl.Show()  
```  
  
 Vous pouvez réduire la longueur de ce code, et accélérer son exécution, si vous utilisez une variable objet en guise de contrôle.  Vous devez déclarer la variable objet à l'aide de la classe spécifique que vous comptez lui assigner \(`Control` dans le cas présent\).  Une fois que vous assignez un objet à la variable, vous pouvez traiter celle\-ci de la même façon que l'objet auquel elle fait référence.  Vous pouvez définir ou récupérer les propriétés de l'objet ou utiliser n'importe laquelle de ses méthodes.  L'exemple suivant utilise une variable objet pour simplifier le code de l'exemple précédent.  
  
```  
Dim ctrlActv As System.Windows.Forms.Control = Me.ActiveForm.ActiveControl  
ctrlActv.Text = "Test"  
ctrlActv.Location = New Point(100, 100)  
ctrlActv.Show()  
```  
  
## Voir aussi  
 [Déclaration de variable](../../../../visual-basic/programming-guide/language-features/variables/variable-declaration.md)   
 [How to: Speed Up Access to an Object with a Long Qualification Path](../../../../visual-basic/programming-guide/language-features/variables/how-to-speed-up-access-to-an-object-with-a-long-qualification-path.md)   
 [Object Variable Declaration](../../../../visual-basic/programming-guide/language-features/variables/object-variable-declaration.md)   
 [Object Variable Assignment](../../../../visual-basic/programming-guide/language-features/variables/object-variable-assignment.md)   
 [Object Variable Values](../../../../visual-basic/programming-guide/language-features/variables/object-variable-values.md)