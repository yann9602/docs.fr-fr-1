---
title: "Fonctionnalités C# qui prennent en charge LINQ | Microsoft Docs"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
helpviewer_keywords:
- LINQ [C#], features supporting LINQ
ms.assetid: 524b0078-ebfd-45a7-b390-f2ceb9d84797
caps.latest.revision: 23
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
ms.openlocfilehash: f844e967e2abb7ea23e04a797017261e33bb4d75
ms.lasthandoff: 03/13/2017

---
# <a name="c-features-that-support-linq"></a>Fonctionnalités C# qui prennent en charge LINQ
La section suivante présente de nouvelles constructions de langage qui sont apparues avec C# 3.0. Même si ces nouvelles fonctionnalités sont toutes plus ou moins utilisées avec les requêtes [!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq_md.md)], elles ne sont pas limitées à [!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq_md.md)] et peuvent être utilisées dans n’importe quel contexte.  
  
## <a name="query-expressions"></a>Expressions de requête  
 Les expressions de requête utilisent une syntaxe déclarative similaire à SQL ou XQuery pour interroger les collections IEnumerable. Au moment de la compilation, la syntaxe de requête est convertie en appels de méthode à l’implémentation de méthodes d’extension d’opérateur de requête standard d’un fournisseur [!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq_md.md)]. Les applications contrôlent les opérateurs de requête standard qui se trouvent dans la portée en spécifiant l’espace de noms approprié avec une directive `using`. L’expression de requête suivante accepte un tableau de chaînes, regroupe les chaînes qui commencent par le même caractère, puis trie ces groupes de chaînes.  
  
```  
var query = from str in stringArray  
            group str by str[0] into stringGroup  
            orderby stringGroup.Key  
            select stringGroup;  
```  
  
 Pour plus d’informations, consultez [Expressions de requête LINQ](../../../../csharp/programming-guide/linq-query-expressions/index.md).  
  
## <a name="implicitly-typed-variables-var"></a>Variables implicitement typées (var)  
 Au lieu de spécifier explicitement un type lorsque vous déclarez et initialisez une variable, vous pouvez utiliser le modificateur [var](../../../../csharp/language-reference/keywords/var.md) pour indiquer au compilateur qu’il doit déduire et assigner le type, comme illustré ici :  
  
```  
var number = 5;  
var name = "Virginia";  
var query = from str in stringArray  
            where str[0] == 'm'  
            select str;  
```  
  
 Les variables déclarées comme `var` sont aussi fortement typées que les variables dont vous spécifiez explicitement le type. `var` permet de créer des types anonymes, mais peut être utilisé pour toutes les variables locales. Les tableaux peuvent également être déclarés avec un typage implicite.  
  
 Pour plus d’informations, consultez [Variables locales implicitement typées](../../../../csharp/programming-guide/classes-and-structs/implicitly-typed-local-variables.md).  
  
## <a name="object-and-collection-initializers"></a>Initialiseurs d’objets et de collections  
 Les initialiseurs d’objets et de collections permettent d’initialiser un objet sans appeler explicitement un constructeur pour cet objet. Les initialiseurs sont généralement utilisés dans les expressions de requête pour projeter la source de données en un nouveau type de données. En supposant une classe nommée `Customer` avec les propriétés publiques `Name` et `Phone`, l’initialiseur d’objet peut être utilisé, comme dans le code suivant :  
  
```  
Customer cust = new Customer { Name = "Mike", Phone = "555-1212" };  
```  
  
 Pour plus d’informations, consultez [Initialiseurs d’objets et de collections](../../../../csharp/programming-guide/classes-and-structs/object-and-collection-initializers.md).  
  
## <a name="anonymous-types"></a>Types anonymes  
 Un type anonyme est construit par le compilateur et le nom du type est uniquement disponible pour le compilateur. Les types anonymes permettent de regrouper facilement des propriétés de manière temporaire dans un résultat de requête, sans avoir à définir un type nommé distinct. Les types anonymes sont initialisés avec une nouvelle expression et un initialiseur d’objet, comme indiqué ici :  
  
```  
select new {name = cust.Name, phone = cust.Phone};  
```  
  
 Pour plus d’informations, consultez [Types anonymes](../../../../csharp/programming-guide/classes-and-structs/anonymous-types.md).  
  
## <a name="extension-methods"></a>méthodes d’extension.  
 Une méthode d’extension est une méthode statique qui peut être associée à un type, de manière à être appelée comme une méthode d’instance de ce type. Cette fonctionnalité permet d’ajouter de nouvelles méthodes aux types existants sans les modifier. Les opérateurs de requête standard sont un ensemble de méthodes d’extension qui fournissent des fonctionnalités de requête [!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq_md.md)] pour tout type qui implémente <xref:System.Collections.Generic.IEnumerable%601>.  
  
 Pour plus d’informations, consultez [Méthodes d’extension](../../../../csharp/programming-guide/classes-and-structs/extension-methods.md).  
  
## <a name="lambda-expressions"></a>Expressions lambda  
 Une expression lambda est une fonction inline qui utilise l’opérateur => pour séparer les paramètres d’entrée du corps de la fonction, et qui peut être convertie au moment de la compilation en un délégué ou une arborescence d’expressions. En programmation [!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq_md.md)], vous rencontrerez des expressions lambda quand vous effectuerez des appels de méthode directs aux opérateurs de requête standard.  
  
 Pour plus d'informations, voir :  
  
-   [Fonctions anonymes](../../../../csharp/programming-guide/statements-expressions-operators/anonymous-functions.md)  
  
-   [Expressions lambda](../../../../csharp/programming-guide/statements-expressions-operators/lambda-expressions.md)  
  
-   [Arborescences d’expressions (C#)](../../../../csharp/programming-guide/concepts/expression-trees/index.md)  
  
## <a name="auto-implemented-properties"></a>Propriétés implémentées automatiquement  
 Les propriétés implémentées automatiquement rendent la déclaration de propriétés plus concise. Quand vous déclarez une propriété comme indiqué dans l’exemple suivant, le compilateur crée un champ de stockage privé et anonyme, uniquement accessible via les méthodes getter et setter de la propriété.  
  
```  
public string Name {get; set;}  
```  
  
 Pour plus d’informations, consultez [Propriétés implémentées automatiquement](../../../../csharp/programming-guide/classes-and-structs/auto-implemented-properties.md).  
  
## <a name="see-also"></a>Voir aussi  
 [LINQ (Language-Integrated Query) (C#)](../../../../csharp/programming-guide/concepts/linq/index.md)
