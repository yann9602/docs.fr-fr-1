---
title: "Comment&#160;: impl&#233;menter et appeler une m&#233;thode d&#39;extension personnalis&#233;e (Guide de programmation&#160;C#) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.technology: 
  - "devlang-csharp"
ms.topic: "article"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "méthodes d'extension (C#), implémenter et appeler"
ms.assetid: 7dab2a56-cf8e-4a47-a444-fe610a02772a
caps.latest.revision: 15
author: "BillWagner"
ms.author: "wiwagn"
caps.handback.revision: 15
---
# Comment&#160;: impl&#233;menter et appeler une m&#233;thode d&#39;extension personnalis&#233;e (Guide de programmation&#160;C#)
Cette rubrique indique comment implémenter vos propres méthodes d'extension pour le n'importe quel type dans le [.NET Framework Class Library](http://go.microsoft.com/fwlink/?LinkID=217856), ou tout autre type. NET que vous souhaitez étendre.  Le code client peut utiliser vos méthodes d'extension en ajoutant une référence à la DLL qui les contient et en ajoutant une directive [using](../../../csharp/language-reference/keywords/using-directive.md) qui spécifie l'espace de noms dans lequel les méthodes d'extension sont définies.  
  
### pour définir et appeler la méthode d'extension  
  
1.  Définissez une [classe](../../../csharp/programming-guide/classes-and-structs/static-classes-and-static-class-members.md) statique pour contenir la méthode d'extension.  
  
     La classe doit être visible par le code client.  Pour plus d'informations sur les règles d'accessibilité, consultez [Modificateurs d'accès](../../../csharp/programming-guide/classes-and-structs/access-modifiers.md).  
  
2.  Implémentez la méthode d'extension comme une méthode statique avec au moins la même visibilité que la classe conteneur.  
  
3.  Le premier paramètre de la méthode spécifie le type sur lequel fonctionne la méthode ; il doit être précédé du modificateur [this](../../../csharp/language-reference/keywords/this.md).  
  
4.  Dans le code appelant, ajoutez une directive `using` pour spécifier l'[espace de noms](../../../csharp/language-reference/keywords/namespace.md) qui contient la classe de méthode d'extension.  
  
5.  Appelez les méthodes comme s'il s'agissait de méthodes d'instance sur le type.  
  
     Notez que le premier paramètre n'est pas spécifié par le code appelant, car il représente le type sur lequel l'opérateur est appliqué et que le compilateur connaît déjà le type de votre objet.  Vous devez seulement fournir des arguments pour les paramètres 2 à `n`.  
  
## Exemple  
 L'exemple suivant implémente une méthode d'extension nommée `WordCount` dans la classe `CustomExtensions.StringExtension`.  La méthode fonctionne sur la classe <xref:System.String>, spécifiée comme premier paramètre de méthode.  L'espace de noms `CustomExtensions` est importé dans l'espace de noms de l'application et la méthode est appelée à l'intérieur de la méthode `Main`.  
  
 [!code-cs[csProgGuideExtensionMethods#1](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-implement-and-call-a-custom-extension-method_1.cs)]  
  
## Compilation du code  
 Pour exécuter ce code, copiez\-le et collez\-le dans un projet d'application console Visual C\# qui a été créé dans [!INCLUDE[vs_current_short](../../../csharp/programming-guide/classes-and-structs/includes/vs-current-short-md.md)].  Par défaut, ce projet cible la version 3.5 du [!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort-md.md)] et il possède une référence à System.Core.dll et une directive `using` pour System.Linq.  Si une ou plusieurs de ces spécifications sont absentes du projet, vous pouvez les ajouter manuellement.  Pour plus d'informations, consultez [How to: Create a LINQ Project](../Topic/How%20to:%20Create%20a%20LINQ%20Project.md).  
  
## Sécurité .NET Framework  
 Les méthodes d'extension ne sont pas particulièrement vulnérables en termes de sécurité.  Elles ne peuvent jamais être utilisées pour emprunter l'identité des méthodes existantes sur un type, car toutes les collisions de nom sont résolues en faveur de l'instance ou de la méthode statique définie par le type lui\-même.  Les méthodes d'extension ne peuvent pas accéder aux données privées dans la classe étendue.  
  
## Voir aussi  
 [Guide de programmation C\#](../../../csharp/programming-guide/index.md)   
 [Méthodes d'extension](../../../csharp/programming-guide/classes-and-structs/extension-methods.md)   
 [LINQ \(Language\-Integrated Query\)](../Topic/LINQ%20\(Language-Integrated%20Query\).md)   
 [Classes statiques et membres de classe statique](../../../csharp/programming-guide/classes-and-structs/static-classes-and-static-class-members.md)   
 [protégés](../../../csharp/language-reference/keywords/protected.md)   
 [interne](../../../csharp/language-reference/keywords/internal.md)   
 [public](../../../csharp/language-reference/keywords/public.md)   
 [this](../../../csharp/language-reference/keywords/this.md)   
 [espace de noms](../../../csharp/language-reference/keywords/namespace.md)