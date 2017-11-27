---
title: "Les paramètres de type ne peuvent pas être utilisés comme qualificateurs"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- vbc32098
- bc32098
helpviewer_keywords: BC32098
ms.assetid: bab05325-dde8-4621-a5f6-368b5b7b2d76
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 58be51e0c05750ee044f0287cde8db037718b4aa
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="type-parameters-cannot-be-used-as-qualifiers"></a>Les paramètres de type ne peuvent pas être utilisés comme qualificateurs
Un élément de programmation est qualifié avec une chaîne de qualification qui inclut un paramètre de type.  
  
 Un paramètre de type représente une exigence pour un type qui doit être fourni lorsque le type générique est construit. Il ne représente pas un type défini spécifique. Une chaîne de qualification doit inclure uniquement les éléments qui sont définis au moment de la compilation.  
  
 Les instructions suivantes peuvent générer cette erreur.  
  
```  
Public Function checkText(Of c As System.Windows.Forms.Control)(  
    ByVal badText As String) As Boolean  
  
    Dim saveText As c.Text  
    ' Insert code to look for badText within saveText.  
End Function  
```  
  
 **ID d’erreur :** BC32098  
  
## <a name="to-correct-this-error"></a>Pour corriger cette erreur  
  
1.  Supprimez le paramètre de type de la chaîne de qualification ou remplacez-le par un type défini.  
  
2.  Si vous devez utiliser un type construit pour rechercher l’élément de programmation qualifié, vous devez utiliser la logique de programme supplémentaire.  
  
## <a name="see-also"></a>Voir aussi  
 [Références aux éléments déclarés](../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)  
 [Types génériques en Visual Basic](../../../visual-basic/programming-guide/language-features/data-types/generic-types.md)  
 [Liste de types](../../../visual-basic/language-reference/statements/type-list.md)
