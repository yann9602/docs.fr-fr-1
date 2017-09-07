---
title: "Génériques et tableaux (guide de programmation C#)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
helpviewer_keywords:
- generics [C#], arrays
- arrays [C#], generics
ms.assetid: 7d956536-3851-41b5-94ad-3e7c0a5fe485
caps.latest.revision: 17
author: BillWagner
ms.author: wiwagn
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
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 46cea2733504e56aec5e65a4c9a8b655bc9431cf
ms.contentlocale: fr-fr
ms.lasthandoff: 07/28/2017

---
# <a name="generics-and-arrays-c-programming-guide"></a>Génériques et tableaux (guide de programmation C#)
En C# 2.0 et versions ultérieures, les tableaux unidimensionnels qui ont une limite inférieure de zéro implémentent automatiquement <xref:System.Collections.Generic.IList%601>. Cela vous permet de créer des méthodes génériques qui peuvent utiliser le même code pour itérer au sein de tableaux et d’autres types de collections. Cette technique est essentiellement utile pour lire les données dans des collections. L’interface <xref:System.Collections.Generic.IList%601> ne peut pas être utilisée pour ajouter ni supprimer des éléments dans un tableau. Une exception est levée si vous essayez d’appeler une méthode <xref:System.Collections.Generic.IList%601> telle que <xref:System.Collections.Generic.IList%601.RemoveAt%2A> sur un tableau dans ce contexte.  
  
 L’exemple de code suivant montre comment une méthode générique seule qui prend un paramètre d’entrée <xref:System.Collections.Generic.IList%601> peut itérer à la fois au sein d’une liste et d’un tableau (en l’occurrence un tableau d’entiers).  
  
 [!code-cs[csProgGuideGenerics#35](../../../csharp/programming-guide/generics/codesnippet/CSharp/generics-and-arrays_1.cs)]  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.Collections.Generic>   
 [Guide de programmation C#](../../../csharp/programming-guide/index.md)   
 [Génériques](../../../csharp/programming-guide/generics/index.md)   
 [Tableaux](../../../csharp/programming-guide/arrays/index.md)   
 [Génériques](~/docs/standard/generics/index.md)

