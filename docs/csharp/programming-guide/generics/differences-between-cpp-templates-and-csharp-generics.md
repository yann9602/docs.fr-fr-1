---
title: "Diff&#233;rences entre les templates&#160;C++ et les g&#233;n&#233;riques&#160;C# (Guide de programmation C#) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
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
  - "génériques (C#), comparés aux modèles C++"
ms.assetid: 1da6beeb-d4a4-4da0-87b7-0cfbe04920b7
caps.latest.revision: 14
caps.handback.revision: 14
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Diff&#233;rences entre les templates&#160;C++ et les g&#233;n&#233;riques&#160;C# (Guide de programmation C#)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Les génériques C\# et les modèles C\+\+ sont des fonctionnalités de langage qui assurent la prise en charge des types paramétrés.  Il existe toutefois de nombreuses différences entre les deux.  Au niveau de la syntaxe, les génériques C\# offrent une approche plus simple aux types paramétrés, sans la complexité des modèles C\+\+.  De plus, C\# n'essaie pas d'offrir toutes les fonctionnalités fournies par les modèles C\+\+.  Au niveau de l'implémentation, la différence principale est que les substitutions de type générique C\# sont exécutées pendant l'exécution et que les informations de type générique sont ainsi conservées pour les objets instanciés.  Pour plus d'informations, consultez [Génériques dans le runtime](../../../csharp/programming-guide/generics/generics-in-the-run-time.md).  
  
 Les différences clés entre génériques C\# et modèles C\+\+ sont les suivantes :  
  
-   Les génériques C\# n'offrent pas la même souplesse que les modèles C\+\+.  Par exemple, il n'est pas possible d'appeler des opérateurs arithmétiques dans une classe générique C\#, bien qu'il soit possible d'appeler des opérateurs définis par l'utilisateur.  
  
-   C\# n'autorise pas les paramètres de modèle sans type, tels que `template C<int i> {}`.  
  
-   C\# ne prend pas en charge la spécialisation explicite, à savoir l'implémentation personnalisée d'un modèle pour un type spécifique.  
  
-   C\# ne prend pas en charge la spécialisation partielle, à savoir l'implémentation personnalisée d'un sous\-ensemble des arguments de type.  
  
-   C\# n'autorise pas le paramètre de type à être utilisé comme classe de base pour le type générique.  
  
-   C\# ne permet pas aux paramètres de type d'avoir des types par défaut.  
  
-   En C\#, un paramètre de type générique ne peut pas être un générique, bien que des types construits puissent être utilisés comme des génériques.  C\+\+ autorise les paramètres de modèle.  
  
-   C\+\+ autorise un code qui peut ne pas être valide pour tous les paramètres de type dans le modèle, dont on vérifie ensuite qu'il utilise le type spécifique utilisé comme paramètre de type.  C\# requiert que le code d'une classe soit écrit de telle manière qu'il fonctionnera avec tout type qui satisfait aux contraintes.  Par exemple, il est possible en C\+\+ d'écrire une fonction qui utilise les opérateurs arithmétiques `+` et `-` sur les objets du paramètre de type, qui produira une erreur au moment de l'instanciation du modèle avec un type qui ne prend pas en charge ces opérateurs.  C\# n'autorise pas ceci. Les seules constructions de langage autorisées sont celles qui peuvent être déduites des contraintes.  
  
## Voir aussi  
 [Guide de programmation C\#](../../../csharp/programming-guide/index.md)   
 [Introduction aux génériques](../../../csharp/programming-guide/generics/introduction-to-generics.md)   
 [Modèles](/visual-cpp/cpp/templates-cpp)