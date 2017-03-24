---
title: "Optional (Visual Basic) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
f1_keywords: 
  - "vb.Optional"
  - "vb.optional"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "Optional keyword, contexts"
  - "Optional keyword"
ms.assetid: 4571ce88-a539-4115-b230-54eb277c6aa7
caps.latest.revision: 14
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 14
---
# Optional (Visual Basic)
[!INCLUDE[vs2017banner](../../../visual-basic/includes/vs2017banner.md)]

Spécifie qu'un argument de procédure peut être omis lorsque la procédure est appelée.  
  
## Notes  
 Pour chaque paramètre optionnel, vous devez spécifier une expression constante comme valeur par défaut de ce paramètre.  Si l'expression a la [rien](../../../visual-basic/language-reference/nothing.md), la valeur par défaut du type de données valeur est utilisée comme valeur par défaut du paramètre.  
  
 Si la liste de paramètres contient un paramètre optionnel, chaque paramètre qui le suit doivent également être facultatifs.  
  
 Le modificateur `Optional` peut être utilisé dans les contextes suivants :  
  
-   [Declare, instruction](../../../visual-basic/language-reference/statements/declare-statement.md)  
  
-   [Function, instruction](../../../visual-basic/language-reference/statements/function-statement.md)  
  
-   [Property, instruction](../../../visual-basic/language-reference/statements/property-statement.md)  
  
-   [Sub, instruction](../../../visual-basic/language-reference/statements/sub-statement.md)  
  
> [!NOTE]
>  En appelant une procédure avec ou sans paramètres optionnels, vous pouvez passer des arguments par position ou son nom.  Pour plus d'informations, consultez [Passing Arguments by Position and by Name](../../../visual-basic/programming-guide/language-features/procedures/passing-arguments-by-position-and-by-name.md).  
  
> [!NOTE]
>  Vous pouvez également définir une procédure avec des paramètres optionnels à l'aide de la surcharge.  Si vous avez un paramètre facultatif, vous pouvez définir deux versions surchargées de la procédure, de celle qui acceptent le paramètre et de celle qui ne fait pas.  Pour plus d'informations, consultez [Procedure Overloading](../../../visual-basic/programming-guide/language-features/procedures/procedure-overloading.md).  
  
## Exemple  
 L'exemple suivant définit une procédure qui possède un paramètre optionnel.  
  
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
  
## Exemple  
 L'exemple suivant montre comment appeler une procédure avec des arguments passés par position et avec des arguments passés par nom.  La procédure a deux paramètres optionnels.  
  
 [!code-vb[VbVbalrKeywords#21](../../../visual-basic/language-reference/codesnippet/VisualBasic/optional_1.vb)]  
  
## Voir aussi  
 [Parameter List](../../../visual-basic/language-reference/statements/parameter-list.md)   
 [Optional Parameters](../../../visual-basic/programming-guide/language-features/procedures/optional-parameters.md)   
 [Mots clés](../../../visual-basic/language-reference/keywords/index.md)