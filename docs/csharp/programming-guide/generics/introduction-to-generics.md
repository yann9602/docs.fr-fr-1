---
title: "Introduction aux génériques (guide de programmation C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords: generics [C#], about generics
ms.assetid: a1ad761e-42f7-41dd-a62f-452a2de26b9d
caps.latest.revision: "32"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: ec4fe9cc9fe7bf868fcc8afe4dc4e4234241e352
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="introduction-to-generics-c-programming-guide"></a>Introduction aux génériques (guide de programmation C#)
Les méthodes et les classes génériques combinent la réutilisabilité, la cohérence des types et l’efficacité, ce que ne peuvent pas faire leurs équivalents non génériques. Les génériques sont plus fréquemment utilisés dans des collections et des méthodes qui agissent sur eux. La version 2.0 de la bibliothèque de classes .NET Framework fournit un nouvel espace de noms, <xref:System.Collections.Generic>, qui contient plusieurs nouvelles classes de collection génériques. Il est recommandé que toutes les applications qui ciblent le [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] 2.0 et versions ultérieures utilisent les nouvelles classes de collection générique au lieu d’équivalents non génériques plus anciens tels que <xref:System.Collections.ArrayList>. Pour plus d’informations, consultez [Génériques dans la bibliothèque de classes .NET Framework](../../../csharp/programming-guide/generics/generics-in-the-net-framework-class-library.md).  
  
 Bien sûr, vous pouvez également créer des types et des méthodes génériques personnalisés pour fournir des solutions et des modèles de conception généralisés qui soient efficaces et de type sécurisé. L’exemple de code suivant montre une classe de liste liée générique simple, à des fins de démonstration. (Dans la plupart des cas, vous devez utiliser le <xref:System.Collections.Generic.List%601> classe fournie par la bibliothèque de classes .NET Framework au lieu de créer votre propre.) Le paramètre de type `T` est utilisé dans plusieurs emplacements où un type concret est normalement utilisé pour indiquer le type de l’élément stocké dans la liste. Il est utilisé de la façon suivante :  
  
-   Comme le type d’un paramètre de méthode dans la méthode`AddHead`.  
  
-   Comme le type de retour de la méthode publique `GetNext` et de la propriété `Data` de la classe imbriquée `Node`.  
  
-   Comme le type des données de membre privé de la classe imbriquée.  
  
 Notez que T est disponible pour la classe imbriquée `Node`. Quand `GenericList<T>` est instancié avec un type concret, par exemple comme un `GenericList<int>`, chaque occurrence de `T` est remplacée par `int`.  
  
 [!code-csharp[csProgGuideGenerics#2](../../../csharp/programming-guide/generics/codesnippet/CSharp/introduction-to-generics_1.cs)]  
  
 L’exemple de code suivant montre comment le code client utilise la classe générique `GenericList<T>` pour créer une liste d’entiers. En changeant l’argument de type, vous pouvez facilement modifier le code suivant pour créer des listes de chaînes ou tout autre type personnalisé :  
  
 [!code-csharp[csProgGuideGenerics#3](../../../csharp/programming-guide/generics/codesnippet/CSharp/introduction-to-generics_2.cs)]  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.Collections.Generic>  
 [Guide de programmation C#](../../../csharp/programming-guide/index.md)  
 [Génériques](../../../csharp/programming-guide/generics/index.md)
