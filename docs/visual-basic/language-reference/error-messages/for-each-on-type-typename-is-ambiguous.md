---
title: "&quot;For Each&quot; pour le type &quot;&lt;typename&gt;&quot; est ambigu, car le type implémente plusieurs instanciations de &quot;System.Collections.Generic.IEnumerable (Of T)&quot; | Documents Microsoft"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vbc32096
- bc32096
dev_langs:
- VB
helpviewer_keywords:
- BC32096
ms.assetid: ed20d09c-913f-482e-89f8-c0a596c3ec24
caps.latest.revision: 7
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
ms.openlocfilehash: 6177b48cdc3bc4085cecb6d73c164684ef1c0bc6
ms.lasthandoff: 03/13/2017

---
# <a name="39for-each39-on-type-39lttypenamegt39-is-ambiguous-because-the-type-implements-multiple-instantiations-of-39systemcollectionsgenericienumerableof-t39"></a>'For Each' pour le type '&lt;typename&gt;' est ambigu, car le type implémente plusieurs instanciations de 'System.Collections.Generic.IEnumerable (Of T)'
A `For Each` instruction spécifie une variable itérateur qui a plusieurs <xref:System.Collections.IEnumerable.GetEnumerator%2A>méthode.</xref:System.Collections.IEnumerable.GetEnumerator%2A>  
  
 La variable itérateur doit être d’un type qui implémente le <xref:System.Collections.IEnumerable?displayProperty=fullName>ou <xref:System.Collections.Generic.IEnumerable%601?displayProperty=fullName>interface dans un de le `Collections` espaces de noms de la [!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort_md.md)].</xref:System.Collections.Generic.IEnumerable%601?displayProperty=fullName> </xref:System.Collections.IEnumerable?displayProperty=fullName> Il est possible qu’une classe implémente plusieurs interfaces génériques construites, à l’aide d’un argument de type différent pour chaque construction. Si une classe qui effectue cette opération est utilisée pour la variable itérateur, cette dernière a plusieurs <xref:System.Collections.IEnumerable.GetEnumerator%2A>méthode.</xref:System.Collections.IEnumerable.GetEnumerator%2A> Dans ce cas, [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] ne peut pas choisir la méthode à appeler.  
  
 **ID d’erreur :** BC32096  
  
## <a name="to-correct-this-error"></a>Pour corriger cette erreur  
  
-   Utilisez [DirectCast, opérateur](../../../visual-basic/language-reference/operators/directcast-operator.md) ou [opérateur TryCast](../../../visual-basic/language-reference/operators/trycast-operator.md) un cast du type de variable itérateur vers l’interface qui définit la <xref:System.Collections.IEnumerable.GetEnumerator%2A>méthode que vous souhaitez utiliser.</xref:System.Collections.IEnumerable.GetEnumerator%2A>  
  
## <a name="see-also"></a>Voir aussi  
 [For Each... Instruction suivante](../../../visual-basic/language-reference/statements/for-each-next-statement.md)   
 [Interfaces](../../../visual-basic/programming-guide/language-features/interfaces/index.md)
