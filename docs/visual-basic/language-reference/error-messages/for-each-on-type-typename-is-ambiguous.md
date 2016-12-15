---
title: "&#39;For Each&#39; on type &#39;&lt;typename&gt;&#39; is ambiguous because the type implements multiple instantiations of &#39;System.Collections.Generic.IEnumerable(Of T)&#39; | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vbc32096"
  - "bc32096"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "BC32096"
ms.assetid: ed20d09c-913f-482e-89f8-c0a596c3ec24
caps.latest.revision: 7
caps.handback.revision: 7
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;For Each&#39; on type &#39;&lt;typename&gt;&#39; is ambiguous because the type implements multiple instantiations of &#39;System.Collections.Generic.IEnumerable(Of T)&#39;
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Une instruction `For Each` spécifie une variable itérateur qui a plusieurs méthodes <xref:System.Collections.IEnumerable.GetEnumerator%2A>.  
  
 La variable itérateur doit être d'un type qui implémente l'interface <xref:System.Collections.IEnumerable?displayProperty=fullName> ou <xref:System.Collections.Generic.IEnumerable%601?displayProperty=fullName> dans l'un des espaces de noms `Collections` du [!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort_md.md)].  Une classe peut implémenter plusieurs interfaces génériques construites à l'aide d'un argument de type différent pour chaque construction.  Si une classe qui procède ainsi est utilisée pour la variable itérateur, cette dernière a plusieurs méthodes <xref:System.Collections.IEnumerable.GetEnumerator%2A>.  Dans ce cas, [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] ne peut pas choisir quelle méthode appeler.  
  
 **ID d'erreur :** BC32096  
  
### Pour corriger cette erreur  
  
-   Utilisez [DirectCast Operator](../../../visual-basic/language-reference/operators/directcast-operator.md) ou [TryCast Operator](../../../visual-basic/language-reference/operators/trycast-operator.md) pour effectuer un cast du type de variable itérateur vers l'interface qui définit la méthode <xref:System.Collections.IEnumerable.GetEnumerator%2A> que vous souhaitez utiliser.  
  
## Voir aussi  
 [For Each...Next, instruction](../../../visual-basic/language-reference/statements/for-each-next-statement.md)   
 [Interfaces](../../../visual-basic/programming-guide/language-features/interfaces/index.md)