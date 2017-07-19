---
title: Objets (Guide de programmation C#) | Microsoft Docs
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
helpviewer_keywords:
- objects [C#], about objects
- variables [C#]
ms.assetid: af4a5230-fbf3-4eea-95e1-8b883c2f845c
caps.latest.revision: 26
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
ms.translationtype: Human Translation
ms.sourcegitcommit: a5ed524a1b17f7be8903f998cbd732594faab831
ms.openlocfilehash: fe548eb5d520945e3f0d52750bbf89935947116e
ms.contentlocale: fr-fr
ms.lasthandoff: 05/15/2017

---
# <a name="objects-c-programming-guide"></a>Objets (Guide de programmation C#)
Une définition de classe ou de struct s’apparente à un plan qui spécifie ce que le type peut faire. Un objet est fondamentalement un bloc de mémoire qui a été alloué et configuré selon le plan. Un programme peut créer de nombreux objets de la même classe. Les objets sont également appelés instances. Ils peuvent être stockés dans une variable nommée, dans un tableau ou dans une collection. Le code client est le code qui utilise ces variables pour appeler les méthodes et accéder aux propriétés publiques de l’objet. Dans un langage orienté objet tel que C#, un programme classique se compose de plusieurs objets qui interagissent de façon dynamique.  
  
> [!NOTE]
>  Les types statiques se comportent différemment de ce qui est décrit ici. Pour plus d’informations, consultez [Classes static et membres de classe static](../../../csharp/programming-guide/classes-and-structs/static-classes-and-static-class-members.md).  
  
## <a name="struct-instances-vs-class-instances"></a>Comparaison des instances de struct et des instances de classe  
 Étant donné que les classes sont des types référence, une variable d’un objet de classe conserve une référence à l’adresse de l’objet sur le tas managé. Si un deuxième objet du même type est assigné au premier objet, les deux variables font référence à l’objet à cette adresse. Ce point est abordé en détail plus loin dans cette rubrique.  
  
 Les instances de classes sont créées à l’aide de l’[opérateur new](../../../csharp/language-reference/keywords/new-operator.md). Dans l’exemple suivant, `Person` est le type, et `person1` et `person 2` sont des instances, ou objets, de ce type.  
  
 [!code-cs[csProgGuideStatements#30](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/objects_1.cs)]  
  
 Étant donné que les structs sont des types valeur, une variable d’un objet de struct conserve une copie de l’objet entier. Les instances de structs peuvent également être créées à l’aide de l’opérateur `new`, mais cela n’est pas obligatoire, comme illustré dans l’exemple suivant :  
  
 [!code-cs[csProgGuideStatements#31](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/objects_2.cs)]  
  
 La mémoire pour `p1` et `p2` est allouée sur la pile de threads. Cette mémoire est récupérée avec le type ou la méthode où elle est déclarée. C’est l’une des raisons pour lesquelles les structs sont copiés au moment de l’assignation. En revanche, la mémoire allouée pour une instance de classe est récupérée automatiquement (garbage collection) par le common language runtime quand toutes les références à l’objet sont hors de la portée. Il n’est pas possible de détruire de façon déterministe un objet de classe comme vous pouvez le faire dans C++. Pour plus d’informations sur l’opération de garbage collection dans le [!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort_md.md)], consultez [Garbage collection](../../../standard/garbage-collection/index.md).  
  
> [!NOTE]
>  L’allocation et la libération de mémoire sur le tas managé sont des opérations très optimisées dans le common language runtime. Dans la plupart des cas, il n’y a pas de différence significative sur le plan des performances entre l’allocation d’une instance de classe sur le tas et l’allocation d’une instance de struct sur la pile.  
  
## <a name="object-identity-vs-value-equality"></a>Comparaison de l’égalité de l’identité et des valeurs des objets  
 Quand vous effectuez une comparaison d’égalité entre deux objets, vous devez d’abord décider si vous souhaitez savoir si les deux variables représentent le même objet en mémoire, ou si les valeurs d’un ou de plusieurs de leurs champs sont équivalentes. Si vous projetez de comparer les valeurs, vous devez établir si les objets sont des instances de types valeur (structs) ou de types référence (classes, délégués, tableaux).  
  
-   Pour déterminer si deux instances de classe référencent le même emplacement en mémoire (ce qui signifie qu’elles ont la même *identité*), utilisez la méthode statique <xref:System.Object.Equals%2A>. (<xref:System.Object?displayProperty=fullName> est la classe de base implicite pour tous les types valeur et types référence, y compris les classes et structs définis par l’utilisateur.)  
  
-   Pour déterminer si les champs d’instance dans deux instances de struct ont les mêmes valeurs, utilisez la méthode <xref:System.ValueType.Equals%2A?displayProperty=fullName>. Comme tous les structs héritent implicitement de <xref:System.ValueType?displayProperty=fullName>, vous appelez directement la méthode sur votre objet, comme indiqué dans l’exemple suivant :  
  
 [!code-cs[csProgGuideStatements#32](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/objects_3.cs)]  
  
 L’implémentation <xref:System.ValueType?displayProperty=fullName> de `Equals` utilise la réflexion, car elle doit être en mesure de déterminer la nature des champs dans chaque struct. Quand vous créez vos propres structs, substituez la méthode `Equals` pour fournir un algorithme d’égalité efficace qui est propre à votre type.  
  
-   Pour déterminer si les valeurs des champs dans deux instances de classe sont égales, vous pouvez utiliser la méthode <xref:System.Object.Equals%2A> ou l’[opérateur ==](../../../csharp/language-reference/operators/equality-comparison-operator.md). Toutefois, utilisez-les uniquement si la classe les a substitués ou surchargés pour fournir une définition personnalisée de ce que signifie « égalité » pour les objets de ce type. La classe peut également implémenter l’interface <xref:System.IEquatable%601> ou <xref:System.Collections.Generic.IEqualityComparer%601>. Les deux interfaces fournissent des méthodes qui peuvent être utilisées pour tester l’égalité des valeurs. Quand vous concevez vos propres classes qui substituent `Equals`, suivez les instructions indiquées dans [Guide pratique pour définir l’égalité de valeurs pour un type](../../../csharp/programming-guide/statements-expressions-operators/how-to-define-value-equality-for-a-type.md) et <xref:System.Object.Equals%28System.Object%29?displayProperty=fullName>.  
  
## <a name="related-sections"></a>Rubriques connexes  
 Pour plus d'informations :  
  
-   [Classes](../../../csharp/programming-guide/classes-and-structs/classes.md)  
  
-   [Structs](../../../csharp/programming-guide/classes-and-structs/structs.md)  
  
-   [Constructeurs](../../../csharp/programming-guide/classes-and-structs/constructors.md)  
  
-   [Finaliseurs](../../../csharp/programming-guide/classes-and-structs/destructors.md)  
  
-   [Événements](../../../csharp/programming-guide/events/index.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Guide de programmation C#](../../../csharp/programming-guide/index.md)   
 [object](../../../csharp/language-reference/keywords/object.md)   
 [Héritage](../../../csharp/programming-guide/classes-and-structs/inheritance.md)   
 [class](../../../csharp/language-reference/keywords/class.md)   
 [struct](../../../csharp/language-reference/keywords/struct.md)   
 [new, opérateur](../../../csharp/language-reference/keywords/new-operator.md)   
 [Système de type commun](../../../standard/base-types/common-type-system.md)
