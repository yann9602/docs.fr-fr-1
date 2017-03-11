---
title: "G&#233;n&#233;riques (guide de programmation C#) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.technology: 
  - "devlang-csharp"
ms.topic: "article"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "langage C#, génériques"
  - "génériques (C#)"
ms.assetid: 75ea8509-a4ea-4e7a-a2b3-cf72482e9282
caps.latest.revision: 23
author: "BillWagner"
ms.author: "wiwagn"
caps.handback.revision: 23
---
# G&#233;n&#233;riques (guide de programmation C#)
Les génériques ont été ajoutés à la version 2.0 du langage C\# et du Common Language Runtime \(CLR\).  Les génériques introduisent dans le .NET Framework le concept de paramètres de type, qui rendent possible la réception des classes et des méthodes dont la spécification d'un ou de plusieurs types diffère jusqu'à ce que la classe ou la méthode soit déclarée et instanciée par code client.  Par exemple, en utilisant un paramètre T de type générique, vous pouvez écrire une classe unique qu'un autre code client peut utiliser sans induire le coût ou le risque de casts d'exécution ou d'opérations de boxing, comme illustré ici :  
  
 [!code-cs[csProgGuideGenerics#1](../../../csharp/programming-guide/generics/codesnippet/csharp/index_1.cs)]  
  
## Vue d'ensemble des génériques  
  
-   Utilisez les types génériques pour optimiser la réutilisation de code, la sécurité du type et les performances.  
  
-   L'utilisation la plus courante de génériques consiste à créer des classes de collection.  
  
-   La bibliothèque de classes .NET Framework contient plusieurs nouvelles classes de collection de génériques dans l'espace de noms <xref:System.Collections.Generic>.  Ceux\-ci doivent être utilisés chaque fois que possible à la place de classes telles que <xref:System.Collections.ArrayList> dans l'espace de noms <xref:System.Collections>.  
  
-   Vous pouvez créer vos propres interfaces, classes, méthodes, événements et délégués génériques.  
  
-   Les classes génériques peuvent être contraintes pour activer l'accès aux méthodes sur des types de données particuliers.  
  
-   Les informations sur les types qui sont utilisés dans un type de données générique peuvent être obtenues par réflexion lors de l'exécution.  
  
## Rubriques connexes  
 Pour plus d'informations :  
  
-   [Introduction aux génériques](../../../csharp/programming-guide/generics/introduction-to-generics.md)  
  
-   [Avantages des génériques](../../../csharp/programming-guide/generics/benefits-of-generics.md)  
  
-   [Paramètres de type générique](../../../csharp/programming-guide/generics/generic-type-parameters.md)  
  
-   [Contraintes sur les paramètres de type](../../../csharp/programming-guide/generics/constraints-on-type-parameters.md)  
  
-   [Classes génériques](../../../csharp/programming-guide/generics/generic-classes.md)  
  
-   [Interfaces génériques](../../../csharp/programming-guide/generics/generic-interfaces.md)  
  
-   [Méthodes génériques](../../../csharp/programming-guide/generics/generic-methods.md)  
  
-   [Délégués génériques](../../../csharp/programming-guide/generics/generic-delegates.md)  
  
-   [Mot clé par default](../../../csharp/programming-guide/generics/default-keyword-in-generic-code.md)  
  
-   [Différences entre les templates C\+\+ et les génériques C\#](../../../csharp/programming-guide/generics/differences-between-cpp-templates-and-csharp-generics.md)  
  
-   [Génériques et réflexion](../../../csharp/programming-guide/generics/generics-and-reflection.md)  
  
-   [Génériques dans le runtime](../../../csharp/programming-guide/generics/generics-in-the-run-time.md)  
  
-   [Génériques dans la bibliothèque de classes .NET Framework](../../../csharp/programming-guide/generics/generics-in-the-net-framework-class-library.md)  
  
## Spécification du langage C\#  
 Pour plus d'informations, consultez [Spécification du langage C\#](../../../csharp/language-reference/language-specification.md).  
  
## Voir aussi  
 <xref:System.Collections.Generic>   
 [Guide de programmation C\#](../../../csharp/programming-guide/index.md)   
 [Types](../../../csharp/programming-guide/types/index.md)   
 [\<typeparam\>](../../../csharp/programming-guide/xmldoc/typeparam.md)   
 [\<typeparamref\>](../../../csharp/programming-guide/xmldoc/typeparamref.md)