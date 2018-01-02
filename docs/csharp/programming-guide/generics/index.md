---
title: "Génériques (guide de programmation C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords:
- C# language, generics
- generics [C#]
ms.assetid: 75ea8509-a4ea-4e7a-a2b3-cf72482e9282
caps.latest.revision: "23"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 0804ca0fcefcc53e06352accf9a2db19edb31037
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="generics-c-programming-guide"></a>Génériques (guide de programmation C#)
Les génériques ont été ajoutés à la version 2.0 du langage C# et du Common Language Runtime (CLR). Les génériques introduisent le concept des paramètres de type dans .NET Framework, qui permettent de concevoir des classes et des méthodes qui diffèrent la spécification d’un ou de plusieurs types jusqu’à ce que la classe ou la méthode soit déclarée et instanciée par le code client. Par exemple, à l’aide d’un paramètre de type générique T, vous pouvez écrire une seule classe qui peut être utilisée par un autre code client sans impliquer le coût ou le risque des casts ou des opérations de boxing à l’exécution, comme illustré ici :  
  
 [!code-csharp[csProgGuideGenerics#1](../../../csharp/programming-guide/generics/codesnippet/CSharp/index_1.cs)]  
  
## <a name="generics-overview"></a>Vue d’ensemble des génériques  
  
-   Utilisez des types génériques pour optimiser la réutilisation de code, la sécurité des types et les performances.  
  
-   L’utilisation la plus courante des génériques est de créer des classes de collection.  
  
-   La bibliothèque de classes du .NET Framework contient plusieurs nouvelles classes de collection génériques dans l’espace de noms <xref:System.Collections.Generic>. Celles-ci doivent être utilisées chaque fois que c’est possible, à la place de classes comme <xref:System.Collections.ArrayList> dans l’espace de noms <xref:System.Collections>.  
  
-   Vous pouvez créer vos propres interfaces, classes, méthodes, événements et délégués génériques.  
  
-   Les classes génériques peuvent être contraintes pour permettre l’accès à des méthodes sur des types de données particuliers.  
  
-   Des informations sur les types qui sont utilisés dans un type de données générique peuvent être obtenues à l’exécution à l’aide de la réflexion.  
  
## <a name="related-sections"></a>Rubriques connexes  
 Pour plus d'informations :  
  
-   [Introduction aux génériques](../../../csharp/programming-guide/generics/introduction-to-generics.md)  
  
-   [Avantages des génériques](../../../csharp/programming-guide/generics/benefits-of-generics.md)  
  
-   [Paramètres de type générique](../../../csharp/programming-guide/generics/generic-type-parameters.md)  
  
-   [Contraintes sur les paramètres de type](../../../csharp/programming-guide/generics/constraints-on-type-parameters.md)  
  
-   [Classes génériques](../../../csharp/programming-guide/generics/generic-classes.md)  
  
-   [Interfaces génériques](../../../csharp/programming-guide/generics/generic-interfaces.md)  
  
-   [Méthodes génériques](../../../csharp/programming-guide/generics/generic-methods.md)  
  
-   [Délégués génériques](../../../csharp/programming-guide/generics/generic-delegates.md)  
  
-   [Différences entre les modèles C++ et les génériques C#](../../../csharp/programming-guide/generics/differences-between-cpp-templates-and-csharp-generics.md)  
  
-   [Génériques et réflexion](../../../csharp/programming-guide/generics/generics-and-reflection.md)  
  
-   [Génériques dans le runtime](../../../csharp/programming-guide/generics/generics-in-the-run-time.md)  
  
-   [Génériques dans la bibliothèque de classes .NET Framework](../../../csharp/programming-guide/generics/generics-in-the-net-framework-class-library.md)  
  
## <a name="c-language-specification"></a>Spécification du langage C#  
 Pour plus d'informations, voir la [spécification du langage C#](../../../csharp/language-reference/language-specification/index.md).  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.Collections.Generic>  
 [Guide de programmation C#](../../../csharp/programming-guide/index.md)  
 [Types](../../../csharp/programming-guide/types/index.md)  
 [\<typeparam>](../../../csharp/programming-guide/xmldoc/typeparam.md)  
 [\<typeparamref>](../../../csharp/programming-guide/xmldoc/typeparamref.md)
