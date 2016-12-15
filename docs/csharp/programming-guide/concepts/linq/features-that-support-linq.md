---
title: "C# Features That Support LINQ | Microsoft Docs"
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
  - "LINQ [C#], features supporting LINQ"
ms.assetid: 524b0078-ebfd-45a7-b390-f2ceb9d84797
caps.latest.revision: 23
caps.handback.revision: 21
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# C# Features That Support LINQ
[!INCLUDE[vs2017banner](../../../../csharp/includes/vs2017banner.md)]

La section suivante présente de nouvelles constructions de langage introduites dans C\# 3.0.  Bien que ces nouvelles fonctionnalités soient toutes utilisées à un certain degré avec les requêtes [!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq_md.md)], elles ne sont pas limitées à [!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq_md.md)] et peuvent être utilisées dans n'importe quel contexte approprié.  
  
## Expressions de requête  
 Les expressions de requête utilisent une syntaxe déclarative semblable à celle de SQL ou de XQuery pour interroger des collections dénombrables.  À la compilation, la syntaxe de requête est convertie en appels de méthode à l'implémentation d'un fournisseur [!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq_md.md)] des méthodes d'extension d'opérateur de requête standard.  Les applications contrôlent les opérateurs de requête standard qui sont dans la portée en spécifiant l'espace de noms approprié avec une directive `using`.  L'expression de requête suivante prend un tableau de chaînes, regroupe les chaînes en fonction de leur premier caractère et classe les groupes.  
  
```  
var query = from str in stringArray  
            group str by str[0] into stringGroup  
            orderby stringGroup.Key  
            select stringGroup;  
```  
  
 Pour plus d'informations, consultez [Expressions de requête \(LINQ\)](../../../../csharp/programming-guide/linq-query-expressions/index.md).  
  
## Variables implicitement typées \(var\)  
 Au lieu de spécifier explicitement un type lorsque vous déclarez et initialisez une variable, vous pouvez utiliser le modificateur [var](../../../../csharp/language-reference/keywords/var.md) pour indiquer au compilateur de déduire et d'assigner le type, comme montré ici :  
  
```  
var number = 5;  
var name = "Virginia";  
var query = from str in stringArray  
            where str[0] == 'm'  
            select str;  
```  
  
 Les variables `var` déclarées sont aussi fortement typées que les variables dont le type a été spécifié explicitement.  L'utilisation de `var` permet de créer des types anonymes, mais elle peut être utilisée pour n'importe quelle variable locale.  Les tableaux peuvent également être déclarés avec des types implicites.  
  
 Pour plus d'informations, consultez [Variables locales implicitement typées](../../../../csharp/programming-guide/classes-and-structs/implicitly-typed-local-variables.md).  
  
## Initialiseurs d'objets et de collections  
 Les initialiseurs d'objets et de collections permettent d'initialiser des objets sans appeler explicitement un constructeur.  Les initialiseurs sont généralement utilisés dans les expressions de requête lors de la projection des données sources dans un nouveau type de données.  Si vous disposez d'une classe nommée `Customer` avec des propriétés `Name` et `Phone` publiques, vous pouvez utiliser l'initialiseur d'objet comme dans le code suivant :  
  
```  
Customer cust = new Customer { Name = "Mike", Phone = "555-1212" };  
```  
  
 Pour plus d'informations, consultez [Initialiseurs d'objets et de collections](../../../../csharp/programming-guide/classes-and-structs/object-and-collection-initializers.md).  
  
## Types anonymes  
 Un type anonyme est construit par le compilateur et seul celui\-ci peut accéder au nom du type.  Les types anonymes constituent un moyen pratique pour regrouper temporairement un ensemble de propriétés dans un résultat de requête sans définir un type nommé distinct.  Les types anonymes sont initialisés avec une nouvelle expression et un initialiseur d'objet, comme présenté ici :  
  
```  
select new {name = cust.Name, phone = cust.Phone};  
```  
  
 Pour plus d'informations, consultez [Types anonymes](../../../../csharp/programming-guide/classes-and-structs/anonymous-types.md).  
  
## Méthodes d'extension  
 Une méthode d'extension est une méthode statique qui peut être associée à un type et ainsi être appelée comme s'il s'agissait d'une méthode d'instance sur le type.  Cette fonctionnalité vous permet en fait d'ajouter de nouvelles méthodes aux types existants sans les modifier réellement.  Les opérateurs de requête standard sont un ensemble de méthodes d'extension qui fournissent les fonctionnalités de requête [!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq_md.md)] pour tout type qui implémente <xref:System.Collections.Generic.IEnumerable%601>.  
  
 Pour plus d'informations, consultez [Méthodes d'extension](../../../../csharp/programming-guide/classes-and-structs/extension-methods.md).  
  
## Expressions lambda  
 Une expression lambda est une fonction inline qui utilise l'opérateur \=\> pour séparer les paramètres d'entrée du corps de la fonction et qui peut être convertie en délégué ou en arborescence d'expression au moment de la compilation.  En termes de programmation [!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq_md.md)], vous rencontrez des expressions lambda lorsque vous effectuez des appels de méthode directs aux opérateurs de requête standard.  
  
 Pour plus d'informations, consultez :  
  
-   [Fonctions anonymes](../../../../csharp/programming-guide/statements-expressions-operators/anonymous-functions.md)  
  
-   [Expressions lambda](../../../../csharp/programming-guide/statements-expressions-operators/lambda-expressions.md)  
  
-   [Arborescences d'expression](../Topic/Expression%20Trees%20\(C%23%20and%20Visual%20Basic\).md)  
  
## Propriétés implémentées automatiquement  
 Les propriétés implémentées automatiquement permettent de rendre la déclaration de propriété plus concise.  Lorsque vous déclarez une propriété comme dans l'exemple suivant, le compilateur crée un champ de stockage confidentiel et anonyme qui n'est accessible que via les accesseurs Get et Set de propriété.  
  
```  
public string Name {get; set;}  
```  
  
 Pour plus d'informations, consultez [Propriétés implémentées automatiquement](../../../../csharp/programming-guide/classes-and-structs/auto-implemented-properties.md).  
  
## Voir aussi  
 [LINQ \(Language\-Integrated Query\)](../Topic/LINQ%20\(Language-Integrated%20Query\).md)   
 [Visual Basic Features That Support LINQ](../../../../visual-basic/programming-guide/concepts/linq/features-that-support-linq.md)