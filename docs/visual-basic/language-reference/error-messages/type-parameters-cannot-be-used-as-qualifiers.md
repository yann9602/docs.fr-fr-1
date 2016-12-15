---
title: "Type parameters cannot be used as qualifiers | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vbc32098"
  - "bc32098"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "BC32098"
ms.assetid: bab05325-dde8-4621-a5f6-368b5b7b2d76
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Type parameters cannot be used as qualifiers
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Un élément de programmation est qualifié avec une chaîne de qualification qui inclut un paramètre de type.  
  
 Un paramètre de type représente une exigence pour un type à fournir lorsque le type générique est construit.  Il ne représente pas un type défini spécifique.  Une chaîne de qualification ne doit inclure que les éléments définis au moment de la compilation.  
  
 Les instructions suivantes peuvent générer cette erreur.  
  
```  
Public Function checkText(Of c As System.Windows.Forms.Control)(  
    ByVal badText As String) As Boolean  
  
    Dim saveText As c.Text  
    ' Insert code to look for badText within saveText.  
End Function  
```  
  
 **ID d'erreur :** BC32098  
  
### Pour corriger cette erreur  
  
1.  Supprimez le paramètre de type de la chaîne de qualification ou remplacez\-le par un type défini.  
  
2.  Si vous devez utiliser un type construit pour rechercher l'élément de programmation qualifié, vous devez utiliser une logique de programme supplémentaire.  
  
## Voir aussi  
 [References to Declared Elements](../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)   
 [Types génériques Visual Basic](../../../visual-basic/programming-guide/language-features/data-types/generic-types.md)   
 [Type List](../../../visual-basic/language-reference/statements/type-list.md)