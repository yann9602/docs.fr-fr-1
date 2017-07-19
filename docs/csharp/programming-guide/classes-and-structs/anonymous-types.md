---
title: "Types anonymes (Guide de programmation C#) | Microsoft Docs"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
helpviewer_keywords:
- anonymous types [C#]
- C# Language, anonymous types
ms.assetid: 59c9d7a4-3b0e-475e-b620-0ab86c088e9b
caps.latest.revision: 28
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
ms.sourcegitcommit: 400dfda51d978f35c3995f90840643aaff1b9c13
ms.openlocfilehash: 6a6950680a733b3d99edd54fc9a9cfd0338e513c
ms.contentlocale: fr-fr
ms.lasthandoff: 03/24/2017

---
# <a name="anonymous-types-c-programming-guide"></a>Types anonymes (Guide de programmation C#)
Les types anonymes permettent d'encapsuler un ensemble de propriétés en lecture seule dans un unique objet sans avoir à définir explicitement un type. Le nom du type est généré par le compilateur et n'est pas disponible au niveau du code source. Le type de chaque propriété est déduit par le compilateur.  
  
 Vous créez des types anonymes en utilisant l’opérateur [new](../../../csharp/language-reference/keywords/new.md) avec un initialiseur d’objet. Pour plus d’informations sur les initialiseurs d’objets, consultez [Initialiseurs d’objets et de collections](../../../csharp/programming-guide/classes-and-structs/object-and-collection-initializers.md).  
  
 L'exemple suivant montre un type anonyme qui est initialisé avec deux propriétés nommées `Amount` et `Message`.  
  
```csharp  
var v = new { Amount = 108, Message = "Hello" };  
  
// Rest the mouse pointer over v.Amount and v.Message in the following  
// statement to verify that their inferred types are int and string.  
Console.WriteLine(v.Amount + v.Message);  
```  
  
 Les types anonymes sont en règle générale utilisés dans la clause [select](../../../csharp/language-reference/keywords/select-clause.md) d’une expression de requête pour retourner un sous-ensemble de propriétés de chaque objet dans la séquence source. Pour plus d’informations sur les requêtes, consultez [Expressions de requête LINQ](../../../csharp/programming-guide/linq-query-expressions/index.md).  
  
 Les types anonymes contiennent une ou plusieurs propriétés en lecture seule publiques. Aucun autre type de membres de classe, tels que des méthodes ou des événements, n'est valide. L'expression qui est utilisée pour initialiser une propriété ne peut pas être `null`, une fonction anonyme ou un type pointeur.  
  
 Le scénario le plus courant consiste à initialiser un type anonyme avec les propriétés d'un autre type. Dans l'exemple suivant, une classe existe qui porte le nom `Product`. La classe `Product` comprend des propriétés `Color` et `Price`, ainsi que d'autres propriétés qui ne vous intéressent pas. La variable `products` est une collection d'objets `Product`. La déclaration de type anonyme commence par le mot clé `new`. La déclaration initialise un nouveau type qui utilise uniquement deux propriétés de `Product`. Une quantité réduite de données est ainsi retournée dans la requête.  
  
 Si vous n'indiquez pas les noms de membre dans le type anonyme, le compilateur attribue aux membres de type anonyme le même nom que celui de la propriété utilisée pour les initialiser. Vous devez fournir un nom pour une propriété qui est initialisée avec une expression, comme indiqué dans l'exemple précédent. Dans l'exemple suivant, les noms des propriétés du type anonyme sont `Color` et `Price`.  
  
 [!code-cs[csRef30Features#81](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/anonymous-types_1.cs)]  
  
 Quand vous utilisez un type anonyme pour initialiser une variable, vous déclarez la variable en tant que variable locale implicitement typée en utilisant [var](../../../csharp/language-reference/keywords/var.md). Le nom de type ne peut pas être spécifié dans la déclaration de variable, car seul le compilateur a accès au nom sous-jacent du type anonyme. Pour plus d’informations sur `var`, consultez [Variables locales implicitement typées](../../../csharp/programming-guide/classes-and-structs/implicitly-typed-local-variables.md).  
  
 Vous pouvez créer un tableau d'éléments typés anonymement en associant une variable locale implicitement typée et un tableau typé implicitement, comme indiqué dans l'exemple suivant.  
  
```csharp  
var anonArray = new[] { new { name = "apple", diam = 4 }, new { name = "grape", diam = 1 }};  
```  
  
## <a name="remarks"></a>Remarques  
 Les types anonymes sont des types [class](../../../csharp/language-reference/keywords/class.md) qui dérivent directement d’[object](../../../csharp/language-reference/keywords/object.md) et qui ne peuvent pas être castés en type à l’exception du type [object](../../../csharp/language-reference/keywords/object.md). Le compilateur fournit un nom pour chaque type anonyme, bien que votre application ne puisse pas y accéder. Du point de vue du CLR, un type anonyme n'est pas différent des autres types de référence.  
  
 Si plusieurs initialiseurs d'objet dans un assembly spécifient une séquence de propriétés dans le même ordre et qui sont du même type et portent le même nom, le compilateur traite les objets comme des instances du même type. Elles partagent les mêmes informations de type générées par le compilateur.  
  
 Vous ne pouvez pas déclarer un champ, une propriété, un événement ou le type de retour d'une méthode comme ayant un type anonyme. De même, vous ne pouvez pas déclarer un paramètre formel d'une méthode, d'une propriété, d'un constructeur ou d'un indexeur comme ayant un type anonyme. Pour passer un type anonyme, ou une collection qui contient des types anonymes, en tant qu'argument d'une méthode, vous pouvez déclarer le paramètre comme objet de type. Cependant, cela va à l'encontre de l'objectif du typage fort. Si vous devez stocker les résultats de requête ou les passer en dehors des limites de la méthode, utilisez un struct ordinaire ou une classe au lieu d'un type anonyme.  
  
 Dans la mesure où les méthodes <xref:System.Object.Equals%2A> et <xref:System.Object.GetHashCode%2A> dans les types anonymes sont définies selon les termes des méthodes `Equals` et `GetHashCode` des propriétés, deux instances du même type anonyme sont égales uniquement si toutes leurs propriétés sont égales.  
  
## <a name="see-also"></a>Voir aussi  
 [Guide de programmation C#](../../../csharp/programming-guide/index.md)   
 [Initialiseurs d’objets et de collections](../../../csharp/programming-guide/classes-and-structs/object-and-collection-initializers.md)   
 [Bien démarrer avec LINQ en C#](../../../csharp/programming-guide/concepts/linq/getting-started-with-linq.md)   
 [Expressions de requête LINQ](../../../csharp/programming-guide/linq-query-expressions/index.md)

