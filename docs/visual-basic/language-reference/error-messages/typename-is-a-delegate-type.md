---
title: "«&lt;typename&gt;&quot; est un type délégué | Documents Microsoft"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- bc32008
- vbc32008
dev_langs:
- VB
helpviewer_keywords:
- BC32008
ms.assetid: dc6abba0-a9ad-450f-8899-87265bc84abc
caps.latest.revision: 11
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
ms.openlocfilehash: 3d6cc283f7e9815eb9b723a450731998f14b3424
ms.lasthandoff: 03/13/2017

---
# <a name="39lttypenamegt39-is-a-delegate-type"></a>«&lt;typename&gt;' est un type délégué
«\<typename >' est un type délégué. Une construction déléguée accepte une seule expression AddressOf en tant que liste d’arguments. Une expression AddressOf peut souvent être utilisée au lieu d’une construction déléguée.  
  
 Un `New` clause crée une instance d’une classe déléguée fournit une liste d’arguments non valide au constructeur délégué.  
  
 Vous pouvez fournir une seule `AddressOf` expression lors de la création d’une nouvelle instance de délégué.  
  
 Cette erreur peut se produire si vous ne passez pas d’arguments au constructeur délégué, si vous passez plusieurs arguments, ou si vous passez un argument unique qui n’est pas valide `AddressOf` expression.  
  
 **ID d’erreur :** BC32008  
  
## <a name="to-correct-this-error"></a>Pour corriger cette erreur  
  
-   Utiliser un seul `AddressOf` expression dans la liste d’arguments pour la classe déléguée dans la `New` clause.  
  
## <a name="see-also"></a>Voir aussi  
 [New, opérateur](../../../visual-basic/language-reference/operators/new-operator.md)   
 [AddressOf (opérateur)](../../../visual-basic/language-reference/operators/addressof-operator.md)   
 [Délégués](../../../visual-basic/programming-guide/language-features/delegates/index.md)   
 [Guide pratique : appeler une méthode déléguée](../../../visual-basic/programming-guide/language-features/delegates/how-to-invoke-a-delegate-method.md)
