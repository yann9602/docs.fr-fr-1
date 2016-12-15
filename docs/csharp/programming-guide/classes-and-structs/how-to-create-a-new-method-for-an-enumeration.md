---
title: "Comment&#160;: cr&#233;er une m&#233;thode pour une &#233;num&#233;ration (Guide de programmation&#160;C#) | Microsoft Docs"
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
  - "extensibilité d'enum (C#)"
  - "énumérations (C#)"
  - "méthodes d'extension (C#), pour les enums"
ms.assetid: 100106f9-1e54-462c-8ebe-3892fe23b6eb
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Comment&#160;: cr&#233;er une m&#233;thode pour une &#233;num&#233;ration (Guide de programmation&#160;C#)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Vous pouvez utiliser des méthodes d'extension pour ajouter les fonctionnalités spécifique à un type d'enum particulier.  
  
## Exemple  
 Dans l'exemple suivant, l'énumération `Grades` représente les notes possibles sous forme de lettre qu'un étudiant peut obtenir dans une classe.  Une méthode d'extension nommée `Passing` est ajoutée au type `Grades` afin que chaque instance de ce type sache maintenant si cela représente une note d'admission ou pas.  
  
 [!code-cs[csProgGuideExtensionMethods#2](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-create-a-new-method-for-an-enumeration_1.cs)]  
  
 Notez que la classe `Extensions` contient également une variable statique mise à jour dynamiquement et que la valeur de retour de la méthode d'extension reflète la valeur actuelle de cette variable.  Cela montre qu'en arrière\-plan les méthodes d'extension sont appelées directement sur la classe statique dans laquelle elles sont définies.  
  
## Compilation du code  
 Pour exécuter ce code, copiez\-le et collez\-le dans un projet d'application console Visual C\# qui a été créé dans [!INCLUDE[vs_current_short](../../../csharp/programming-guide/classes-and-structs/includes/vs_current_short_md.md)].  Par défaut, ce projet cible la version 3.5 du [!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort_md.md)] et il possède une référence à System.Core.dll et une directive `using` pour System.Linq.  Si une ou plusieurs de ces spécifications sont absentes du projet, vous pouvez les ajouter manuellement.  Pour plus d'informations, consultez [How to: Create a LINQ Project](../Topic/How%20to:%20Create%20a%20LINQ%20Project.md).  
  
## Voir aussi  
 [Guide de programmation C\#](../../../csharp/programming-guide/index.md)   
 [Méthodes d'extension](../../../csharp/programming-guide/classes-and-structs/extension-methods.md)