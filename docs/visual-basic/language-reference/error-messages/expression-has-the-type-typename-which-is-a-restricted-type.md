---
title: "Expression has the type &#39;&lt;typename&gt;&#39; which is a restricted type and cannot be used to access members inherited from &#39;Object&#39; or &#39;ValueType&#39; | Microsoft Docs"
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
  - "bc31393"
  - "vbc31393"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "BC31393"
ms.assetid: 2963cf3f-c527-4aa7-b67c-ee80b6d23186
caps.latest.revision: 6
caps.handback.revision: 6
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Expression has the type &#39;&lt;typename&gt;&#39; which is a restricted type and cannot be used to access members inherited from &#39;Object&#39; or &#39;ValueType&#39;
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Une expression a la valeur d'un type qui ne peut pas être boxed par le common language runtime \(CLR\) mais accède à un membre qui nécessite une conversion boxing.  
  
 *Conversion boxing* fait référence au traitement nécessaire pour convertir un type en `Object` ou, quelquefois, en <xref:System.ValueType>.  Le common language runtime ne peut pas convertir certains types de structure, par exemple <xref:System.ArgIterator>, <xref:System.RuntimeArgumentHandle> et <xref:System.TypedReference>.  
  
 Cette expression tente d'utiliser le type restreint pour appeler une méthode héritée de <xref:System.Object> ou de <xref:System.ValueType>, comme <xref:System.Object.GetHashCode%2A> ou <xref:System.Object.ToString%2A>.  Pour accéder à cette méthode, [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] a tenté une conversion boxing implicite qui provoque cette erreur.  
  
 **ID d'erreur :** BC31393  
  
### Pour corriger cette erreur  
  
1.  Localisez l'expression qui a la valeur du type cité.  
  
2.  Localisez la partie de votre instruction qui essaie d'appeler la méthode héritée de <xref:System.Object> ou de <xref:System.ValueType>.  
  
3.  Réécrivez l'instruction pour éviter l'appel de méthode.  
  
## Voir aussi  
 [Implicit and Explicit Conversions](../../../visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md)