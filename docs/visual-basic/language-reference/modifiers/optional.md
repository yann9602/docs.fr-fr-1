---
title: Optional (Visual Basic)
ms.date: 07/20/2015
ms.prod: .net
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.Optional
- vb.optional
helpviewer_keywords:
- Optional keyword [Visual Basic], contexts
- Optional keyword [Visual Basic]
ms.assetid: 4571ce88-a539-4115-b230-54eb277c6aa7
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 3aa01c2c1ae731c8fe00fdee24521760db69e624
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="optional-visual-basic"></a>Optional (Visual Basic)
Spécifie qu’un argument de procédure peut être omis lorsque la procédure est appelée.  
  
## <a name="remarks"></a>Remarques  
 Pour chaque paramètre facultatif, vous devez spécifier une expression constante comme valeur par défaut de ce paramètre. Si l’expression prend la valeur [rien](../../../visual-basic/language-reference/nothing.md), la valeur par défaut la valeur du type de données est utilisée comme valeur par défaut du paramètre.  
  
 Si la liste de paramètres contient un paramètre facultatif, chaque paramètre qui le suit doit également être facultatif.  
  
 Le modificateur `Optional` peut être utilisé dans les contextes suivants :  
  
-   [Declare (instruction)](../../../visual-basic/language-reference/statements/declare-statement.md)  
  
-   [Function (instruction)](../../../visual-basic/language-reference/statements/function-statement.md)  
  
-   [Property (instruction)](../../../visual-basic/language-reference/statements/property-statement.md)  
  
-   [Sub (instruction)](../../../visual-basic/language-reference/statements/sub-statement.md)  
  
> [!NOTE]
>  Lorsque vous appelez une procédure avec ou sans paramètres facultatifs, vous pouvez passer des arguments par position ou par nom. Pour plus d’informations, consultez [en passant les Arguments par Position et par nom](../../../visual-basic/programming-guide/language-features/procedures/passing-arguments-by-position-and-by-name.md).  
  
> [!NOTE]
>  Vous pouvez également définir une procédure avec des paramètres facultatifs à l’aide de la surcharge. Si vous avez un seul paramètre facultatif, vous pouvez définir deux versions surchargées de la procédure, un qui accepte le paramètre et un autre. Pour plus d’informations, consultez [surcharge de procédure](../../../visual-basic/programming-guide/language-features/procedures/procedure-overloading.md).  
  
## <a name="example"></a>Exemple  
 L’exemple suivant définit une procédure qui possède un paramètre facultatif.  
  
```  
Public Function FindMatches(ByRef values As List(Of String),  
                            ByVal searchString As String,  
                            Optional ByVal matchCase As Boolean = False) As List(Of String)  
  
    Dim results As IEnumerable(Of String)  
  
    If matchCase Then  
        results = From v In values  
                  Where v.Contains(searchString)  
    Else  
        results = From v In values  
                  Where UCase(v).Contains(UCase(searchString))  
    End If  
  
    Return results.ToList()  
End Function  
```  
  
## <a name="example"></a>Exemple  
 L’exemple suivant montre comment appeler une procédure avec des arguments passés par position et avec des arguments passés par nom. La procédure comporte deux paramètres facultatifs.  
  
 [!code-vb[VbVbalrKeywords#21](../../../visual-basic/language-reference/codesnippet/VisualBasic/optional_1.vb)]  
  
## <a name="see-also"></a>Voir aussi  
 [Liste de paramètres](../../../visual-basic/language-reference/statements/parameter-list.md)  
 [Paramètres facultatifs](../../../visual-basic/programming-guide/language-features/procedures/optional-parameters.md)  
 [Mots clés](../../../visual-basic/language-reference/keywords/index.md)
