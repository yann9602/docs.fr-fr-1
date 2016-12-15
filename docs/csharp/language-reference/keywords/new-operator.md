---
title: "new, op&#233;rateur (r&#233;f&#233;rence C#) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
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
  - "opérateur new (mot clé C#)"
ms.assetid: a212b697-a79b-4105-9923-1f7b108036e8
caps.latest.revision: 22
caps.handback.revision: 22
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# new, op&#233;rateur (r&#233;f&#233;rence C#)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Utilisé pour créer des objets et appeler des constructeurs.  Par exemple :  
  
```  
Class1 obj  = new Class1();  
```  
  
 Il est également utilisé pour créer des instances de types anonymes.  
  
```  
var query = from cust in customers  
            select new {Name = cust.Name, Address = cust.PrimaryAddress};  
```  
  
 L'opérateur `new` est également utilisé pour appeler le constructeur par défaut des types valeur.  Par exemple :  
  
```  
int i = new int();  
```  
  
 Dans l'instruction précédente, `i` est initialisé sur la valeur `0`, qui correspond à la valeur par défaut pour le type `int`.  L'instruction produit le même résultat que ce qui suit :  
  
```  
int i = 0;  
```  
  
 Pour obtenir une liste exhaustive des valeurs par défaut, consultez [Tableau des valeurs par défaut](../../../csharp/language-reference/keywords/default-values-table.md).  
  
 N'oubliez pas que déclarer un constructeur par défaut pour un [struct](../../../csharp/language-reference/keywords/struct.md) est une erreur, car chaque type valeur a implicitement un constructeur public par défaut.  Il est possible de déclarer des constructeurs paramétrés sur un type struct pour définir ses valeurs initiales, mais cela est nécessaire uniquement si les valeurs autres que la valeur par défaut sont requises.  
  
 Les objets de type valeur tels que les structs sont créés sur la pile, tandis que les objets de type référence tels que les classes sont créés sur le tas.  Les deux types d'objets sont détruits automatiquement, mais les objets basés sur les types valeur sont détruits lorsqu'ils sortent de portée, alors que les objets basés sur des types référence sont détruits à un moment non spécifié après la suppression de la dernière référence.  Pour les types référence qui consomment des ressources fixes telles que de grandes quantités de mémoire, des handles de fichiers ou des connexions réseau, il est quelquefois préférable d'employer la finalisation déterministe pour s'assurer que l'objet est détruit dès que possible.  Pour plus d'informations, consultez [using, instruction](../../../csharp/language-reference/keywords/using-statement.md).  
  
 L'opérateur `new` ne peut pas être surchargé.  
  
 Si l'opérateur `new` échoue lors de l'allocation de mémoire, il lève l'exception, <xref:System.OutOfMemoryException>.  
  
## Exemple  
 Dans l'exemple suivant, un objet de `struct` et un objet de classe sont créés et initialisés à l'aide de l'opérateur `new`, puis des valeurs leur sont attribuées.  Les valeurs par défaut et les valeurs attribuées sont affichées.  
  
 [!code-cs[csrefKeywordsOperator#7](../../../csharp/language-reference/keywords/codesnippet/CSharp/new-operator_1.cs)]  
  
 Notez dans l'exemple que la valeur par défaut d'une chaîne est `null`.  C'est pourquoi elle n'est pas affichée.  
  
## Spécification du langage C\#  
 [!INCLUDE[CSharplangspec](../../../csharp/language-reference/keywords/includes/csharplangspec_md.md)]  
  
## Voir aussi  
 [Référence C\#](../../../csharp/language-reference/index.md)   
 [Guide de programmation C\#](../../../csharp/programming-guide/index.md)   
 [Mots clés C\#](../../../csharp/language-reference/keywords/index.md)   
 [Mots clés des opérateurs](../../../csharp/language-reference/keywords/operator-keywords.md)   
 [new](../../../csharp/language-reference/keywords/new.md)   
 [Types anonymes](../../../csharp/programming-guide/classes-and-structs/anonymous-types.md)