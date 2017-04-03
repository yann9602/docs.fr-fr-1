---
title: "Utilisation de structs (Guide de programmation C#) | Microsoft Docs"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
helpviewer_keywords:
- structs [C#], using
ms.assetid: cea4a459-9eb9-442b-8d08-490e0797ba38
caps.latest.revision: 28
author: BillWagner
ms.author: wiwagn
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Human Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 8cb5fa79de38294add5cebdd38537636591de126
ms.lasthandoff: 03/13/2017

---
# <a name="using-structs-c-programming-guide"></a>Utilisation de structs (Guide de programmation C#)
Le type `struct` est approprié pour représenter des objets légers tels que `Point`, `Rectangle`et `Color`. Même s’il est aussi pratique de représenter un point sous la forme d’une [classe](../../../csharp/language-reference/keywords/class.md) avec des [propriétés implémentées automatiquement](../../../csharp/programming-guide/classes-and-structs/auto-implemented-properties.md), un [struct](../../../csharp/language-reference/keywords/struct.md) peut être plus efficace dans certains scénarios. Par exemple, si vous déclarez un tableau de 1 000 objets `Point` , vous devez allouer de la mémoire supplémentaire pour faire référence à chacun des objets. Dans ce cas, un struct est moins onéreux. Étant donné que le [!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort_md.md)] contient un objet appelé <xref:System.Drawing.Point>, le struct utilisé dans cet exemple est nommé "CoOrds" à la place.  
  
 [!code-cs[csProgGuideObjects#1](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/using-structs_1.cs)]  
  
 Définir un constructeur par défaut (sans paramètre) pour un struct constitue une erreur. Vous ne devez pas non plus initialiser un champ d'instance dans le corps d'un struct. Vous pouvez initialiser des membres de struct uniquement en utilisant un constructeur paramétrable ou en accédant individuellement aux membres après que le struct a été déclaré. Tout membre privé (ou inaccessible) peut uniquement être initialisé dans un constructeur.  
  
 Quand vous utilisez l’opérateur [new](../../../csharp/language-reference/keywords/new.md) pour créer un objet struct, ce dernier est créé et le constructeur approprié est appelé. Contrairement aux classes, les structs peuvent être instanciés sans avoir recours à l’opérateur `new` . Dans un tel cas, il n’y a pas d’appel au constructeur, ce qui rend l’allocation plus efficace. Toutefois, les champs ne sont pas assignés et l’objet ne peut pas être utilisé tant que tous les champs ne sont pas initialisés.  
  
 Lorsqu'un struct contient un type référence en tant que membre, le constructeur par défaut du membre doit être appelé explicitement, sinon le membre reste non assigné et le struct ne peut pas être utilisé. (Cela provoque l’erreur du compilateur CS0171.)  
  
 Il n'existe pas d'héritage pour un struct comme il en existe pour une classe. Un struct ne peut pas hériter d'un autre struct ou d'une classe ; il ne peut pas non plus servir de base à une classe. Toutefois, les structs héritent de la classe de base <xref:System.Object>. Un struct peut implémenter des interfaces exactement de la même manière que les classes.  
  
 Vous ne pouvez pas déclarer une classe à l’aide du mot clé `struct`. En C#, les classes et les structs ont une sémantique différente. Un struct est un type valeur, alors qu'une classe est un type référence. Pour plus d’informations, consultez [Types valeur](../../../csharp/language-reference/keywords/value-types.md).  
  
 Sauf si vous avez besoin d’une sémantique de type référence, une petite classe peut être gérée plus efficacement par le système si vous la déclarez plutôt sous forme de struct.  
  
## <a name="example-1"></a>Exemple 1  
  
### <a name="description"></a>Description  
 Cet exemple illustre l’initialisation du type `struct` à l’aide des constructeurs par défaut et des constructeurs paramétrables.  
  
### <a name="code"></a>Code  
 [!code-cs[csProgGuideObjects#1](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/using-structs_1.cs)]  
  
 [!code-cs[csProgGuideObjects#2](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/using-structs_2.cs)]  
  
## <a name="example-2"></a>Exemple 2  
  
### <a name="description"></a>Description  
 Cet exemple montre une caractéristique propre aux structs. Il crée un objet CoOrds sans utiliser l’opérateur `new` . Si vous remplacez le mot `struct` par le mot `class`, le programme ne peut pas se compiler.  
  
### <a name="code"></a>Code  
 [!code-cs[csProgGuideObjects#1](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/using-structs_1.cs)]  
  
 [!code-cs[csProgGuideObjects#3](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/using-structs_3.cs)]  
  
## <a name="see-also"></a>Voir aussi  
 [Guide de programmation C#](../../../csharp/programming-guide/index.md)   
 [Classes et structs](../../../csharp/programming-guide/classes-and-structs/index.md)   
 [Structs](../../../csharp/programming-guide/classes-and-structs/structs.md)
