---
title: "Structures (Guide de programmation C#) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.technology: 
  - "devlang-csharp"
ms.topic: "article"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "langage C#, structs"
  - "structures (C#)"
ms.assetid: b7cf4ff2-0eb7-4e5c-93d5-b2196b4f5d89
caps.latest.revision: 31
author: "BillWagner"
ms.author: "wiwagn"
caps.handback.revision: 31
---
# Structures (Guide de programmation C#)
Les structs sont définis à l'aide du mot clé [struct](../../../csharp/language-reference/keywords/struct.md), par exemple :  
  
 [!code-cs[csProgGuideObjects#39](../../../csharp/programming-guide/classes-and-structs/codesnippet/csharp/structs_1.cs)]  
  
 Les structs partagent presque tous la même syntaxe que les classes, bien qu'ils soient plus limités que ces dernières :  
  
-   Dans une déclaration de structure, les champs ne peuvent pas être initialisés à moins qu'ils ne soient déclarés comme const ou static.  
  
-   Un struct ne peut pas déclarer de constructeur \(un constructeur sans paramètres\) ni de destructeur par défaut.  
  
-   Les structs sont copiés lors de l'assignation.  Lorsqu'un struct est assigné à une nouvelle variable, toutes les données sont copiées et les modifications apportées à la nouvelle copie ne changent pas les données de la copie d'origine.  Il est important de se souvenir lors de l'utilisation des collections de types valeur tels que Dictionnaire\<chaîne, myStruct\>.  
  
-   Les structs sont des types valeur et les classes des types référence.  
  
-   Contrairement aux classes, les objets struct peuvent être instanciés sans recours à l'opérateur `new`.  
  
-   Les structs peuvent déclarer des constructeurs qui ont des paramètres.  
  
-   Un struct ne peut pas hériter d'un autre struct ou d'une classe ; il ne peut pas non plus servir de base à une classe.  Tous les structs héritent directement de `System.ValueType`, qui hérite de `System.Object`.  
  
-   Un struct peut implémenter des interfaces.  
  
-   Un struct peut être utilisé comme un type Nullable et peut se voir assigner une valeur Null.  
  
## Rubriques connexes  
 Pour plus d'informations :  
  
-   [Utilisation de structs](../../../csharp/programming-guide/classes-and-structs/using-structs.md)  
  
-   [Constructeurs](../../../csharp/programming-guide/classes-and-structs/constructors.md)  
  
-   [Types Nullable](../../../csharp/programming-guide/nullable-types/index.md)  
  
-   [Comment : différencier le passage d'un struct et le passage d'une référence de classe à une méthode](../../../csharp/programming-guide/classes-and-structs/how-to-know-the-difference-passing-a-struct-and-passing-a-class-to-a-method.md)  
  
-   [Comment : implémenter des conversions définies par l'utilisateur entre des structs](../../../csharp/programming-guide/statements-expressions-operators/how-to-implement-user-defined-conversions-between-structs.md)  
  
-   [More About Variables](http://go.microsoft.com/fwlink/?LinkId=221230) dans [Beginning Visual C\# 2010](http://go.microsoft.com/fwlink/?LinkId=221214)  
  
## Voir aussi  
 [Guide de programmation C\#](../../../csharp/programming-guide/index.md)   
 [Classes et structs](../../../csharp/programming-guide/classes-and-structs/index.md)   
 [Classes](../../../csharp/programming-guide/classes-and-structs/classes.md)