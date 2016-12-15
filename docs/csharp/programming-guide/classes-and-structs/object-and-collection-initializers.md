---
title: "Initialiseurs d&#39;objets et de collection (Guide de programmation C#) | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
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
  - "initialiseurs de collections (C#)"
  - "initialiseurs d'objets (C#)"
ms.assetid: c58f3db5-d7d4-4651-bd2d-5a3a97357f61
caps.latest.revision: 27
caps.handback.revision: 27
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Initialiseurs d&#39;objets et de collection (Guide de programmation C#)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Les initialiseurs d'objet vous permettent d'assigner des valeurs aux champs ou propriétés accessibles d'un objet au moment de la création sans avoir à appeler un constructeur suivi de lignes d'instructions d'assignation.  La syntaxe de l'initialiseur de l'objet vous permet de spécifier les arguments d'un constructeur ou de les omettre \(et la syntaxe de parenthèses\).  L'exemple suivant montre comment utiliser l'initialiseur de l'objet de type nommé, `Cat`, et comment appeler le constructeur par défaut.  Notez l'utilisation de propriétés implémentées automatiquement dans la classe `Cat`.  Pour plus d'informations, consultez [Propriétés implémentées automatiquement](../../../csharp/programming-guide/classes-and-structs/auto-implemented-properties.md).  
  
 [!code-cs[csProgGuideLINQ#39](../../../csharp/programming-guide/arrays/codesnippet/CSharp/object-and-collection-initializers_1.cs)]  
  
 [!code-cs[csProgGuideLINQ#45](../../../csharp/programming-guide/arrays/codesnippet/CSharp/object-and-collection-initializers_2.cs)]  
  
## Initialiseurs d'objet avec des types anonymes  
 Même si les initialiseurs d'objets peuvent être utilisés dans n'importe quel contexte, ils sont particulièrement utiles dans les expressions de requête [!INCLUDE[vbteclinq](../../../csharp/includes/vbteclinq_md.md)].  Les expressions de requête utilisent fréquemment des [types anonymes](../../../csharp/programming-guide/classes-and-structs/anonymous-types.md), et ne peuvent être initialisées qu'à l'aide d'un initialiseur d'objet, comme indiqué dans la déclaration suivante.  
  
```  
var pet = new { Age = 10, Name = "Fluffy" };  
```  
  
 Les types anonymes permettent à la clause `select` d'une expression de requête [!INCLUDE[vbteclinq](../../../csharp/includes/vbteclinq_md.md)] de transformer les objets de la séquence d'origine en objets dont la valeur et la forme peuvent différer de l'original.  Cela s'avère utile si vous souhaitez stocker uniquement une partie des informations de chaque objet d'une séquence.  Dans l'exemple suivant, supposons qu'un objet de produit \(`p`\) contient de nombreux champs et méthodes et que vous souhaitez uniquement créer une séquence d'objets qui contiennent le nom de produit et le prix unitaire.  
  
 [!code-cs[csProgGuideLINQ#40](../../../csharp/programming-guide/arrays/codesnippet/CSharp/object-and-collection-initializers_3.cs)]  
  
 Lorsque cette requête est exécutée, la variable `productInfos` contient une séquence d'objets qui sont accessibles dans une instruction `foreach` comme indiqué dans cet exemple :  
  
```  
foreach(var p in productInfos){...}  
```  
  
 Chaque objet dans le nouveau type anonyme a deux propriétés publiques qui reçoivent les mêmes noms que les propriétés ou champs de l'objet d'origine.  Vous pouvez également renommer un champ lorsque vous créez un type anonyme. L'exemple suivant renomme le champ `UnitPrice` en `Price`.  
  
```  
select new {p.ProductName, Price = p.UnitPrice};  
```  
  
## Initialiseurs d'objets avec les types Nullable  
 C'est une erreur au moment de la compilation que d'utiliser un initialiseur d'objet avec un struct Nullable.  
  
## Initialiseurs de collection  
 Les initialiseurs de collections vous permettent de spécifier un ou plusieurs initialiseurs d'éléments quand vous initialisez une classe de collection qui implémente <xref:System.Collections.IEnumerable> ou une classe liée à une méthode d'extension `Add`.  Les initialiseurs d'élément peuvent être une valeur simple, une expression ou un initialiseur d'objet.  En utilisant un initialiseur de collection, il n'est pas nécessaire de spécifier plusieurs appels à la méthode `Add` de la classe dans votre code source ; le compilateur ajoute les appels.  
  
 Les exemples suivants présentent deux initialiseurs de collection simples :  
  
```  
List<int> digits = new List<int> { 0, 1, 2, 3, 4, 5, 6, 7, 8, 9 };  
List<int> digits2 = new List<int> { 0 + 1, 12 % 3, MakeInt() };  
```  
  
 L'initialiseur de collection suivant utilise des initialiseurs d'objets pour initialiser les objets de la classe `Cat` définis dans un exemple précédent.  Notez que les initialiseurs d'objets individuels sont placés entre accolades et séparés par une virgule.  
  
 [!code-cs[csProgGuideLINQ#41](../../../csharp/programming-guide/arrays/codesnippet/CSharp/object-and-collection-initializers_4.cs)]  
  
 Vous pouvez spécifier [Null](../../../csharp/language-reference/keywords/null.md) comme un élément dans un initialiseur de collection si la méthode `Add` de la collection l'autorise.  
  
 [!code-cs[csProgGuideLINQ#42](../../../csharp/programming-guide/arrays/codesnippet/CSharp/object-and-collection-initializers_5.cs)]  
  
 Vous pouvez spécifier des éléments indexés si la collection prend en charge l'indexation.  
  
```  
var numbers = new Dictionary<int, string> {   
    [7] = "seven",   
    [9] = "nine",   
    [13] = "thirteen"   
};  
  
```  
  
## Exemple  
 [!code-cs[csProgGuideLINQ#46](../../../csharp/programming-guide/arrays/codesnippet/CSharp/object-and-collection-initializers_6.cs)]  
  
## Voir aussi  
 [Guide de programmation C\#](../../../csharp/programming-guide/index.md)   
 [Expressions de requête \(LINQ\)](../../../csharp/programming-guide/linq-query-expressions/index.md)   
 [Types anonymes](../../../csharp/programming-guide/classes-and-structs/anonymous-types.md)