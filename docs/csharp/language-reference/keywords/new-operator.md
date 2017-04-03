---
title: "new, opérateur (référence C#) | Microsoft Docs"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
helpviewer_keywords:
- new operator keyword [C#]
ms.assetid: a212b697-a79b-4105-9923-1f7b108036e8
caps.latest.revision: 22
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
translationtype: Human Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: f0831bbbaf68c8c9e1e0e2d77ccf18e7c8b42e4a
ms.lasthandoff: 03/13/2017

---
# <a name="new-operator-c-reference"></a>new, opérateur (référence C#)
Cet opérateur s’utilise pour créer des objets et appeler des constructeurs. Exemple :  
  
```  
Class1 obj  = new Class1();  
```  
  
 Il est également utilisé pour créer des instances de types anonymes :  
  
```  
var query = from cust in customers  
            select new {Name = cust.Name, Address = cust.PrimaryAddress};  
```  
  
 L’opérateur `new` est aussi utilisé pour appeler le constructeur par défaut pour les types valeur. Exemple :  
  
```  
int i = new int();  
```  
  
 Dans l’instruction précédente, `i` est initialisé à `0`, qui est la valeur par défaut pour le type `int`. L’instruction produit le même résultat que ce qui suit :  
  
```  
int i = 0;  
```  
  
 Pour obtenir une liste complète des valeurs par défaut, consultez [Tableau des valeurs par défaut](../../../csharp/language-reference/keywords/default-values-table.md).  
  
 N’oubliez pas qu’il est incorrect de déclarer un constructeur par défaut pour un [struct](../../../csharp/language-reference/keywords/struct.md), car chaque type valeur a implicitement un constructeur public par défaut. Il est possible de déclarer des constructeurs paramétrables sur un type struct pour définir ses valeurs initiales, mais cela est nécessaire uniquement si d’autres valeurs que la valeur par défaut sont requises.  
  
 Les objets de type valeur tels que les structs sont créés sur la pile, tandis que les objets de type référence tels que les classes sont créés sur le tas. Les deux types d’objets sont détruits automatiquement, mais les objets basés sur des types valeur sont détruits quand ils sortent de la portée, alors que les objets basés sur des types référence sont détruits à n’importe quel moment après la suppression de la dernière référence à ces objets. Pour les types référence qui consomment des ressources fixes telles que de grandes quantités de mémoire, des descripteurs de fichiers ou des connexions réseau, il est parfois préférable d’utiliser la finalisation déterministe pour s’assurer que l’objet est détruit dès que possible. Pour plus d’informations, consultez [using, instruction](../../../csharp/language-reference/keywords/using-statement.md).  
  
 L’opérateur `new` ne peut pas être surchargé.  
  
 Si l’opérateur `new` ne réussit pas à allouer de la mémoire, il lève l’exception <xref:System.OutOfMemoryException>.  
  
## <a name="example"></a>Exemple  
 Dans l’exemple suivant, un objet `struct` et un objet de classe sont créés et initialisés à l’aide de l’opérateur `new`, puis des valeurs leur sont assignées. La valeur par défaut et les valeurs assignées sont affichées.  
  
 [!code-cs[csrefKeywordsOperator#7](../../../csharp/language-reference/keywords/codesnippet/CSharp/new-operator_1.cs)]  
  
 Notez que, dans l’exemple, la valeur par défaut d’une chaîne est `null`. Elle n’est donc pas affichée.  
  
## <a name="c-language-specification"></a>Spécification du langage C#  
 [!INCLUDE[CSharplangspec](../../../csharp/language-reference/keywords/includes/csharplangspec_md.md)]  
  
## <a name="see-also"></a>Voir aussi  
 [Informations de référence sur C#](../../../csharp/language-reference/index.md)   
 [Guide de programmation C#](../../../csharp/programming-guide/index.md)   
 [Mots clés C#](../../../csharp/language-reference/keywords/index.md)   
 [Mots clés des opérateurs](../../../csharp/language-reference/keywords/operator-keywords.md)   
 [new](../../../csharp/language-reference/keywords/new.md)   
 [Types anonymes](../../../csharp/programming-guide/classes-and-structs/anonymous-types.md)
