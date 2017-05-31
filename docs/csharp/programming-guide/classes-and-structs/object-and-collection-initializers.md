---
title: "Initialiseurs d’objet et de collection (Guide de programmation C#) | Microsoft Docs"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
helpviewer_keywords:
- object initializers [C#]
- collection initializers [C#]
ms.assetid: c58f3db5-d7d4-4651-bd2d-5a3a97357f61
caps.latest.revision: 27
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
ms.sourcegitcommit: 66045a6902e64db394a1f5812658e25a11692027
ms.openlocfilehash: a4d0e8f348afdf1793804a4062be45d2fb4e7e2b
ms.contentlocale: fr-fr
ms.lasthandoff: 04/21/2017

---
# <a name="object-and-collection-initializers-c-programming-guide"></a>Initialiseurs d’objet et de collection (Guide de programmation C#)
Les initialiseurs d'objet vous permettent d'affecter des valeurs aux champs ou propriétés accessibles d'un objet, au moment de sa création, sans devoir appeler un constructeur suivi de ses lignes d'instructions d'assignation. La syntaxe de l'initialiseur de l'objet vous permet de spécifier les arguments d'un constructeur ou de les omettre (et la syntaxe de parenthèses).  L'exemple suivant montre comment utiliser l'initialiseur de l'objet de type nommé, `Cat`, et comment appeler le constructeur par défaut. Notez l'utilisation de propriétés implémentées automatiquement dans la classe `Cat`. Pour plus d’informations, consultez [Propriétés implémentées automatiquement](../../../csharp/programming-guide/classes-and-structs/auto-implemented-properties.md).  
  
 [!code-cs[csProgGuideLINQ#39](../../../csharp/programming-guide/arrays/codesnippet/CSharp/object-and-collection-initializers_1.cs)]  
  
 [!code-cs[csProgGuideLINQ#45](../../../csharp/programming-guide/arrays/codesnippet/CSharp/object-and-collection-initializers_2.cs)]  
  
## <a name="object-initializers-with-anonymous-types"></a>Initialiseurs d'objet avec des types anonymes  
 Les initialiseurs d’objet peuvent être utilisés dans tous les contextes, mais ils sont particulièrement utiles dans les expressions de requête [!INCLUDE[vbteclinq](../../../csharp/includes/vbteclinq_md.md)]. Les expressions de requête utilisent souvent des [types anonymes](../../../csharp/programming-guide/classes-and-structs/anonymous-types.md), qui peuvent uniquement être initialisés à l’aide d’un initialiseur d’objet, comme indiqué dans la déclaration suivante.  
  
```csharp
var pet = new { Age = 10, Name = "Fluffy" };  
```  
  
 Les types anonymes permettent à la clause `select` d’une expression de requête [!INCLUDE[vbteclinq](../../../csharp/includes/vbteclinq_md.md)] de transformer les objets de la séquence d’origine en objets dont la valeur et la forme peuvent différer de l’original. Cela s'avère utile si vous souhaitez stocker uniquement une partie des informations de chaque objet d'une séquence. Dans l'exemple suivant, supposons qu'un objet de produit (`p`) contient de nombreux champs et méthodes et que vous souhaitez uniquement créer une séquence d'objets qui contiennent le nom de produit et le prix unitaire.  
  
 [!code-cs[csProgGuideLINQ#40](../../../csharp/programming-guide/arrays/codesnippet/CSharp/object-and-collection-initializers_3.cs)]  
  
 Lorsque cette requête est exécutée, la variable `productInfos` contient une séquence d'objets qui sont accessibles dans une instruction `foreach` comme indiqué dans cet exemple :  
  
```csharp
foreach(var p in productInfos){...}  
```  
  
 Chaque objet dans le nouveau type anonyme a deux propriétés publiques qui reçoivent les mêmes noms que les propriétés ou champs de l'objet d'origine. Vous pouvez également renommer un champ lorsque vous créez un type anonyme. L'exemple suivant renomme le champ `UnitPrice` en `Price`.  
  
```csharp
select new {p.ProductName, Price = p.UnitPrice};  
```  
  
## <a name="object-initializers-with-nullable-types"></a>Initialiseurs d'objets avec les types Nullable  
 C'est une erreur au moment de la compilation que d'utiliser un initialiseur d'objet avec un struct Nullable.  
  
## <a name="collection-initializers"></a>Initialiseurs de collection  
 Les initialiseurs de collection vous permettent de spécifier un ou plusieurs initialiseurs d’élément quand vous initialisez un type de collection qui implémente <xref:System.Collections.IEnumerable> et qui utilise `Add` comme méthode d’instance ou méthode d’extension avec la signature appropriée. Les initialiseurs d'élément peuvent être une valeur simple, une expression ou un initialiseur d'objet. En utilisant un initialiseur de collection, il n'est pas nécessaire de spécifier plusieurs appels à la méthode `Add` de la classe dans votre code source ; le compilateur ajoute les appels.  
  
 Les exemples suivants présentent deux initialiseurs de collection simples :  
  
```csharp
List<int> digits = new List<int> { 0, 1, 2, 3, 4, 5, 6, 7, 8, 9 };  
List<int> digits2 = new List<int> { 0 + 1, 12 % 3, MakeInt() };  
```  
  
 L'initialiseur de collection suivant utilise des initialiseurs d'objets pour initialiser les objets de la classe `Cat` définis dans un exemple précédent. Notez que les initialiseurs d'objets individuels sont placés entre accolades et séparés par une virgule.  
  
 [!code-cs[csProgGuideLINQ#41](../../../csharp/programming-guide/arrays/codesnippet/CSharp/object-and-collection-initializers_4.cs)]  
  
 Vous pouvez spécifier [Null](../../../csharp/language-reference/keywords/null.md) comme élément dans un initialiseur de collection si la méthode `Add` de la collection l’autorise.  
  
 [!code-cs[csProgGuideLINQ#42](../../../csharp/programming-guide/arrays/codesnippet/CSharp/object-and-collection-initializers_5.cs)]  
  
 Vous pouvez spécifier des éléments indexés si la collection prend en charge l’indexation.  
  
```csharp
var numbers = new Dictionary<int, string> {   
    [7] = "seven",   
    [9] = "nine",   
    [13] = "thirteen"   
};  
```  
  
## <a name="example"></a>Exemple  
 [!code-cs[csProgGuideLINQ#46](../../../csharp/programming-guide/arrays/codesnippet/CSharp/object-and-collection-initializers_6.cs)]  
  
## <a name="see-also"></a>Voir aussi  
 [Guide de programmation C#](../../../csharp/programming-guide/index.md)   
 [Expressions de requête LINQ](../../../csharp/programming-guide/linq-query-expressions/index.md)   
 [Types anonymes](../../../csharp/programming-guide/classes-and-structs/anonymous-types.md)

