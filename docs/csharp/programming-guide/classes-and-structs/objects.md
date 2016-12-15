---
title: "Objets (Guide de programmation C#) | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "objets (C#), à propos des objets"
  - "variables (C#)"
ms.assetid: af4a5230-fbf3-4eea-95e1-8b883c2f845c
caps.latest.revision: 26
caps.handback.revision: 26
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Objets (Guide de programmation C#)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Une définition de classe ou de struct ressemble à un plan qui spécifie ce que le type peut faire.  Un objet est fondamentalement un bloc de mémoire qui a été alloué et configuré en fonction du plan.  Un programme peut créer de nombreux objets de la même classe.  Les objets sont également appelés instances, et ils peuvent être stockés dans une variable nommée, dans un tableau ou dans une collection.  Le code client est le code qui utilise ces variables pour appeler les méthodes et accéder aux propriétés publiques de l'objet.  Dans un langage orienté objet tel que C\#, un programme classique se compose de plusieurs objets qui interagissent dynamiquement.  
  
> [!NOTE]
>  Les types statiques se comportent différemment de ce qui est décrit ici.  Pour plus d’informations, consultez [Classes statiques et membres de classe statique](../../../csharp/programming-guide/classes-and-structs/static-classes-and-static-class-members.md).  
  
## Instances de struct VS. des instances de classe  
 Parce que les classes sont des types référence, une variable d'objet de classe maintient une référence à l'adresse de l'objet sur le tas managé.  Si un deuxième objet du même type est assigné au premier objet, les deux variables font référence à l'objet à cette adresse.  Ce point est abordé plus en détail ultérieurement dans cette rubrique.  
  
 Les instances de classes sont créées à l'aide du [nouvel opérateur](../../../csharp/language-reference/keywords/new-operator.md).  Dans l'exemple suivant, `Person` est le type et `person1` et `person 2` sont des instances, ou objets, de ce type.  
  
 [!code-cs[csProgGuideStatements#30](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/objects_1.cs)]  
  
 Parce que les structs sont des types valeur, une variable d'objet de struct conserve une copie de l'objet entier.  Les instances de structs peuvent également être créées à l'aide de l'opérateur `new`, mais cela n'est pas obligatoire, comme illustré dans l'exemple suivant :  
  
 [!code-cs[csProgGuideStatements#31](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/objects_2.cs)]  
  
 La mémoire pour `p1` et `p2` est allouée sur la pile des threads.  Cette mémoire est récupérée avec le type ou la méthode dans laquelle elle est déclarée.  C'est l'une des raisons pour lesquelles les structs sont copiés lors de l'assignation.  Par contraste, la mémoire allouée pour une instance de classe est récupérée automatiquement \(par le garbage collector\) par le Common Language Runtime lorsque toutes les références à l'objet sont sorties de la portée.  Il n'est pas possible de détruire de façon déterministe un objet de classe comme cela est possible en C\+\+.  Pour plus d'informations sur le garbage collection dans [!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort_md.md)], consultez [Garbage Collection](../Topic/Garbage%20Collection.md).  
  
> [!NOTE]
>  L'allocation et la désallocation de mémoire sur le tas managé sont très optimisées dans le common language runtime.  Dans la plupart des cas, il n'y a aucune différence significative de performances entre l'allocation d'une instance de classe sur le tas et l'allocation d'une instance de struct sur la pile.  
  
## Identité de l'objet VS. l'égalité des valeurs  
 Lorsque vous comparez deux objets pour l'égalité, vous devez distinguer en premier si vous souhaitez savoir si les deux variables représentent le même objet en mémoire, ou si les valeurs d'un ou plusieurs de leurs champs sont équivalentes.  Si vous projetez de comparer des valeurs, vous devez savoir si les objets sont des instances de types valeur \(structs\) ou types référence \(classes, délégués, tableaux\).  
  
-   Pour déterminer si deux instances de classe font référence au même emplacement en mémoire \(ce qui signifie qu'ils ont la même *identité*\), utilisez la méthode <xref:System.Object.Equals%2A> statique.  \(<xref:System.Object?displayProperty=fullName> est la classe de base implicite pour tous les types valeur et types référence, y compris les structs et les classes définis par l'utilisateur.\)  
  
-   Pour déterminer si les champs d'instance dans deux instances de struct ont les mêmes valeurs, utilisez la méthode <xref:System.ValueType.Equals%2A?displayProperty=fullName>.  Étant donné que tous les structs héritent implicitement de <xref:System.ValueType?displayProperty=fullName>, vous appelez directement la méthode sur votre objet comme indiqué dans l'exemple suivant :  
  
 [!code-cs[csProgGuideStatements#32](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/objects_3.cs)]  
  
 L'implémentation <xref:System.ValueType?displayProperty=fullName> de `Equals` utilise la réflexion parce qu'elle doit être en mesure de déterminer la nature des champs dans tout struct.  Lorsque vous créez vos propres structs, remplacez la méthode `Equals` pour fournir un algorithme d'égalité efficace et spécifique à votre type.  
  
-   Pour déterminer si les valeurs des champs dans deux instances de classe sont égales, vous pouvez utiliser la méthode <xref:System.Object.Equals%2A> ou l'[opérateur \=\=](../../../csharp/language-reference/operators/equality-comparison-operator.md) \(page éventuellement en anglais\).  Toutefois, ne les utilisez que si la classe les a remplacés ou surchargés pour fournir une définition personnalisée de ce que signifie « égalité » pour les objets de ce type.  La classe peut également implémenter l'interface <xref:System.IEquatable%601> ou l'interface <xref:System.Collections.Generic.IEqualityComparer%601>.  Les deux interfaces fournissent des méthodes qui peuvent être utilisées pour tester l'égalité des valeurs.  Lorsque vous concevez vos propres classes qui remplacent `Equals`, veillez à suivre les instructions indiquées dans [Comment : définir une égalité de valeurs pour un type](../../../csharp/programming-guide/statements-expressions-operators/how-to-define-value-equality-for-a-type.md) et <xref:System.Object.Equals%28System.Object%29?displayProperty=fullName>.  
  
## Rubriques connexes  
 Pour plus d'informations :  
  
-   [Classes](../../../csharp/programming-guide/classes-and-structs/classes.md)  
  
-   [Structures](../../../csharp/programming-guide/classes-and-structs/structs.md)  
  
-   [Constructeurs](../../../csharp/programming-guide/classes-and-structs/constructors.md)  
  
-   [Destructeurs](../../../csharp/programming-guide/classes-and-structs/destructors.md)  
  
-   [Événements](../../../csharp/programming-guide/events/index.md)  
  
## Voir aussi  
 [Guide de programmation C\#](../../../csharp/programming-guide/index.md)   
 [objet](../../../csharp/language-reference/keywords/object.md)   
 [Héritage](../../../csharp/programming-guide/classes-and-structs/inheritance.md)   
 [classe](../../../csharp/language-reference/keywords/class.md)   
 [struct](../../../csharp/language-reference/keywords/struct.md)   
 [Opérateur new](../../../csharp/language-reference/keywords/new-operator.md)   
 [Système de type commun](../../../standard/base-types/common-type-system.md)