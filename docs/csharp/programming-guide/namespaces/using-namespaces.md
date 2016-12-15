---
title: "Utilisation d&#39;espaces de noms (Guide de programmation C#) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "cs.names"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "noms qualifiés complets (C#)"
  - "espaces de noms (C#), comment utiliser"
ms.assetid: 1fe8bf39-addc-438a-bd9e-86410e32381d
caps.latest.revision: 26
caps.handback.revision: 26
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Utilisation d&#39;espaces de noms (Guide de programmation C#)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Les espaces de noms sont énormément employés dans les programmes C\# de deux manières.  Premièrement, les classes .NET Framework utilisent des espaces de noms pour organiser ses nombreuses classes.  Deuxièmement, déclarer ses propres espaces de noms peut aider à contrôler la portée des noms de classes et de méthodes dans les projets de programmation plus volumineux.  
  
## Accès aux espaces de noms  
 La plupart des applications C\# commencent par une section de directives `using`.  Cette section répertorie les espaces de noms que l'application utilisera fréquemment, et évite au programmeur de devoir spécifier un nom qualifié complet chaque fois qu'une méthode contenue à l'intérieur est utilisée.  
  
 Par exemple, en incluant la ligne :  
  
 [!code-cs[csProgGuide#1](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/using-namespaces_1.cs)]  
  
 Au démarrage d'un programme, le programmeur peut utiliser le code :  
  
 [!code-cs[csProgGuide#31](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/using-namespaces_2.cs)]  
  
 à la place de :  
  
 [!code-cs[csProgGuide#30](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/using-namespaces_3.cs)]  
  
## Alias d'espaces de noms  
 Les [using, directive](../../../csharp/language-reference/keywords/using-directive.md) peuvent également permettre de créer un alias pour un [espace de noms](../../../csharp/language-reference/keywords/namespace.md).  Par exemple, si vous utilisez un espace de noms écrit qui contient des espaces de noms imbriqués, déclarer un alias vous offre un moyen pratique d'en référencer un en particulier, comme suit :  
  
 [!code-cs[csProgGuideNamespaces#7](../../../csharp/programming-guide/namespaces/codesnippet/CSharp/using-namespaces_4.cs)]  
  
## Utilisation d'espaces de noms pour contrôler la portée  
 Le mot clé `namespace` permet de déclarer une portée.  La capacité de créer des portées dans votre projet aide à organiser le code et vous permet de créer des types globalement uniques.  Dans l'exemple suivant, une classe intitulée `SampleClass` est définie dans deux espaces de noms, l'une étant imbriquée dans l'autre.  [. Opérateur](../../../csharp/language-reference/operators/member-access-operator.md) est utilisé pour distinguer la méthode appelée.  
  
 [!code-cs[csProgGuideNamespaces#8](../../../csharp/programming-guide/namespaces/codesnippet/CSharp/using-namespaces_5.cs)]  
  
## Noms complets  
 Les espaces de noms et les types ont des titres uniques décrits par des noms qualifiés complets qui indiquent une hiérarchie logique.  Par exemple, l'instruction `A.B` implique que `A` est le nom de l'espace de noms ou du type, et que `B` est imbriqué à l'intérieur.  
  
 Dans l'exemple suivant, on trouve des classes et des espaces de noms imbriqués.  Le nom qualifié complet est indiqué sous la forme d'un commentaire à la suite de chaque entité.  
  
 [!code-cs[csProgGuideNamespaces#9](../../../csharp/programming-guide/namespaces/codesnippet/CSharp/using-namespaces_6.cs)]  
  
 Dans le segment de code précédent :  
  
-   L'espace de noms `N1` est membre de l'espace de noms global.  Son nom qualifié complet est `N1`.  
  
-   L'espace de noms `N2` est membre de `N1`.  Son nom qualifié complet est `N1.N2`.  
  
-   La classe `C1` est membre de `N1`.  Son nom qualifié complet est `N1.C1`.  
  
-   Le nom de classe `C2` est utilisé à deux reprises dans ce code.  Cependant, les noms qualifiés complets sont uniques.  La première instance de `C2` est déclarée dans `C1` ; par conséquent, son nom qualifié complet est : `N1.C1.C2`.  La deuxième instance de `C2` est déclarée dans un espace de noms `N2` ; par conséquent, son nom qualifié complet est `N1.N2.C2`.  
  
 En utilisant le segment de code précédent, vous pouvez ajouter une nouvelle classe membre `C3` à l'espace de noms `N1.N2`, comme suit :  
  
 [!code-cs[csProgGuideNamespaces#10](../../../csharp/programming-guide/namespaces/codesnippet/CSharp/using-namespaces_7.cs)]  
  
 En général, utilisez `::` pour référencer un alias d'espace de noms ou `global::` pour référencer l'espace de noms global et `.` pour qualifier des types ou des membres.  
  
 C'est une erreur d'utiliser `::` avec un alias qui référence un type au lieu d'un espace de noms.  Par exemple :  
  
 [!code-cs[csProgGuideNamespaces#11](../../../csharp/programming-guide/namespaces/codesnippet/CSharp/using-namespaces_8.cs)]  
  
 [!code-cs[csProgGuideNamespaces#12](../../../csharp/programming-guide/namespaces/codesnippet/CSharp/using-namespaces_9.cs)]  
  
 N'oubliez pas que le mot `global` n'est pas un alias prédéfini. Par conséquent, `global.X` n'a pas de signification particulière.  Il acquiert une signification particulière uniquement lorsqu'il est utilisé avec `::`.  
  
 L'avertissement du compilateur CS0440 est généré si vous définissez un alias nommé global, car `global::` référence toujours l'espace de noms global et pas un alias.  Par exemple, la ligne suivante génère l'avertissement  :  
  
 [!code-cs[csProgGuideNamespaces#13](../../../csharp/programming-guide/namespaces/codesnippet/CSharp/using-namespaces_10.cs)]  
  
 L'utilisation de `::` avec des alias est une bonne idée et protège contre l'introduction inattendue de types supplémentaires.  Prenons l'exemple suivant :  
  
 [!code-cs[csProgGuideNamespaces#14](../../../csharp/programming-guide/namespaces/codesnippet/CSharp/using-namespaces_11.cs)]  
  
 [!code-cs[csProgGuideNamespaces#15](../../../csharp/programming-guide/namespaces/codesnippet/CSharp/using-namespaces_12.cs)]  
  
 Il fonctionne, mais si un type nommé `Alias` est introduit par la suite, `Alias.` crée une liaison avec ce type à la place.  L'utilisation de `Alias::Exception` permet de s'assurer que cet `Alias` est traité comme un alias d'espace de noms et non pris pour un type.  
  
 Consultez la rubrique [Comment : utiliser l'alias d'espace de noms global](../../../csharp/programming-guide/namespaces/how-to-use-the-global-namespace-alias.md) pour plus d'informations sur l'alias `global`.  
  
## Voir aussi  
 [Guide de programmation C\#](../../../csharp/programming-guide/index.md)   
 [Espaces de noms](../../../csharp/programming-guide/namespaces/index.md)   
 [Mots clés d'espaces de noms](../../../csharp/language-reference/keywords/namespace-keywords.md)   
 [. Opérateur](../../../csharp/language-reference/operators/member-access-operator.md)   
 [::, opérateur](../../../csharp/language-reference/operators/namespace-alias-qualifer.md)   
 [extern](../../../csharp/language-reference/keywords/extern.md)