---
title: "interface (référence C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords: interface_CSharpKeyword
helpviewer_keywords: interface keyword [C#]
ms.assetid: 7da38e81-4f99-4bc5-b07d-c986b687eeba
caps.latest.revision: "29"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: aba9ee66a90216066a47f22e251182caad465818
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="interface-c-reference"></a>interface (référence C#)
Une interface contient uniquement des signatures de [méthodes](../../../csharp/programming-guide/classes-and-structs/methods.md), de [propriétés](../../../csharp/programming-guide/classes-and-structs/properties.md), d’[événements](../../../csharp/programming-guide/events/index.md) ou d’[indexeurs](../../../csharp/programming-guide/indexers/index.md). Une classe ou un struct qui implémente l’interface doit implémenter les membres de l’interface qui sont spécifiés dans la définition de l’interface. Dans l’exemple suivant, la classe `ImplementationClass` doit implémenter une méthode nommée `SampleMethod` qui n’a aucun paramètre et qui retourne `void`.  
  
 Pour plus d’informations et d’exemples, consultez [Interfaces](../../../csharp/programming-guide/interfaces/index.md).  
  
## <a name="example"></a>Exemple  
 [!code-csharp[csrefKeywordsTypes#14](../../../csharp/language-reference/keywords/codesnippet/CSharp/interface_1.cs)]  
  
 Une interface peut être membre d’un espace de noms ou d’une classe, et peut contenir les signatures des membres suivants :  
  
-   [Méthodes](../../../csharp/programming-guide/classes-and-structs/methods.md)  
  
-   [Propriétés](../../../csharp/programming-guide/classes-and-structs/using-properties.md)  
  
-   [Indexeurs](../../../csharp/programming-guide/indexers/using-indexers.md)  
  
-   [Événements](../../../csharp/language-reference/keywords/event.md)  
  
 Une interface peut hériter d’une ou de plusieurs interfaces de base.  
  
 Lorsqu’une liste de types de base contient une classe de base et des interfaces, la classe de base doit figurer en premier dans la liste.  
  
 Une classe qui implémente une interface peut implémenter explicitement les membres de cette interface. Un membre implémenté explicitement n’est pas accessible via une instance de classe, mais uniquement via une instance de l’interface.  
  
 Pour plus d’informations et plus d’exemples sur l’implémentation explicite des interfaces, consultez [Implémentation d’interface explicite](../../../csharp/programming-guide/interfaces/explicit-interface-implementation.md).  
  
## <a name="example"></a>Exemple  
 L’exemple suivant montre une implémentation d’interface. Dans cet exemple, l’interface contient la déclaration de propriété, et la classe contient l’implémentation. Toutes les instances d’une classe qui implémentent `IPoint` ont les propriétés entières `x` et `y`.  
  
 [!code-csharp[csrefKeywordsTypes#15](../../../csharp/language-reference/keywords/codesnippet/CSharp/interface_2.cs)]  
  
## <a name="c-language-specification"></a>Spécification du langage C#  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Voir aussi  
 [Référence C#](../../../csharp/language-reference/index.md)  
 [Guide de programmation C#](../../../csharp/programming-guide/index.md)  
 [Mots clés C#](../../../csharp/language-reference/keywords/index.md)  
 [Types référence](../../../csharp/language-reference/keywords/reference-types.md)  
 [Interfaces](../../../csharp/programming-guide/interfaces/index.md)  
 [Utilisation de propriétés](../../../csharp/programming-guide/classes-and-structs/using-properties.md)  
 [Utilisation d’indexeurs](../../../csharp/programming-guide/indexers/using-indexers.md)  
 [class](../../../csharp/language-reference/keywords/class.md)  
 [struct](../../../csharp/language-reference/keywords/struct.md)  
 [Interfaces](../../../csharp/programming-guide/interfaces/index.md)
