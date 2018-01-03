---
title: "Itérateur (Visual Basic)"
ms.date: 07/20/2015
ms.prod: .net
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords: vb.Iterator
helpviewer_keywords: Iterator keyword [Visual Basic]
ms.assetid: 69cb0b04-ac87-49d0-bcfe-810c0d60daff
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: fd6c0b1fa422dc4ab659d8c59472e5c098c729bc
ms.sourcegitcommit: 34ec7753acf76f90a0fa845235ef06663dc9e36e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/21/2017
---
# <a name="iterator-visual-basic"></a>Itérateur (Visual Basic)
Spécifie qu’une fonction ou `Get` accesseur est un itérateur.  
  
## <a name="remarks"></a>Notes  
 Un *itérateur* effectue une itération personnalisée sur une collection. Un itérateur utilise le [Yield](../../../visual-basic/language-reference/statements/yield-statement.md) instruction pour retourner chaque élément dans la collection un à la fois. Lorsqu’un `Yield` instruction est atteinte, l’emplacement actuel dans le code est conservé. L'exécution redémarrera à partir de cet emplacement la prochaine fois que la fonction d'itérateur sera appelée.  
  
 Un itérateur peut être implémenté sous la forme d’une fonction ou un `Get` accesseur d’une définition de propriété. Le `Iterator` modificateur apparaît dans la déclaration de la fonction d’itérateur ou `Get` accesseur.  
  
 Vous appelez un itérateur depuis le code client en utilisant un [For Each... L’instruction suivante](../../../visual-basic/language-reference/statements/for-each-next-statement.md).  
  
 Le type de retour d’une fonction d’itérateur ou `Get` accesseur peut être <xref:System.Collections.IEnumerable>, <xref:System.Collections.Generic.IEnumerable%601>, <xref:System.Collections.IEnumerator>, ou <xref:System.Collections.Generic.IEnumerator%601>.  
  
 Un itérateur ne peut avoir aucune `ByRef` paramètres.  
  
 Un itérateur ne peut pas être présent dans un événement, un constructeur d’instance, un constructeur statique ou un destructeur statique.  
  
 Un itérateur peut être une fonction anonyme. Pour plus d'informations, consultez [Itérateurs](../../programming-guide/concepts/iterators.md).  
  
## <a name="usage"></a>Utilisation  
 Le modificateur `Iterator` peut être utilisé dans les contextes suivants :  
  
-   [Function (instruction)](../../../visual-basic/language-reference/statements/function-statement.md)  
  
-   [Property (instruction)](../../../visual-basic/language-reference/statements/property-statement.md)  
  
## <a name="example"></a>Exemple  
 L’exemple suivant montre une fonction d’itérateur. La fonction d’itérateur a un `Yield` instruction qui se trouve dans un [pour... Suivant](../../../visual-basic/language-reference/statements/for-next-statement.md) boucle. Chaque itération de la [pour chaque](../../../visual-basic/language-reference/statements/for-each-next-statement.md) corps de l’instruction dans `Main` crée un appel à la `Power` fonction d’itérateur. Chaque appel à la fonction d'itérateur continue vers l'exécution suivante de l'instruction `Yield`, qui se produit pendant l'itération suivante de la boucle `For…Next`.  
  
 [!code-vb[VbVbalrStatements#98](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/iterator_1.vb)]  
  
## <a name="example"></a>Exemple  
 L'exemple suivant illustre un accesseur `Get` qui est un itérateur. Le `Iterator` modificateur est dans la déclaration de propriété.  
  
 [!code-vb[VbVbalrStatements#99](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/iterator_2.vb)]  
  
 Pour obtenir des exemples supplémentaires, consultez [itérateurs](../../programming-guide/concepts/iterators.md).  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.Runtime.CompilerServices.IteratorStateMachineAttribute>  
 [Itérateurs](../../programming-guide/concepts/iterators.md)  
 [Yield (instruction)](../../../visual-basic/language-reference/statements/yield-statement.md)
