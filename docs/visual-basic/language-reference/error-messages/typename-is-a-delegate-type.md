---
title: "&#39; &lt;typename&gt;&#39; est un type délégué"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- bc32008
- vbc32008
helpviewer_keywords: BC32008
ms.assetid: dc6abba0-a9ad-450f-8899-87265bc84abc
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 9428f0ac321b90e36d4d987381ed69b6c968894c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="39lttypenamegt39-is-a-delegate-type"></a>&#39; &lt;typename&gt;&#39; est un type délégué
'\<nom_type >' est un type délégué. Une construction déléguée accepte une seule expression AddressOf en tant que liste d’arguments. Souvent une expression AddressOf peut être utilisée au lieu d’une construction de délégué.  
  
 A `New` clause crée une instance d’une classe déléguée fournit une liste d’arguments non valide au constructeur délégué.  
  
 Vous pouvez fournir une seule `AddressOf` expression lors de la création d’une nouvelle instance de délégué.  
  
 Cette erreur peut se produire si vous ne passez pas d’arguments au constructeur délégué, si vous passez plusieurs arguments, ou si vous passez un argument unique qui n’est pas valide `AddressOf` expression.  
  
 **ID d’erreur :** BC32008  
  
## <a name="to-correct-this-error"></a>Pour corriger cette erreur  
  
-   Utiliser un seul `AddressOf` expression dans la liste d’arguments pour la classe déléguée dans la `New` clause.  
  
## <a name="see-also"></a>Voir aussi  
 [New (opérateur)](../../../visual-basic/language-reference/operators/new-operator.md)  
 [AddressOf (opérateur)](../../../visual-basic/language-reference/operators/addressof-operator.md)  
 [Délégués](../../../visual-basic/programming-guide/language-features/delegates/index.md)  
 [Guide pratique : appeler une méthode déléguée](../../../visual-basic/programming-guide/language-features/delegates/how-to-invoke-a-delegate-method.md)
