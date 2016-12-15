---
title: "Comment&#160;: interroger une collection d&#39;objets (Guide de programmation&#160;C#) | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
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
  - "interroger une collection d'objets (C#)"
  - "requêtes (LINQ en C#), collections d'objets"
  - "expressions de requête (LINQ en C#), collections d'objets"
ms.assetid: 122d1e3b-1604-4add-b6b4-b84530a77b6b
caps.latest.revision: 8
caps.handback.revision: 8
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Comment&#160;: interroger une collection d&#39;objets (Guide de programmation&#160;C#)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Cet exemple montre comment effectuer une requête simple sur une liste d'objets `Student`.  Chaque objet `Student` contient des informations de base à propos de l'étudiant, et une liste qui représente les notes de l'étudiant lors de quatre examens.  
  
 Cette application sert de cadre pour de nombreux autres exemples dans cette section qui utilisent la même source de données `students` .  
  
## Exemple  
 La requête suivante retourne les étudiants qui ont reçu une note supérieure ou égale à 90 lors de leur premier examen.  
  
 [!code-cs[csProgGuideLINQ#15](../../../csharp/programming-guide/arrays/codesnippet/CSharp/how-to-query-a-collection-of-objects_1.cs)]  
  
 Cette requête est volontairement simple pour vous permettre d'expérimenter.  Par exemple, vous pouvez essayer plus de prédicats dans la clause `where` ou utiliser une clause `orderby` pour trier les résultats.  
  
## Compilation du code  
  
-   Créez un projet [!INCLUDE[vs_current_short](../../../csharp/programming-guide/classes-and-structs/includes/vs_current_short_md.md)] qui cible la version 3.5 du .NET Framework.  Par défaut, le projet possède une référence à System.Core.dll et une directive `using` pour l'espace de noms System.Linq.  
  
-   Copiez le code dans votre projet.  
  
-   Appuyez sur F5 pour compiler et exécuter le programme.  
  
-   Appuyez sur une touche pour quitter la fenêtre de console.  
  
## Voir aussi  
 [Expressions de requête \(LINQ\)](../../../csharp/programming-guide/linq-query-expressions/index.md)