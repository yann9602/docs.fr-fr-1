---
title: "checked (r&#233;f&#233;rence C#) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.technology: 
  - "devlang-csharp"
ms.topic: "article"
f1_keywords: 
  - "checked_CSharpKeyword"
  - "checked"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "checked (mot clé C#)"
ms.assetid: 718a1194-988d-48a3-b089-d6ee8bd1608d
caps.latest.revision: 24
author: "BillWagner"
ms.author: "wiwagn"
caps.handback.revision: 24
---
# checked (r&#233;f&#233;rence C#)
Le mot clé `checked` sert à activer explicitement le contrôle de dépassement pour les opérations arithmétiques de type entier et les conversions.  
  
 Par défaut, une expression qui contient uniquement des valeurs constantes provoque une erreur de compilateur si l'expression produit une valeur qui est à l'extérieur de la plage du type de destination.  Si l'expression contient une ou plusieurs valeurs non constantes, le compilateur ne détecte pas le dépassement de capacité.  L'évaluation de l'expression assignée à `i2` dans l'exemple suivant ne provoque pas d'erreur du compilateur.  
  
 [!code-cs[csrefKeywordsChecked#3](../../../csharp/language-reference/keywords/codesnippet/CSharp/checked_1.cs)]  
  
 Par défaut, le dépassement de capacité éventuel au moment de l'exécution de ces expressions non constantes n'est pas vérifié, et elles ne déclenchent pas d'exceptions de dépassement de capacité.  L'exemple précédent affiche \-2,147,483,639 comme somme de deux entiers positifs.  
  
 Le contrôle de dépassement peut être activé par les options du compilateur, la configuration de l'environnement ou l'utilisation du mot clé `checked`.  Les exemples suivants montrent comment utiliser une expression `checked` ou un bloc `checked` pour détecter le dépassement de capacité produit par la somme précédente au moment de l'exécution.  Les deux exemples déclenchent une exception de dépassement de capacité.  
  
 [!code-cs[csrefKeywordsChecked#4](../../../csharp/language-reference/keywords/codesnippet/CSharp/checked_2.cs)]  
  
 Le mot clé [unchecked](../../../csharp/language-reference/keywords/unchecked.md) peut être utilisé pour empêcher la vérification du dépassement de capacité.  
  
## Exemple  
 Cet exemple indique comment utiliser `checked` pour activer la vérification du dépassement au moment de l'exécution.  
  
 [!code-cs[csrefKeywordsChecked#1](../../../csharp/language-reference/keywords/codesnippet/CSharp/checked_3.cs)]  
  
## Spécification du langage C\#  
 [!INCLUDE[CSharplangspec](../../../csharp/language-reference/keywords/includes/csharplangspec-md.md)]  
  
## Voir aussi  
 [Référence C\#](../../../csharp/language-reference/index.md)   
 [Guide de programmation C\#](../../../csharp/programming-guide/index.md)   
 [Mots clés C\#](../../../csharp/language-reference/keywords/index.md)   
 [Checked et unchecked](../../../csharp/language-reference/keywords/checked-and-unchecked.md)   
 [unchecked](../../../csharp/language-reference/keywords/unchecked.md)