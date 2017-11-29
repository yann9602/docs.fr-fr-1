---
title: "La résolution de surcharge à liaison tardive ne peut pas être appliquée à &#39; &lt;nom_procédure&gt;&#39; car l’instance d’accès est un type interface"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- vbc30933
- bc30933
helpviewer_keywords:
- overload resolution [Visual Basic], with late-bound argument
- BC30933
ms.assetid: 8182eea0-dd34-4d6e-9ca0-41d8713e9dc4
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: fb7f8a9f6eadfc9fd856ea57d362b43d25ff81a1
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="latebound-overload-resolution-cannot-be-applied-to-39ltprocedurenamegt39-because-the-accessing-instance-is-an-interface-type"></a>La résolution de surcharge à liaison tardive ne peut pas être appliquée à &#39; &lt;nom_procédure&gt;&#39; car l’instance d’accès est un type interface
Le compilateur tente de résoudre une référence à une propriété surchargée ou une procédure, mais la référence échoue parce qu’un argument est de type `Object` et l’objet de référence a le type de données d’une interface. Le `Object` argument force le compilateur à résoudre la référence en tant qu’à liaison tardive.  
  
 Dans ces circonstances, le compilateur résout la surcharge via la classe d’implémentation à la place de l’interface sous-jacente. Si la classe renomme l’une des versions surchargées, le compilateur ne tient pas compte de cette version comme une surcharge car son nom est différent. Le compilateur ignore la version renommée lorsque le bon choix pour résoudre la référence peut avoir été alors à son tour.  
  
 **ID d’erreur :** BC30933  
  
## <a name="to-correct-this-error"></a>Pour corriger cette erreur  
  
-   Utilisez `CType` pour effectuer un cast de l’argument de `Object` au type spécifié par la signature de la surcharge que vous souhaitez appeler.  
  
     Notez qu’il ne permet pas d’effectuer un cast de l’objet de référence à l’interface sous-jacente. Vous devez effectuer un cast de l’argument pour éviter cette erreur.  
  
## <a name="example"></a>Exemple  
 L’exemple suivant montre un appel à une procédure surchargée `Sub` procédure qui provoque cette erreur au moment de la compilation.  
  
```  
Module m1  
    Interface i1  
        Sub s1(ByVal p1 As Integer)  
        Sub s1(ByVal p1 As Double)  
    End Interface  
    Class c1  
        Implements i1  
        Public Overloads Sub s1(ByVal p1 As Integer) Implements i1.s1  
        End Sub  
        Public Overloads Sub s2(ByVal p1 As Double) Implements i1.s1  
        End Sub  
    End Class  
    Sub Main()  
        Dim refer As i1 = New c1  
        Dim o1 As Object = 3.1415  
        ' The following reference is INVALID and causes a compiler error.  
        refer.s1(o1)   
    End Sub  
End Module  
```  
  
 Dans l’exemple précédent, si le compilateur a autorisé l’appel à `s1` lors de l’écriture, la résolution a lieu via la classe `c1` au lieu de l’interface `i1`. Cela signifie que le compilateur ne tient pas compte `s2` , car son nom est différent dans `c1`, même s’il est le bon choix, comme défini par `i1`.  
  
 Vous pouvez corriger l’erreur en modifiant l’appel à une des lignes de code suivantes :  
  
```  
refer.s1(CType(o1, Integer))  
refer.s1(CType(o1, Double))  
```  
  
 Chacune des lignes précédentes du code effectue un cast explicite le `Object` variable `o1` à un des types de paramètres définis pour les surcharges.  
  
## <a name="see-also"></a>Voir aussi  
 [Surcharge de procédure](../../../visual-basic/programming-guide/language-features/procedures/procedure-overloading.md)  
 [Résolution de surcharge](../../../visual-basic/programming-guide/language-features/procedures/overload-resolution.md)  
 [CType (fonction)](../../../visual-basic/language-reference/functions/ctype-function.md)
