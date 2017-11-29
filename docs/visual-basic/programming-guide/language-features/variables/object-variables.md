---
title: Variables objet dans Visual Basic
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- object variables [Visual Basic], about object variables
- variables [Visual Basic], object
- objects [Visual Basic], accessing
- object variables [Visual Basic]
ms.assetid: 6169a196-2b13-4ba5-a205-154bc1b87844
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 44689d649a381618e5d6c934deb2b7b9bea463ed
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="object-variables-in-visual-basic"></a>Variables objet dans Visual Basic
En plus de stockage direct de valeurs, une variable peut faire référence à un objet. Vous assignez un objet à une variable pour les mêmes raisons que vous assignez une valeur à une variable :  
  
-   Un nom de variable est souvent plus court et plus facile à retenir que le chemin d’accès complet de méthodes et propriétés nécessaires pour accéder à l’objet lui-même.  
  
-   À l’aide d’une variable qui fait référence à un objet est plus efficace qu’en accédant à plusieurs reprises de l’objet lui-même via les méthodes ou propriétés nécessaires.  
  
-   Vous pouvez modifier une variable pour faire référence à d’autres objets pendant l’exécution de votre code.  
  
## <a name="making-code-shorter"></a>Raccourcissement du code  
 Vous pouvez utiliser des variables objets pour réduire le code que vous devez taper. L’exemple suivant utilise le chemin d’accès complet de méthodes et propriétés pour accéder à un <xref:System.Windows.Forms.Control> objet.  
  
```  
' Assume Me is a valid Form, or replace Me with a valid Form.  
Me.ActiveForm.ActiveControl.Text = "Test"  
Me.ActiveForm.ActiveControl.Location = New Point(100, 100)  
Me.ActiveForm.ActiveControl.Show()  
```  
  
 Vous pouvez réduire ce code et accélérer l’exécution, si vous utilisez une variable objet pour le contrôle. Vous devez déclarer la variable objet avec la classe spécifique que vous prévoyez d’affecter à ce dernier (`Control` dans ce cas). Une fois que vous assignez un objet à la variable, vous pouvez traiter il d’exactement comme l’objet auquel il fait référence. Vous pouvez définir ou récupérer les propriétés de l’objet ou utiliser une de ses méthodes. L’exemple suivant utilise une variable objet pour simplifier le code dans l’exemple précédent.  
  
```  
Dim ctrlActv As System.Windows.Forms.Control = Me.ActiveForm.ActiveControl  
ctrlActv.Text = "Test"  
ctrlActv.Location = New Point(100, 100)  
ctrlActv.Show()  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Déclaration de variable](../../../../visual-basic/programming-guide/language-features/variables/variable-declaration.md)  
 [Guide pratique : accélérer l’accès à un objet comportant un chemin d’accès de qualification long](../../../../visual-basic/programming-guide/language-features/variables/how-to-speed-up-access-to-an-object-with-a-long-qualification-path.md)  
 [Déclaration des variables objets](../../../../visual-basic/programming-guide/language-features/variables/object-variable-declaration.md)  
 [Assignation des variables objets](../../../../visual-basic/programming-guide/language-features/variables/object-variable-assignment.md)  
 [Valeurs des variables objets](../../../../visual-basic/programming-guide/language-features/variables/object-variable-values.md)
