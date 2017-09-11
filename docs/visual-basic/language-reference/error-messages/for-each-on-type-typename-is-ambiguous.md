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
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: 783c741a8acb0d27ef6ff5c52939bd12a026ba74
ms.contentlocale: fr-fr
ms.lasthandoff: 04/12/2017

---
# <a name="39for-each39-on-type-39lttypenamegt39-is-ambiguous-because-the-type-implements-multiple-instantiations-of-39systemcollectionsgenericienumerableof-t39"></a><span data-ttu-id="37dd9-102">'For Each' pour le type '&lt;typename&gt;' est ambigu, car le type implémente plusieurs instanciations de 'System.Collections.Generic.IEnumerable (Of T)'</span><span class="sxs-lookup"><span data-stu-id="37dd9-102">&#39;For Each&#39; on type &#39;&lt;typename&gt;&#39; is ambiguous because the type implements multiple instantiations of &#39;System.Collections.Generic.IEnumerable(Of T)&#39;</span></span>
<span data-ttu-id="37dd9-103">A `For Each` instruction spécifie une variable itérateur qui a plusieurs <xref:System.Collections.IEnumerable.GetEnumerator%2A>méthode.</xref:System.Collections.IEnumerable.GetEnumerator%2A></span><span class="sxs-lookup"><span data-stu-id="37dd9-103">A `For Each` statement specifies an iterator variable that has more than one <xref:System.Collections.IEnumerable.GetEnumerator%2A> method.</span></span>  
  
 <span data-ttu-id="37dd9-104">La variable itérateur doit être d’un type qui implémente le <xref:System.Collections.IEnumerable?displayProperty=fullName>ou <xref:System.Collections.Generic.IEnumerable%601?displayProperty=fullName>interface dans un de le `Collections` espaces de noms de la [!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort_md.md)].</xref:System.Collections.Generic.IEnumerable%601?displayProperty=fullName> </xref:System.Collections.IEnumerable?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="37dd9-104">The iterator variable must be of a type that implements the <xref:System.Collections.IEnumerable?displayProperty=fullName> or <xref:System.Collections.Generic.IEnumerable%601?displayProperty=fullName> interface in one of the `Collections` namespaces of the [!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort_md.md)].</span></span> <span data-ttu-id="37dd9-105">Il est possible qu’une classe implémente plusieurs interfaces génériques construites, à l’aide d’un argument de type différent pour chaque construction.</span><span class="sxs-lookup"><span data-stu-id="37dd9-105">It is possible for a class to implement more than one constructed generic interface, using a different type argument for each construction.</span></span> <span data-ttu-id="37dd9-106">Si une classe qui effectue cette opération est utilisée pour la variable itérateur, cette dernière a plusieurs <xref:System.Collections.IEnumerable.GetEnumerator%2A>méthode.</xref:System.Collections.IEnumerable.GetEnumerator%2A></span><span class="sxs-lookup"><span data-stu-id="37dd9-106">If a class that does this is used for the iterator variable, that variable has more than one <xref:System.Collections.IEnumerable.GetEnumerator%2A> method.</span></span> <span data-ttu-id="37dd9-107">Dans ce cas, [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] ne peut pas choisir la méthode à appeler.</span><span class="sxs-lookup"><span data-stu-id="37dd9-107">In such a case, [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] cannot choose which method to call.</span></span>  
  
 <span data-ttu-id="37dd9-108">**ID d’erreur :** BC32096</span><span class="sxs-lookup"><span data-stu-id="37dd9-108">**Error ID:** BC32096</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="37dd9-109">Pour corriger cette erreur</span><span class="sxs-lookup"><span data-stu-id="37dd9-109">To correct this error</span></span>  
  
-   <span data-ttu-id="37dd9-110">Utilisez [DirectCast, opérateur](../../../visual-basic/language-reference/operators/directcast-operator.md) ou [opérateur TryCast](../../../visual-basic/language-reference/operators/trycast-operator.md) un cast du type de variable itérateur vers l’interface qui définit la <xref:System.Collections.IEnumerable.GetEnumerator%2A>méthode que vous souhaitez utiliser.</xref:System.Collections.IEnumerable.GetEnumerator%2A></span><span class="sxs-lookup"><span data-stu-id="37dd9-110">Use [DirectCast Operator](../../../visual-basic/language-reference/operators/directcast-operator.md) or [TryCast Operator](../../../visual-basic/language-reference/operators/trycast-operator.md) to cast the iterator variable type to the interface defining the <xref:System.Collections.IEnumerable.GetEnumerator%2A> method you want to use.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="37dd9-111">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="37dd9-111">See Also</span></span>  
 <span data-ttu-id="37dd9-112">[For Each... Instruction suivante](../../../visual-basic/language-reference/statements/for-each-next-statement.md) </span><span class="sxs-lookup"><span data-stu-id="37dd9-112">[For Each...Next Statement](../../../visual-basic/language-reference/statements/for-each-next-statement.md) </span></span>  
<span data-ttu-id="37dd9-113"> [Interfaces](../../../visual-basic/programming-guide/language-features/interfaces/index.md)</span><span class="sxs-lookup"><span data-stu-id="37dd9-113"> [Interfaces](../../../visual-basic/programming-guide/language-features/interfaces/index.md)</span></span>
