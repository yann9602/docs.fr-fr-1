---
title: "What&#39;s New for Visual C# | Microsoft Docs"
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
ms.assetid: 9f18dc26-27fa-4603-a639-b573f07a117b
caps.latest.revision: 39
caps.handback.revision: 39
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# What&#39;s New for Visual C# #
[!INCLUDE[vs2017banner](../../csharp/includes/vs2017banner.md)]

Cette page recense les noms des principales fonctionnalités pour chaque version de C\# et décrit les fonctionnalités nouvelles et améliorées de la dernière version du langage.  
  
## Versions antérieures  
 C\# 1, Visual Studio .NET 2002  
 Première version  
  
 C\# 1.1, Visual Studio .NET 2003  
 `#line` pragma et commentaires de documents xml  
  
 C\# 2, Visual Studio .NET 2005  
 Méthodes anonymes, génériques, types Nullable, iterateurs\/rendement, classes `static`, variance co\/contra pour les délégués  
  
 C\# 3, Visual Studio .NET 2008  
 Initialiseurs d’objet et de collection, expressions lambda, méthodes d’extension, types anonymes, propriétés automatiques, Language Integrated Query \(LINQ\), types anonymes, inférence de type de variable `var` locale, LINQ  
  
 C\# 4, Visual Studio .NET 2010  
 `Dynamic`, arguments nommés, paramètres facultatifs, variance co\/contra générique  
  
 C\# 5, Visual Studio .NET 2012  
 `Async` \/ `await`, attributs des information sur l’appelant  
  
 Visual Studio .NET 2013  
 Correctifs de bogues, améliorations des performances et aperçus des technologies de la plateforme des compilateurs .NET \(« Roslyn »\)  
  
 C\# 6, Visual Studio .NET 2015  
 Version actuelle, voir ci\-dessous  
  
## Version actuelle  
 [nameof](../../csharp/language-reference/keywords/nameof.md)  
 Vous pouvez obtenir le nom de chaîne non qualifié d’un type ou membre et l’utiliser dans un message d’erreur sans effectuer de codage irréversible de chaîne.  Votre code reste alors correct lors de la refactorisation.  Cette fonctionnalité est également utile pour placer des liens MVC modèle\-vue\-contrôleur et activer des événements de modification de propriété.  
  
 [Interpolation de chaîne](../../csharp/language-reference/keywords/interpolated-strings.md)  
 Vous pouvez utiliser des expressions d’interpolation de chaîne pour construire des chaînes.  Une expression de chaîne interpolée s’apparente à une chaîne de modèle contenant des expressions.  C\# crée une chaîne en remplaçant les expressions par les représentations ToString des résultats des expressions.  Les arguments d’une chaîne interpolée sont plus compréhensibles que dans une [Mise en forme composite](../Topic/Composite%20Formatting.md).  
  
 [Accès aux membres et indexation Null\-condition](../../csharp/language-reference/operators/null-conditional-operators.md)  
 Vous pouvez rechercher les valeurs Null à l’aide d’une syntaxe très légère avant d’effectuer une opération d’accès aux membres \(`?.`\) ou d’indexation \(`?[]`\).  Ces opérateurs permettent d’écrire moins de code pour gérer les vérifications Null, notamment pour l’exploration des structures de données.  Si la référence objet ou l’opérande gauche est Null, l’opération renvoie la valeur Null.  
  
 [Initialiseurs d’index](../../csharp/programming-guide/classes-and-structs/object-and-collection-initializers.md).  
 Vous pouvez désormais initialiser des éléments spécifiques d’une collection qui prend en charge l’indexation, par exemple un dictionnaire.  
  
 [Initialiseur de collection et méthodes d’ajout d’extension](../../csharp/programming-guide/classes-and-structs/object-and-collection-initializers.md)  
 Vous pouvez désormais utiliser des initialiseurs de collection lorsque la collection comporte une méthode d’ajout d’extension.  Auparavant, la méthode d’ajout devait être une méthode d’instance.  
  
 **Résolution de surcharge**  
 Le compilateur a amélioré la résolution de surcharge. En conséquence, une plus grande proportion de code se comporte exactement comme prévu.  Vous cesserez notamment de rencontrer des problèmes lorsque vous choisissez entre les surcharges ayant des types de valeur Nullable, ou lorsque vous transmettez des groupes de méthodes \(au lieu d’expressions lambda\) aux surcharges ayant des délégués.  
  
 [Filtres d’exception](../../csharp/language-reference/keywords/try-catch.md)  
 Vous pouvez utiliser des filtres d’exception dans des clauses `catch` pour déterminer si une clause Catch doit gérer l’exception.  Sans cette fonctionnalité, vous devez lever à nouveau l’exception, ce qui a pour effet d’extraire la pile des appels signalée dans l’exception renvoyée.  
  
 [Blocs Await in Catch et Finally](../../csharp/language-reference/keywords/try-catch.md)  
 Vous pouvez utiliser `await` dans des clauses `catch` et `finally`.  
  
 [Initialiseurs de propriété automatique](../../csharp/programming-guide/classes-and-structs/auto-implemented-properties.md)  
 Vous pouvez désormais initialiser des propriétés automatiques comme vous le faites pour des champs.  
  
 [Propriétés automatiques d’accesseur Get](../../csharp/programming-guide/classes-and-structs/auto-implemented-properties.md)  
 Vous pouvez définir des propriétés automatiques en lecture seule sans avoir à définir une propriété avec sa syntaxe complète.  Vous pouvez initialiser la propriété lorsque vous la déclarez ou dans le constructeur du type.  
  
 **Membres de fonction avec corps d’expression**  
 Vous pouvez déclarer des membres avec des corps d’expression de code à l’aide de la même syntaxe légère que pour les expressions lambda.  Consultez [Méthodes](../../csharp/programming-guide/classes-and-structs/methods.md), [Propriétés](../../csharp/programming-guide/classes-and-structs/properties.md), [Indexeurs](../../csharp/programming-guide/indexers/index.md) et [Opérateurs surchargeables](../../csharp/programming-guide/statements-expressions-operators/overloadable-operators.md).  
  
 [Utilisation du type Static](../../csharp/language-reference/keywords/using-directive.md)  
 Vous pouvez importer des membres statiques accessibles de type Static de manière à pouvoir faire référence aux membres sans qualifier l’accès avec le nom du type.  
  
## Voir aussi  
 [Nouveautés de Visual Studio 2015](/visual-studio/ide/what-s-new-in-visual-studio-2015)