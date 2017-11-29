---
title: Structures (Guide de programmation C#)
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords:
- C# language, structs
- structs [C#]
ms.assetid: b7cf4ff2-0eb7-4e5c-93d5-b2196b4f5d89
caps.latest.revision: "31"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 475d9b96e078270faf6c841a62e6031556e8e539
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="structs-c-programming-guide"></a>Structures (Guide de programmation C#)
Les structs sont définis à l’aide du mot clé [struct](../../../csharp/language-reference/keywords/struct.md), par exemple :  
  
 [!code-csharp[csProgGuideObjects#39](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/structs_1.cs)]  
  
 Les structs partagent presque tous la même syntaxe que les classes, bien qu'ils soient plus limités que ces dernières :  
  
-   Au sein d’une déclaration de struct, les champs ne peuvent pas être initialisés à moins d’être déclarés comme étant de type const ou static.  
  
-   Un struct ne peut pas déclarer de constructeur par défaut (un constructeur sans paramètre) ni de finaliseur.  
  
-   Les structs sont copiés lors de l'assignation. Lorsqu'un struct est assigné à une nouvelle variable, toutes les données sont copiées et les modifications apportées à la nouvelle copie ne changent pas les données de la copie d'origine. Il est important de s’en souvenir lors de l’utilisation de collections de types valeur comme Dictionary\<string, myStruct>.  
  
-   Les structs sont des types valeur et les classes des types référence.  
  
-   Contrairement aux classes, il est possible d’instancier les structs sans avoir recours à un opérateur `new`.  
  
-   Les structs peuvent déclarer des constructeurs qui ont des paramètres.  
  
-   Un struct ne peut pas hériter d'un autre struct ou d'une classe ; il ne peut pas non plus servir de base à une classe. Tous les structs héritent directement de `System.ValueType`, qui hérite de `System.Object`.  
  
-   Un struct peut implémenter des interfaces.  
  
-   Un struct peut être utilisé comme un type Nullable et peut avoir une valeur null.  
  
## <a name="related-sections"></a>Rubriques connexes  
 Pour plus d'informations :  
  
-   [Utilisation de structs](../../../csharp/programming-guide/classes-and-structs/using-structs.md)  
  
-   [Constructeurs](../../../csharp/programming-guide/classes-and-structs/constructors.md)  
  
-   [Types Nullable](../../../csharp/programming-guide/nullable-types/index.md)  
  
-   [Comment : différencier le passage d’un struct et le passage d’une référence de classe à une méthode](../../../csharp/programming-guide/classes-and-structs/how-to-know-the-difference-passing-a-struct-and-passing-a-class-to-a-method.md)  
  
-   [Comment : implémenter des conversions définies par l’utilisateur entre des structs](../../../csharp/programming-guide/statements-expressions-operators/how-to-implement-user-defined-conversions-between-structs.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Guide de programmation C#](../../../csharp/programming-guide/index.md)  
 [Classes et structs](../../../csharp/programming-guide/classes-and-structs/index.md)  
 [Classes](../../../csharp/programming-guide/classes-and-structs/classes.md)
