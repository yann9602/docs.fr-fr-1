---
title: "Comment&#160;: initialiser un dictionnaire avec un initialiseur de collection (Guide de programmation C#) | Microsoft Docs"
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
  - "initialiseurs de collections [C#], avec dictionnaire"
ms.assetid: 25283922-f8ee-40dc-a639-fac30804ec71
caps.latest.revision: 10
caps.handback.revision: 10
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Comment&#160;: initialiser un dictionnaire avec un initialiseur de collection (Guide de programmation C#)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Un <xref:System.Collections.Generic.Dictionary%602> contient une collection de paires clé\/valeur.  Sa méthode <xref:System.Collections.Generic.Dictionary%602.Add%2A> accepte deux paramètres, un pour la clé et un autre pour la valeur.  Pour initialiser un <xref:System.Collections.Generic.Dictionary%602> ou toute collection dont la méthode `Add` accepte plusieurs paramètres, mettez chaque jeu de paramètres entre accolades comme dans l'exemple suivant.  
  
## Exemple  
 Dans l'exemple de code suivant, un <xref:System.Collections.Generic.Dictionary%602> est initialisé avec les instances de type `StudentName`.  
  
 [!code-cs[csProgGuideLINQ#34](../../../csharp/programming-guide/arrays/codesnippet/CSharp/how-to-initialize-a-dictionary-with-a-collection-initializer_1.cs)]  
  
 Notez les deux paires d'accolades dans chaque élément de la collection.  Les accolades les plus à l'intérieur encadrent l'initialiseur d'objet pour `StudentName` et les accolades les plus à l'extérieur encadrent l'initialiseur pour la paire clé\/valeur qui sera ajoutée au <xref:System.Collections.Generic.Dictionary%602> `students`.  Enfin, l'initialiseur de collection pour le dictionnaire est entièrement entre accolades.  
  
## Compilation du code  
 Pour exécuter ce code, copiez et collez la classe dans un projet d'application console Visual C\# qui a été créé dans [!INCLUDE[vs_current_short](../../../csharp/programming-guide/classes-and-structs/includes/vs_current_short_md.md)].  Par défaut, ce projet concerne la version 3.5 du [!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort_md.md)] et il possède une référence à System.Core.dll et une directive using pour System.Linq.  Si une ou plusieurs de ces spécifications sont absentes du projet, vous pouvez les ajouter manuellement.  Pour plus d'informations, consultez [How to: Create a LINQ Project](../Topic/How%20to:%20Create%20a%20LINQ%20Project.md).  
  
## Voir aussi  
 [Guide de programmation C\#](../../../csharp/programming-guide/index.md)   
 [Initialiseurs d'objets et de collections](../../../csharp/programming-guide/classes-and-structs/object-and-collection-initializers.md)