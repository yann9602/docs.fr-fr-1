---
title: "Comment&#160;: diff&#233;rencier le passage d&#39;un struct et le passage d&#39;une r&#233;f&#233;rence de classe &#224; une m&#233;thode (Guide de programmation C#) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.technology: 
  - "devlang-csharp"
ms.topic: "article"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "méthodes (C#), passer des classes par rapport à des structs"
  - "passer des paramètres (C#), structs et classes"
  - "structures (C#), passer en tant que paramètre de la méthode"
ms.assetid: 9c1313a6-32a8-4ea7-a59f-450f66af628b
caps.latest.revision: 25
author: "BillWagner"
ms.author: "wiwagn"
caps.handback.revision: 25
---
# Comment&#160;: diff&#233;rencier le passage d&#39;un struct et le passage d&#39;une r&#233;f&#233;rence de classe &#224; une m&#233;thode (Guide de programmation C#)
l'exemple suivant montre comment passer [struct](../../../csharp/language-reference/keywords/struct.md) à une méthode diffère de passer une instance de [classe](../../../csharp/language-reference/keywords/class.md) à une méthode.  Dans l'exemple, les deux arguments \(struct et instance de classe\) sont passés par valeur, et les deux méthodes modifient la valeur d'un champ de l'argument.  Toutefois, les résultats des deux méthodes ne sont pas identiques car ce qui est passé lorsque vous passez un struct diffère de celui qui est passé lorsque vous passez une instance d'une classe.  
  
 Étant donné qu'un struct est [type valeur](../../../csharp/language-reference/keywords/value-types.md), lorsque vous [passez une structure par valeur](../../../csharp/programming-guide/classes-and-structs/passing-value-type-parameters.md) à une méthode, la méthode reçoit et traite une copie de l'argument de structure.  La méthode n'a pas accès au structure d'origine dans la méthode d'appel et ne peut donc pas la modifier de quelque manière que ce soit.  La méthode peut uniquement modifier la copie.  
  
 une instance de classe est [type référence](../../../csharp/language-reference/keywords/reference-types.md), pas un type valeur.  Lorsque [un type référence est passé par valeur](../../../csharp/programming-guide/classes-and-structs/passing-reference-type-parameters.md) à une méthode, la méthode reçoit une copie de la référence à l'instance de classe.  Autrement dit, la méthode reçoit une copie de l'adresse de l'instance, pas une copie de l'instance elle\-même.  L'instance de la classe dans la méthode d'appel a une adresse, le paramètre dans la méthode appelée une copie de l'adresse, et les deux adresses renvoient au même objet.  Étant donné que le paramètre contient une seule copie de l'adresse, la méthode appelée ne peut pas modifier l'adresse de l'instance de la classe dans la méthode.  Toutefois, la méthode appelée peut utiliser l'adresse pour accéder aux membres de classe que les deux l'adresse d'origine et la copie est référencé.  Si la méthode appelée modifie un membre de classe, l'instance de la classe d'origine dans la méthode d'appel change également.  
  
 la sortie de l'exemple suivant illustre la différence.  La valeur du champ d' `willIChange` de l'instance de classe est modifiée par l'appel à la méthode `ClassTaker` car la méthode utilise l'adresse dans le paramètre pour rechercher le champ spécifié de l'instance de classe.  Le champ d' `willIChange` de la structure dans la méthode d'appel n'est modifié par un appel à la méthode `StructTaker` parce que la valeur de l'argument est une copie de la structure elle\-même, pas une copie de son adresse.  `StructTaker` modifie la copie, et la copie est perdue dès que l'appel à `StructTaker` est terminé.  
  
## Exemple  
 [!code-cs[csProgGuideObjects#32](../../../csharp/programming-guide/classes-and-structs/codesnippet/csharp/how-to-know-the-differen_1.cs)]  
  
## Voir aussi  
 [Guide de programmation C\#](../../../csharp/programming-guide/index.md)   
 [Classes](../../../csharp/programming-guide/classes-and-structs/classes.md)   
 [Structures](../../../csharp/programming-guide/classes-and-structs/structs.md)   
 [Passage de paramètres](../../../csharp/programming-guide/classes-and-structs/passing-parameters.md)