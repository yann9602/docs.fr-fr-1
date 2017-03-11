---
title: "Constructeurs statiques (Guide de programmation C#) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.technology: 
  - "devlang-csharp"
ms.topic: "article"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "constructeurs (C#), statiques"
  - "constructeurs statiques (C#)"
ms.assetid: 151ec95e-3c4d-4ed7-885d-95b7a3be2e7d
caps.latest.revision: 23
author: "BillWagner"
ms.author: "wiwagn"
caps.handback.revision: 23
---
# Constructeurs statiques (Guide de programmation C#)
Un constructeur statique est utilisé pour initialiser n'importe quelle donnée [statique](../../../csharp/language-reference/keywords/static.md), ou pour effectuer une action particulière devant être effectuée une seule fois.  Il est appelé automatiquement avant que la première instance soit créée ou que des membres statiques soient référencés.  
  
 [!code-cs[csProgGuideObjects#14](../../../csharp/programming-guide/classes-and-structs/codesnippet/csharp/static-constructors_1.cs)]  
  
 Les constructeurs statiques ont les propriétés suivantes :  
  
-   Un constructeur statique n'accepte pas de modificateurs d'accès ni de paramètres.  
  
-   Un constructeur statique est appelé automatiquement pour initialiser la [classe](../../../csharp/language-reference/keywords/class.md) avant que la première instance soit créée ou que tous les membres statiques sont référencés.  
  
-   Il ne peut pas être appelé directement.  
  
-   L'utilisateur n'a aucun contrôle sur le moment où le constructeur statique est exécuté dans le programme.  
  
-   Exemple typique d'utilisation d'un constructeur statique : lorsque la classe utilise un fichier journal et que le constructeur est utilisé pour écrire des entrées dans ce fichier.  
  
-   Les constructeurs statiques sont également utiles lors de la création de classes wrapper pour du code non managé, lorsque le constructeur peut appeler la méthode `LoadLibrary`.  
  
-   Si un constructeur statique lève une exception, l'exécution ne l'appelle pas une deuxième fois et le type reste non initialisé pendant la durée de vie du domaine d'application dans lequel votre programme s'exécute.  
  
## Exemple  
 Dans cet exemple, la classe `Bus` a un constructeur static.  Lorsque la première instance de `Bus` est créée \(`bus1`\), le constructeur static est appelé pour initialiser la classe.  L'exemple de sortie vérifie que le constructeur static est exécuté une seule fois, même si deux instances de `Bus` sont créées, et qu'il est exécuté avant le constructeur d'instance ne le soit.  
  
 [!code-cs[csProgGuideObjects#15](../../../csharp/programming-guide/classes-and-structs/codesnippet/csharp/static-constructors_2.cs)]  
  
## Voir aussi  
 [Guide de programmation C\#](../../../csharp/programming-guide/index.md)   
 [Classes et structs](../../../csharp/programming-guide/classes-and-structs/index.md)   
 [Constructeurs](../../../csharp/programming-guide/classes-and-structs/constructors.md)   
 [Classes statiques et membres de classe statique](../../../csharp/programming-guide/classes-and-structs/static-classes-and-static-class-members.md)   
 [Destructeurs](../../../csharp/programming-guide/classes-and-structs/destructors.md)