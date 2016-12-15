---
title: "&#39;&lt;name1&gt;&#39; is ambiguous, imported from the namespaces or types &#39;&lt;name2&gt;&#39; | Microsoft Docs"
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
  - "vbc30561"
  - "bc30561"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "BC30561"
ms.assetid: 761091f7-1018-4299-b481-3966a4a2c126
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;&lt;name1&gt;&#39; is ambiguous, imported from the namespaces or types &#39;&lt;name2&gt;&#39;
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Vous avez fourni un nom ambigu qui entre par conséquent en conflit avec un autre nom.  Le compilateur [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] ne possède aucune règle de résolution de conflit ; vous devez lever vous\-même toute ambiguïté sur les noms.  
  
 **ID d'erreur :** BC30561  
  
### Pour corriger cette erreur  
  
1.  Levez toute ambiguïté sur le nom en supprimant les importations d'espaces de noms.  
  
2.  Qualifiez le nom de manière complète.  
  
## Voir aussi  
 [Imports Statement \(.NET Namespace and Type\)](../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md)   
 [Espaces de noms dans Visual Basic](../../../visual-basic/programming-guide/program-structure/namespaces.md)   
 [Namespace Statement](../../../visual-basic/language-reference/statements/namespace-statement.md)