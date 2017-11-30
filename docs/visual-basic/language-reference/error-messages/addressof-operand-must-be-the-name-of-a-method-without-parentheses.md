---
title: "&#39; AddressOf &#39; opérande doit être le nom d’une méthode (sans parenthèses)"
ms.date: 07/20/2015
ms.prod: .net
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- vbc30577
- bc30577
helpviewer_keywords: BC30577
ms.assetid: c2c55640-5c61-4e66-97a4-4322020c6001
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 02c996f1c94250526982e35395288b07db619db7
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="39addressof39-operand-must-be-the-name-of-a-method-without-parentheses"></a>&#39; AddressOf &#39; opérande doit être le nom d’une méthode (sans parenthèses)
L’opérateur `AddressOf` crée une instance de délégué de procédure qui fait référence à une procédure spécifique. La syntaxe est la suivante.  
  
 `AddressOf` `procedurename`  
  
 Vous avez inséré des parenthèses autour de l’argument qui suit `AddressOf`, où aucune n’est nécessaire.  
  
 **ID d’erreur :** BC30577  
  
## <a name="to-correct-this-error"></a>Pour corriger cette erreur  
  
1.  Supprimez les parenthèses autour de l’argument qui suit `AddressOf`.  
  
2.  Assurez-vous que l’argument est un nom de méthode.  
  
## <a name="see-also"></a>Voir aussi  
 [AddressOf (opérateur)](../../../visual-basic/language-reference/operators/addressof-operator.md)  
 [Délégués](../../../visual-basic/programming-guide/language-features/delegates/index.md)
