---
title: "Introduction aux g&#233;n&#233;riques (guide de programmation C#) | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
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
  - "génériques (C#), à propos des génériques"
ms.assetid: a1ad761e-42f7-41dd-a62f-452a2de26b9d
caps.latest.revision: 32
caps.handback.revision: 32
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Introduction aux g&#233;n&#233;riques (guide de programmation C#)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Les classes génériques et les méthodes combinent un niveau de réutilisabilité, de sécurité de type et d'efficacité sans commune mesure avec leurs homologues non génériques.  Les génériques sont le plus souvent utilisés avec des collections et méthodes qui fonctionnent sur eux.  La version 2.0 de la bibliothèque de classes .NET Framework fournit un nouvel espace de noms, <xref:System.Collections.Generic>, qui contient plusieurs nouvelles classes de collection basées sur générique.  Il est recommandé que toutes les applications qui ciblent [!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort_md.md)] 2.0 et suivantes utilisent les nouvelles classes de collections génériques plutôt que des équivalents non génériques plus anciens tels que <xref:System.Collections.ArrayList>.  Pour plus d'informations, consultez [Génériques dans la bibliothèque de classes .NET Framework](../../../csharp/programming-guide/generics/generics-in-the-net-framework-class-library.md).  
  
 Bien sûr, vous pouvez également créer des types et des méthodes génériques personnalisés afin de fournir vos propres solutions et modèles de design généralisés qui sont de type sécurisé et efficace.  L'exemple de code suivant emploie une simple classe de liste liée générique à des fins de démonstration.  \(Dans la plupart des cas, vous devez utiliser la classe <xref:System.Collections.Generic.List%601> fournie par la bibliothèque de classes .NET Framework au lieu de créer la vôtre.\) Le paramètre de type `T` est utilisé dans plusieurs emplacements où l'on utiliserait normalement un type concret pour indiquer le type de l'élément stocké dans la liste.  Il est utilisé dans les manières suivantes :  
  
-   Comme le type d'un paramètre de méthode dans la méthode `AddHead`.  
  
-   Comme le type de retour de la méthode publique `GetNext` et de la propriété `Data` dans la classe `Node` imbriquée.  
  
-   Comme le type des données de membre privé dans la classe imbriquée.  
  
 Notez que T est disponible à la classe `Node` imbriquée.  Lorsque `GenericList<T>` est instancié avec un type concret, comme un `GenericList<int>`, par exemple, chaque occurrence de `T` est remplacée par `int`.  
  
 [!code-cs[csProgGuideGenerics#2](../../../csharp/programming-guide/generics/codesnippet/CSharp/introduction-to-generics_1.cs)]  
  
 L'exemple de code suivant montre comment le code client utilise la classe `GenericList<T>` générique pour créer une liste d'entiers.  En changeant simplement l'argument de type, le code suivant pourrait être facilement modifié pour créer des listes de chaînes ou tout autre type personnalisé :  
  
 [!code-cs[csProgGuideGenerics#3](../../../csharp/programming-guide/generics/codesnippet/CSharp/introduction-to-generics_2.cs)]  
  
## Voir aussi  
 <xref:System.Collections.Generic>   
 [Guide de programmation C\#](../../../csharp/programming-guide/index.md)   
 [Génériques](../../../csharp/programming-guide/generics/index.md)