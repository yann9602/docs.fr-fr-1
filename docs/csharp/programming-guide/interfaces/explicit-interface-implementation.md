---
title: "Impl&#233;mentation d’interface explicite (Guide de programmation C#) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.technology: 
  - "devlang-csharp"
ms.topic: "article"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "interfaces explicites (C#)"
  - "interfaces [C#], explicites"
ms.assetid: 181c901f-0d4c-4f29-97fc-895079617bf2
caps.latest.revision: 14
author: "BillWagner"
ms.author: "wiwagn"
caps.handback.revision: 14
---
# Impl&#233;mentation d’interface explicite (Guide de programmation C#)
Si une [classe](../../../csharp/language-reference/keywords/class.md) implémente deux interfaces qui contiennent un membre avec la même signature, l'implémentation de ce membre sur la classe fera en sorte que les deux interfaces utilisent ce membre comme leur implémentation.  Dans l'exemple suivant, tous les appels à `Paint` appeler la même méthode.  
  
 [!code-cs[csProgGuideInheritance#39](../../../csharp/programming-guide/classes-and-structs/codesnippet/csharp/explicit-interface-imple_1.cs)]  
  
 Toutefois, si les deux membres d'[interface](../../../csharp/language-reference/keywords/interface.md) n'exécutent pas la même fonction, cela peut engendrer une implémentation incorrecte d'une interface ou des deux.  Il est possible d'implémenter un membre d'interface explicitement, en créant un membre de classe qui n'est appelé qu'à travers l'interface et qui est spécifique à cette interface.  Pour ce faire, vous devez nommer le membre de classe avec le nom de l'interface et un point.  Par exemple :  
  
 [!code-cs[csProgGuideInheritance#40](../../../csharp/programming-guide/classes-and-structs/codesnippet/csharp/explicit-interface-imple_2.cs)]  
  
 Le membre de classe `IControl.Paint` est uniquement disponible à travers l'interface `IControl`, et `ISurface.Paint` est uniquement disponible à travers `ISurface`.  Les deux implémentations de méthode sont distinctes, et aucune n'est directement disponible sur la classe.  Par exemple :  
  
 [!code-cs[csProgGuideInheritance#41](../../../csharp/programming-guide/classes-and-structs/codesnippet/csharp/explicit-interface-imple_3.cs)]  
  
 L'implémentation explicite est également utilisée pour résoudre les cas où deux interfaces déclarent chacune des membres différents du même nom, comme une propriété et une méthode :  
  
 [!code-cs[csProgGuideInheritance#42](../../../csharp/programming-guide/classes-and-structs/codesnippet/csharp/explicit-interface-imple_4.cs)]  
  
 Pour implémenter les deux interfaces, une classe doit utiliser l'implémentation explicite pour la propriété P, la méthode P, ou les deux, pour éviter une erreur du compilateur.  Par exemple :  
  
 [!code-cs[csProgGuideInheritance#43](../../../csharp/programming-guide/classes-and-structs/codesnippet/csharp/explicit-interface-imple_5.cs)]  
  
## Voir aussi  
 [Guide de programmation C\#](../../../csharp/programming-guide/index.md)   
 [Classes et structs](../../../csharp/programming-guide/classes-and-structs/index.md)   
 [Interfaces](../../../csharp/programming-guide/interfaces/index.md)   
 [Héritage](../../../csharp/programming-guide/classes-and-structs/inheritance.md)