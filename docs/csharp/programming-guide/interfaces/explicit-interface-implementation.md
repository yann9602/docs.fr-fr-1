---
title: "Implémentation d’interface explicite (Guide de programmation C#)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
helpviewer_keywords:
- explicit interfaces [C#]
- interfaces [C#], explicit
ms.assetid: 181c901f-0d4c-4f29-97fc-895079617bf2
caps.latest.revision: 14
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
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 6baf985e8031e1e859d20570168222ca8f368eff
ms.contentlocale: fr-fr
ms.lasthandoff: 07/28/2017

---
# <a name="explicit-interface-implementation-c-programming-guide"></a>Implémentation d’interface explicite (Guide de programmation C#)
Si une [classe](../../../csharp/language-reference/keywords/class.md) implémente deux interfaces qui contiennent un membre avec la même signature, l’implémentation de ce membre sur la classe a pour conséquence que les deux interfaces utilisent ce membre comme leur implémentation. Dans l’exemple suivant, tous les appels à `Paint` appellent la même méthode.  
  
 [!code-cs[csProgGuideInheritance#39](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/explicit-interface-implementation_1.cs)]  
  
 Toutefois, si les deux membres d’[interface](../../../csharp/language-reference/keywords/interface.md) n’exécutent pas la même fonction, cela peut engendrer une implémentation incorrecte d’une interface ou des deux. Il est possible d’implémenter un membre d’interface explicitement, en créant un membre de classe qui n’est appelé que via l’interface et qui est spécifique à cette interface. Pour ce faire, vous devez nommer le membre de classe avec le nom de l’interface et un point. Exemple :  
  
 [!code-cs[csProgGuideInheritance#40](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/explicit-interface-implementation_2.cs)]  
  
 Le membre de classe `IControl.Paint` est disponible uniquement via l’interface `IControl` et `ISurface.Paint` est disponible uniquement via `ISurface`. Les deux implémentations de méthode sont distinctes, et aucune n’est directement disponible sur la classe. Exemple :  
  
 [!code-cs[csProgGuideInheritance#41](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/explicit-interface-implementation_3.cs)]  
  
 L’implémentation explicite est également utilisée pour résoudre les cas où deux interfaces déclarent chacune des membres différents du même nom, comme une propriété et une méthode :  
  
 [!code-cs[csProgGuideInheritance#42](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/explicit-interface-implementation_4.cs)]  
  
 Pour implémenter les deux interfaces, une classe doit utiliser l’implémentation explicite pour la propriété P, la méthode P, ou les deux, pour éviter une erreur du compilateur. Exemple :  
  
 [!code-cs[csProgGuideInheritance#43](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/explicit-interface-implementation_5.cs)]  
  
## <a name="see-also"></a>Voir aussi  
 [Guide de programmation C#](../../../csharp/programming-guide/index.md)   
 [Classes et structs](../../../csharp/programming-guide/classes-and-structs/index.md)   
 [Interfaces](../../../csharp/programming-guide/interfaces/index.md)   
 [Héritage](../../../csharp/programming-guide/classes-and-structs/inheritance.md)

