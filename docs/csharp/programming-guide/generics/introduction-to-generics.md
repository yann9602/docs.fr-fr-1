---
title: "Introduction aux génériques (guide de programmation C#) | Microsoft Docs"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
helpviewer_keywords:
- generics [C#], about generics
ms.assetid: a1ad761e-42f7-41dd-a62f-452a2de26b9d
caps.latest.revision: 32
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
translationtype: Human Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: f3092eb1e5435bbced565b02d989a57abf2d52e0
ms.lasthandoff: 03/13/2017

---
# <a name="introduction-to-generics-c-programming-guide"></a>Introduction aux génériques (guide de programmation C#)
Les méthodes et les classes génériques combinent la réutilisabilité, la cohérence des types et l’efficacité, ce que ne peuvent pas faire leurs équivalents non génériques. Les génériques sont plus fréquemment utilisés dans des collections et des méthodes qui agissent sur eux. La version 2.0 de la bibliothèque de classes .NET Framework fournit un nouvel espace de noms, <xref:System.Collections.Generic>, qui inclut plusieurs nouvelles classes de collection génériques. Pour toutes les applications qui ciblent le [!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort_md.md)] 2.0 et versions ultérieures, il est recommandé d’utiliser les nouvelles classes de collections génériques plutôt que leurs équivalents non génériques, tels que <xref:System.Collections.ArrayList>. Pour plus d’informations, consultez [Génériques dans la bibliothèque de classes .NET Framework](../../../csharp/programming-guide/generics/generics-in-the-net-framework-class-library.md).  
  
 Bien sûr, vous pouvez également créer des types et des méthodes génériques personnalisés pour fournir des solutions et des modèles de conception généralisés qui soient efficaces et de type sécurisé. L’exemple de code suivant montre une classe de liste liée générique simple, à des fins de démonstration. Dans la plupart des cas, vous devrez utiliser la classe <xref:System.Collections.Generic.List%601> fournie par la bibliothèque de classes .NET Framework au lieu de créer la vôtre. Le paramètre de type `T` est utilisé dans plusieurs emplacements où un type concret est normalement utilisé pour indiquer le type de l’élément stocké dans la liste. Il est utilisé de la façon suivante :  
  
-   Comme le type d’un paramètre de méthode dans la méthode`AddHead`.  
  
-   Comme le type de retour de la méthode publique `GetNext` et de la propriété `Data` de la classe imbriquée `Node`.  
  
-   Comme le type des données de membre privé de la classe imbriquée.  
  
 Notez que T est disponible pour la classe imbriquée `Node`. Quand `GenericList<T>` est instancié avec un type concret, par exemple comme un `GenericList<int>`, chaque occurrence de `T` est remplacée par `int`.  
  
 [!code-cs[csProgGuideGenerics#2](../../../csharp/programming-guide/generics/codesnippet/CSharp/introduction-to-generics_1.cs)]  
  
 L’exemple de code suivant montre comment le code client utilise la classe générique `GenericList<T>` pour créer une liste d’entiers. En changeant l’argument de type, vous pouvez facilement modifier le code suivant pour créer des listes de chaînes ou tout autre type personnalisé :  
  
 [!code-cs[csProgGuideGenerics#3](../../../csharp/programming-guide/generics/codesnippet/CSharp/introduction-to-generics_2.cs)]  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.Collections.Generic>   
 [Guide de programmation C#](../../../csharp/programming-guide/index.md)   
 [Génériques](../../../csharp/programming-guide/generics/index.md)
