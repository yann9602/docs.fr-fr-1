---
title: yield, instruction (Visual Basic)
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords: vb.Yield
helpviewer_keywords:
- iterators, Yield statement [Visual Basic]
- iterators [Visual Basic]
- Yield statement [Visual Basic]
ms.assetid: f33126c5-d7c4-43e2-8e36-4ae3f0703d97
caps.latest.revision: "22"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 99f5129d5cb43cddfb17731f337a72fae22d3626
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="yield-statement-visual-basic"></a>yield, instruction (Visual Basic)
Envoie l’élément suivant d’un regroupement à un `For Each...Next` instruction.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
Yield expression  
```  
  
#### <a name="parameters"></a>Paramètres  
  
|Terme|Définition|  
|---|---|  
|`expression`|Obligatoire. Une expression qui est implicitement convertible au type de la fonction d’itérateur ou `Get` accesseur qui contienne la `Yield` instruction.|  
  
## <a name="remarks"></a>Remarques  
 La `Yield` instruction retourne un élément d’une collection à la fois. Le `Yield` instruction est incluse dans une fonction d’itérateur ou `Get` accesseur, qui effectuent des itérations personnalisées sur une collection.  
  
 Vous consommez une fonction d’itérateur en utilisant un [For Each... L’instruction suivante](../../../visual-basic/language-reference/statements/for-each-next-statement.md) ou une requête LINQ. Chaque itération de la `For Each` boucle appelle la fonction d’itérateur. Lorsqu’un `Yield` instruction est atteint dans la fonction d’itérateur, `expression` est renvoyé, et l’emplacement actuel dans le code est conservé. L'exécution redémarrera à partir de cet emplacement la prochaine fois que la fonction d'itérateur sera appelée.  
  
 Une conversion implicite doit exister entre le type de `expression` dans la `Yield` instruction pour le type de retour de l’itérateur.  
  
 Vous pouvez utiliser un `Exit Function` ou `Return` instruction à la fin de l’itération.  
  
 « Produit » n’est pas un mot réservé et a une signification spéciale uniquement lorsqu’il est utilisé dans une `Iterator` fonction ou `Get` accesseur.  
  
 Pour plus d’informations sur les fonctions d’itérateur et `Get` accesseurs, consultez [itérateurs](http://msdn.microsoft.com/library/f45331db-d595-46ec-9142-551d3d1eb1a7).  
  
## <a name="iterator-functions-and-get-accessors"></a>Fonctions d’itérateur et accesseurs Get  
 La déclaration d’une fonction d’itérateur ou `Get` accesseur doit remplir les conditions suivantes :  
  
-   Il doit inclure un [itérateur](../../../visual-basic/language-reference/modifiers/iterator.md) modificateur.  
  
-   Le type de retour doit être <xref:System.Collections.IEnumerable>, <xref:System.Collections.Generic.IEnumerable%601>, <xref:System.Collections.IEnumerator>, ou <xref:System.Collections.Generic.IEnumerator%601>.  
  
-   Il ne peut avoir aucune `ByRef` paramètres.  
  
 Une fonction d’itérateur ne peut pas se produire dans un événement, un constructeur d’instance, un constructeur statique ou un destructeur statique.  
  
 Une fonction d’itérateur peut être une fonction anonyme. Pour plus d’informations, consultez [Itérateurs](http://msdn.microsoft.com/library/f45331db-d595-46ec-9142-551d3d1eb1a7).  
  
## <a name="exception-handling"></a>Gestion des exceptions  
 A `Yield` instruction peut être à l’intérieur d’un `Try` bloc d’un [essayez... Catch... Instruction finally](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md). A `Try` bloc qui a un `Yield` instruction peut avoir `Catch` bloque et peut avoir un `Finally` bloc.  
  
 A `Yield` instruction ne peut pas être à l’intérieur d’un `Catch` bloc ou une `Finally` bloc.  
  
 Si le `For Each` corps (en dehors de la fonction d’itérateur) lève une exception, une `Catch` bloc dans la fonction d’itérateur n’est pas exécutée, mais un `Finally` bloc dans la fonction d’itérateur est exécuté. A `Catch` bloc à l’intérieur d’une fonction d’itérateur intercepte uniquement les exceptions qui se produisent à l’intérieur de la fonction d’itérateur.  
  
## <a name="technical-implementation"></a>Implémentation technique  
 Le code suivant retourne un `IEnumerable (Of String)` à partir d’une fonction d’itérateur parcourt ensuite les éléments de la `IEnumerable (Of String)`.  
  
```vb  
Dim elements As IEnumerable(Of String) = MyIteratorFunction()  
    …  
For Each element As String In elements  
Next  
```  
  
 L’appel à `MyIteratorFunction` n’exécute pas le corps de la fonction. À la place, l'appel retourne `IEnumerable(Of String)` dans la variable `elements`.  
  
 Dans une itération de la boucle `For Each`, la méthode <xref:System.Collections.IEnumerator.MoveNext%2A> est appelée pour `elements`. Cet appel exécute le corps de `MyIteratorFunction` jusqu'à ce que l'instruction `Yield` suivante soit atteinte. Le `Yield` instruction retourne une expression qui détermine non seulement la valeur de la `element` variable pour la consommation par le corps de la boucle, mais également le <xref:System.Collections.Generic.IEnumerator%601.Current%2A> propriété d’éléments, qui est un `IEnumerable (Of String)`.  
  
 À chaque itération suivante de la boucle `For Each`, l'exécution du corps de l'itérateur reprend à partir de l'emplacement où elle s'est interrompue, et s'arrête encore lorsqu'elle atteint une instruction `Yield`. Le `For Each` boucle termine lorsque la fin de la fonction d’itérateur ou une `Return` ou `Exit Function` instruction est atteinte.  
  
## <a name="example"></a>Exemple  
 L’exemple suivant comprend une `Yield` instruction qui se trouve dans un [pour... Suivant](../../../visual-basic/language-reference/statements/for-next-statement.md) boucle. Chaque itération de la [pour chaque](../../../visual-basic/language-reference/statements/for-each-next-statement.md) corps de l’instruction dans `Main` crée un appel à la `Power` fonction d’itérateur. Chaque appel à la fonction d'itérateur continue vers l'exécution suivante de l'instruction `Yield`, qui se produit pendant l'itération suivante de la boucle `For…Next`.  
  
 Le type de retour de la méthode iterator est <xref:System.Collections.Generic.IEnumerable%601>, un type interface itérateur. Lorsque la méthode Iterator est appelée, elle retourne un objet énumérable contenant les puissances d'un nombre.  
  
 [!code-vb[VbVbalrStatements#98](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/yield-statement_1.vb)]  
  
## <a name="example"></a>Exemple  
 L'exemple suivant illustre un accesseur `Get` qui est un itérateur. La déclaration de propriété comprend un `Iterator` modificateur.  
  
 [!code-vb[VbVbalrStatements#99](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/yield-statement_2.vb)]  
  
 Pour obtenir des exemples supplémentaires, consultez [itérateurs](http://msdn.microsoft.com/library/f45331db-d595-46ec-9142-551d3d1eb1a7).  
  
## <a name="see-also"></a>Voir aussi  
 [Itérateurs](http://msdn.microsoft.com/library/f45331db-d595-46ec-9142-551d3d1eb1a7)  
 [Instructions](../../../visual-basic/language-reference/statements/index.md)
