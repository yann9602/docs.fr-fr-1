---
title: "Classe déléguée &#39; &lt;classname&gt;&#39; n’a aucun méthode Invoke, afin de l’expression de ce type ne peut pas être la cible d’un appel de méthode"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- vbc30220
- bc30220
helpviewer_keywords: BC30220
ms.assetid: 6be0d61c-f2f9-4f9b-ab90-8871a0d7206d
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 55d0e2442807e25737d90ac4b45a59b9d3e73037
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="delegate-class-39ltclassnamegt39-has-no-invoke-method-so-an-expression-of-this-type-cannot-be-the-target-of-a-method-call"></a>Classe déléguée &#39; &lt;classname&gt;&#39; n’a aucun méthode Invoke, afin de l’expression de ce type ne peut pas être la cible d’un appel de méthode
Un appel à `Invoke` via un délégué a échoué, car `Invoke` n’est pas implémentée sur la classe déléguée.  
  
 **ID d’erreur :** BC30220  
  
## <a name="to-correct-this-error"></a>Pour corriger cette erreur  
  
1.  Assurez-vous qu’une instance de la classe déléguée a été créée avec un `Dim` instruction et qu’une procédure a été assignée à l’instance de délégué avec le `AddressOf` opérateur.  
  
2.  Recherchez le code qui implémente la classe déléguée et vérifiez qu’il implémente la `Invoke` procédure.  
  
## <a name="see-also"></a>Voir aussi  
 [Délégués](../../../visual-basic/programming-guide/language-features/delegates/index.md)  
 [Delegate (instruction)](../../../visual-basic/language-reference/statements/delegate-statement.md)  
 [AddressOf (opérateur)](../../../visual-basic/language-reference/operators/addressof-operator.md)  
 [Dim (instruction)](../../../visual-basic/language-reference/statements/dim-statement.md)
