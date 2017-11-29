---
title: "Comment : convertir un objet en un autre type dans Visual Basic"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords: objects [Visual Basic], converting
ms.assetid: 60cb5fc7-7ba4-4ab5-9c24-480fa12ddcdc
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 053c93e7cf842138f5b9299cd2fcfa56342dd40b
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-convert-an-object-to-another-type-in-visual-basic"></a>Comment : convertir un objet en un autre type dans Visual Basic
Vous convertissez un `Object` variable à un autre type de données à l’aide d’un mot clé de conversion comme [CType, fonction](../../../../visual-basic/language-reference/functions/ctype-function.md).  
  
## <a name="example"></a>Exemple  
 L’exemple suivant convertit un `Object` variable à un `Integer` et un `String`.  
  
```  
Public Sub objectConversion(ByVal anObject As Object)  
    Dim anInteger As Integer  
    Dim aString As String  
    anInteger = CType(anObject, Integer)  
    aString = CType(anObject, String)  
End Sub  
```  
  
 Si vous savez que le contenu d’un `Object` variable sont d’un type de données particulier, il est préférable de convertir la variable de ce type de données. Si vous continuez à utiliser le `Object` variable, vous encourez soit *boxing* et *unboxing* (pour un type valeur) ou *liaison tardive* (pour un type de référence). Ces opérations tous de prendre du temps d’exécution et ralentissent les performances.  
  
## <a name="compiling-the-code"></a>Compilation du code  
 Cet exemple nécessite :  
  
-   une référence à l'espace de noms <xref:System?displayProperty=nameWithType>.  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.Object>  
 [Conversions de type dans Visual Basic](../../../../visual-basic/programming-guide/language-features/data-types/type-conversions.md)  
 [Conversions étendues et restrictives](../../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)  
 [Conversions implicites et explicites](../../../../visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md)  
 [Conversion entre des chaînes et d’autres types](../../../../visual-basic/programming-guide/language-features/data-types/conversions-between-strings-and-other-types.md)  
 [Conversions de tableau](../../../../visual-basic/programming-guide/language-features/data-types/array-conversions.md)  
 [Structures](../../../../visual-basic/programming-guide/language-features/data-types/structures.md)  
 [Types de données](../../../../visual-basic/language-reference/data-types/data-type-summary.md)  
 [Fonctions de conversion de types](../../../../visual-basic/language-reference/functions/type-conversion-functions.md)
