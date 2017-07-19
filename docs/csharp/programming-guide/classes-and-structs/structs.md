---
title: Structs (Guide de programmation C#) | Microsoft Docs
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
helpviewer_keywords:
- C# language, structs
- structs [C#]
ms.assetid: b7cf4ff2-0eb7-4e5c-93d5-b2196b4f5d89
caps.latest.revision: 31
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
ms.sourcegitcommit: a5ed524a1b17f7be8903f998cbd732594faab831
ms.openlocfilehash: 41574404f923695b3ba065d3c22f102bd2843e68
ms.contentlocale: fr-fr
ms.lasthandoff: 05/22/2017

---
# <a name="structs-c-programming-guide"></a>Structures (Guide de programmation C#)
Les structs sont définis à l’aide du mot clé [struct](../../../csharp/language-reference/keywords/struct.md), par exemple :  
  
 [!code-cs[csProgGuideObjects#39](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/structs_1.cs)]  
  
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
