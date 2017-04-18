---
title: "Délégué de la classe&lt;classname&gt;&quot; n’a aucun méthode Invoke, donc une expression de ce type ne peut pas être la cible d’un appel de méthode | Documents Microsoft"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vbc30220
- bc30220
dev_langs:
- VB
helpviewer_keywords:
- BC30220
ms.assetid: 6be0d61c-f2f9-4f9b-ab90-8871a0d7206d
caps.latest.revision: 10
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: ddc5ef0f0b3e9baa58f17dafb727e250c0fba9fd
ms.lasthandoff: 03/13/2017

---
# <a name="delegate-class-39ltclassnamegt39-has-no-invoke-method-so-an-expression-of-this-type-cannot-be-the-target-of-a-method-call"></a>Délégué de la classe&lt;classname&gt;' n’a aucun méthode Invoke, donc une expression de ce type ne peut pas être la cible d’un appel de méthode
Un appel à `Invoke` via un délégué a échoué, car `Invoke` n’est pas implémentée sur la classe déléguée.  
  
 **ID d’erreur :** BC30220  
  
## <a name="to-correct-this-error"></a>Pour corriger cette erreur  
  
1.  Assurez-vous qu’une instance de la classe déléguée a été créée avec un `Dim` instruction et qu’une procédure a été attribuée à l’instance de délégué avec le `AddressOf` opérateur.  
  
2.  Recherchez le code qui implémente la classe déléguée et vérifiez qu’il implémente la `Invoke` procédure.  
  
## <a name="see-also"></a>Voir aussi  
 [Délégués](../../../visual-basic/programming-guide/language-features/delegates/index.md)   
 [Delegate, instruction](../../../visual-basic/language-reference/statements/delegate-statement.md)   
 [AddressOf (opérateur)](../../../visual-basic/language-reference/operators/addressof-operator.md)   
 [Dim (instruction)](../../../visual-basic/language-reference/statements/dim-statement.md)
