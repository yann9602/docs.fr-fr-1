---
title: "Comment : définir des propriétés abstraites (Guide de programmation C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords:
- properties [C#], abstract
- abstract properties [C#]
ms.assetid: 672a90eb-47b9-4ae0-9914-af53852fddcb
caps.latest.revision: "13"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: cd8a42c1040180c19bc58627ab0c6a21ace77773
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-define-abstract-properties-c-programming-guide"></a>Comment : définir des propriétés abstraites (Guide de programmation C#)
L’exemple suivant montre comment définir des propriétés [abstract](../../../csharp/language-reference/keywords/abstract.md). Une déclaration de propriété abstraite ne fournit pas une implémentation des accesseurs de propriété ; elle déclare que la classe prend en charge des propriétés, mais laisse l’implémentation de l’accesseur aux classes dérivées. L’exemple suivant montre comment implémenter les propriétés abstraites héritées d’une classe de base.  
  
 Cet exemple se compose de trois fichiers, chacun étant compilé individuellement, et l’assembly obtenu est référencé par la compilation suivante :  
  
-   abstractshape.cs : classe `Shape` qui contient une propriété `Area` abstraite.  
  
-   shapes.cs : sous-classes de la classe `Shape`.  
  
-   shapetest.cs : programme de test destiné à afficher les zones de certains objets dérivés de `Shape`.  
  
 Pour compiler l’exemple, utilisez la commande suivante :  
  
 `csc abstractshape.cs shapes.cs shapetest.cs`  
  
 Cette commande crée le fichier exécutable shapetest.exe.  
  
## <a name="example"></a>Exemple  
 Ce fichier déclare la classe `Shape` qui contient la propriété `Area` du type `double`.  
  
 [!code-csharp[csProgGuideInheritance#1](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-define-abstract-properties_1.cs)]  
  
-   Les modificateurs sur la propriété sont placés sur la déclaration de propriété proprement dite. Exemple :  
  
    ```  
    public abstract double Area  
    ```  
  
-   Quand vous déclarez une propriété abstraite (telle que `Area` dans cet exemple), vous indiquez simplement quels les accesseurs de propriété sont disponibles, mais vous ne les implémentez pas. Dans cet exemple, seul un accesseur [get](../../../csharp/language-reference/keywords/get.md) est disponible, donc la propriété est en lecture seule.  
  
## <a name="example"></a>Exemple  
 Le code suivant présente trois sous-classes de `Shape` et indique comment elles substituent la propriété `Area` pour fournir leur propre implémentation.  
  
 [!code-csharp[csProgGuideInheritance#2](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-define-abstract-properties_2.cs)]  
  
## <a name="example"></a>Exemple  
 Le code suivant montre un programme de test qui crée un certain nombre d’objets dérivés de `Shape` et imprime les zones correspondantes.  
  
 [!code-csharp[csProgGuideInheritance#3](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-define-abstract-properties_3.cs)]  
  
## <a name="see-also"></a>Voir aussi  
 [Guide de programmation C#](../../../csharp/programming-guide/index.md)  
 [Classes et structs](../../../csharp/programming-guide/classes-and-structs/index.md)  
 [Classes abstract et sealed et membres de classe](../../../csharp/programming-guide/classes-and-structs/abstract-and-sealed-classes-and-class-members.md)  
 [Propriétés](../../../csharp/programming-guide/classes-and-structs/properties.md)  
 [Guide pratique : créer et utiliser des assemblys à l’aide de la ligne de commande](http://msdn.microsoft.com/library/70f65026-3687-4e9c-ab79-c18b97dd8be4)
