---
title: "Interfaces génériques (guide de programmation C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords:
- C# language, generic interfaces
- generics [C#], interfaces
ms.assetid: a8fa49a1-6e78-4a09-87e5-84a0b9f5ffbe
caps.latest.revision: "28"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 0326a7bc459c641cbfafe39fe36525a947051c16
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="generic-interfaces-c-programming-guide"></a>Interfaces génériques (guide de programmation C#)
Il est souvent utile de définir des interfaces pour les classes de collections génériques, ou pour les classes génériques qui représentent des éléments dans la collection. Pour les classes génériques, il est préférable d’utiliser des interfaces génériques, comme <xref:System.IComparable%601> à la place d’<xref:System.IComparable>, pour éviter les opérations de boxing et d’unboxing sur les types valeur. La bibliothèque de classes .NET Framework définit plusieurs interfaces génériques à utiliser avec les classes de collections dans l’espace de noms <xref:System.Collections.Generic>.  
  
 Quand une interface est spécifiée comme une contrainte sur un paramètre de type, seuls les types qui implémentent l’interface peuvent être utilisés. L’exemple de code suivant illustre une classe `SortedList<T>` qui dérive de la classe `GenericList<T>`. Pour plus d’informations, consultez [Introduction aux génériques](../../../csharp/programming-guide/generics/introduction-to-generics.md). `SortedList<T>` ajoute la contrainte `where T : IComparable<T>`. Ceci permet à la méthode `BubbleSort` dans `SortedList<T>` d’utiliser la méthode générique <xref:System.IComparable%601.CompareTo%2A> sur les éléments de liste. Dans cet exemple, les éléments de liste sont une classe simple, `Person`, qui implémente `IComparable<Person>`.  
  
 [!code-csharp[csProgGuideGenerics#29](../../../csharp/programming-guide/generics/codesnippet/CSharp/generic-interfaces_1.cs)]  
  
 Plusieurs interfaces peuvent être spécifiées en tant que contraintes sur un seul type, comme suit :  
  
 [!code-csharp[csProgGuideGenerics#30](../../../csharp/programming-guide/generics/codesnippet/CSharp/generic-interfaces_2.cs)]  
  
 Une interface peut définir plusieurs paramètres de type, comme suit :  
  
 [!code-csharp[csProgGuideGenerics#31](../../../csharp/programming-guide/generics/codesnippet/CSharp/generic-interfaces_3.cs)]  
  
 Les règles d’héritage qui s’appliquent aux classes s’appliquent également aux interfaces :  
  
 [!code-csharp[csProgGuideGenerics#32](../../../csharp/programming-guide/generics/codesnippet/CSharp/generic-interfaces_4.cs)]  
  
 Les interfaces génériques peuvent hériter d’interfaces non génériques si l’interface générique est de type contravariant, ce qui signifie qu’elle utilise uniquement son paramètre de type comme valeur de retour. Dans la bibliothèque de classes .NET Framework, <xref:System.Collections.Generic.IEnumerable%601> hérite d’<xref:System.Collections.IEnumerable>, car <xref:System.Collections.Generic.IEnumerable%601> utilise uniquement `T` dans la valeur de retour de <xref:System.Collections.Generic.IEnumerable%601.GetEnumerator%2A> et dans l’accesseur Get de propriété <xref:System.Collections.Generic.IEnumerator%601.Current%2A>.  
  
 Les classes concrètes peuvent implémenter des interfaces construites fermées, comme suit :  
  
 [!code-csharp[csProgGuideGenerics#33](../../../csharp/programming-guide/generics/codesnippet/CSharp/generic-interfaces_5.cs)]  
  
 Les classes génériques peuvent implémenter des interfaces génériques ou des interfaces construites fermées tant que la liste de paramètres de classe fournit tous les arguments requis par l’interface, comme suit :  
  
 [!code-csharp[csProgGuideGenerics#34](../../../csharp/programming-guide/generics/codesnippet/CSharp/generic-interfaces_6.cs)]  
  
 Les règles qui déterminent la surcharge des méthodes sont les mêmes pour les méthodes dans les classes génériques, les structs génériques ou les interfaces génériques. Pour plus d’informations, consultez [Méthodes génériques](../../../csharp/programming-guide/generics/generic-methods.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Guide de programmation C#](../../../csharp/programming-guide/index.md)  
 [Introduction aux génériques](../../../csharp/programming-guide/generics/introduction-to-generics.md)  
 [interface](../../../csharp/language-reference/keywords/interface.md)  
 [Génériques](~/docs/standard/generics/index.md)
