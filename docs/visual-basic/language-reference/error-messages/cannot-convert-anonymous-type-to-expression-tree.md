---
title: "Impossible de convertir le type anonyme en arborescence de l’expression, car elle contient un champ qui sert à initialiser un autre champ"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- bc36548
- vbc36548
helpviewer_keywords: BC36548
ms.assetid: 27de068f-080e-4160-86bf-1ec23fd1925a
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: c2cf8a40060359393807cfb648c46fef9ed853af
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="cannot-convert-anonymous-type-to-expression-tree-because-it-contains-a-field-that-is-used-in-the-initialization-of-another-field"></a>Impossible de convertir le type anonyme en arborescence de l’expression, car elle contient un champ qui sert à initialiser un autre champ
Le compilateur n’accepte pas de conversion d’anonyme en arborescence d’expression lorsqu’une propriété du type anonyme est utilisée pour initialiser une autre propriété du type anonyme. Par exemple, dans le code suivant, `Prop1` déclaré dans la liste d’initialisation et puis utilisé comme valeur initiale pour `Prop2`.  
  
```vb  
Module M2  
  
    Sub ExpressionExample(Of T)(ByVal x As Expressions.Expression(Of Func(Of T)))  
    End Sub  
  
    Sub Main()  
        ' The following line causes the error.  
        ' ExpressionExample(Function() New With {.Prop1 = 2, .Prop2 = .Prop1})  
  
    End Sub  
End Module  
```  
  
 **ID d’erreur :** BC36548  
  
## <a name="to-correct-this-error"></a>Pour corriger cette erreur  
  
-   Assignez la valeur initiale pour `Prop1` à une variable locale. Assignez cette variable à la fois aux `Prop1` et `Prop2`, comme illustré dans le code suivant.  
  
    ```  
    Sub Main()  
  
        Dim temp = 2  
        ExpressionExample(Function() New With {.Prop1 = temp, .Prop2 = temp})  
  
    End Sub  
    ```  
  
## <a name="see-also"></a>Voir aussi  
 [Types anonymes](../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md)  
 [Arborescences de l’expression](http://msdn.microsoft.com/library/fb1d3ed8-d5b0-4211-a71f-dd271529294b)  
 [Guide pratique : utiliser des arborescences d’expression pour générer des requêtes dynamiques](http://msdn.microsoft.com/library/1e37e0cc-eef3-48bb-8b69-3adabf322735)
