---
title: "G&#233;n&#233;riques dans le runtime (Guide de programmation&#160;C#) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.technology: 
  - "devlang-csharp"
ms.topic: "article"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "génériques (C#), au moment de l'exécution"
ms.assetid: 119df7e6-9ceb-49df-af36-24f8f8c0747f
caps.latest.revision: 18
author: "BillWagner"
ms.author: "wiwagn"
caps.handback.revision: 18
---
# G&#233;n&#233;riques dans le runtime (Guide de programmation&#160;C#)
Lorsqu'un type ou une méthode générique est compilé dans le langage intermédiaire Microsoft \(MSIL\), il \(elle\) contient des métadonnées qui l'identifient comme ayant des paramètres de type.  La façon dont le MSIL d'un type générique est utilisé diffère selon que le paramètre de type fourni est un type valeur ou référence.  
  
 Lorsqu'un type générique est construit en premier avec un type valeur comme paramètre, le runtime crée un type générique spécialisé avec le paramètre fourni ou les paramètres substitués aux emplacements appropriés dans le MSIL.  Des types génériques spécialisés sont créés une fois pour chaque type valeur unique qui est utilisé comme paramètre.  
  
 Par exemple, supposons que votre code de programme ait déclaré une pile construite d'entiers :  
  
 [!code-cs[csProgGuideGenerics#42](../../../csharp/programming-guide/generics/codesnippet/csharp/generics-in-the-run-time_1.cs)]  
  
 À ce stade, le runtime génère une version spécialisée de la classe <xref:System.Collections.Generic.Stack%601> classe dont l'entier a été substitué correctement à son paramètre.  Maintenant, chaque fois que le code de programme utilise une pile d'entiers, le runtime réutilise la classe <xref:System.Collections.Generic.Stack%601> spécialisée générée.  Dans l'exemple suivant, deux instances d'une pile d'entiers sont créées, et elles partagent une instance unique du code `Stack<int>` :  
  
 [!code-cs[csProgGuideGenerics#43](../../../csharp/programming-guide/generics/codesnippet/csharp/generics-in-the-run-time_2.cs)]  
  
 Toutefois, supposons qu'une autre classe <xref:System.Collections.Generic.Stack%601> avec un type valeur différent tel qu'un `long` ou une structure définie par l'utilisateur comme son paramètre est créée à un autre endroit dans votre code.  Le runtime génère alors une autre version du type générique et substitue un `long` aux emplacements appropriés dans le MSIL.  Les conversions ne sont plus nécessaires parce que chaque classe générique spécialisée contient le type valeur en mode natif.  
  
 Les génériques fonctionnent un peu différemment pour les types référence.  La première fois qu'un type générique est construit avec un type référence quelconque, le runtime crée un type générique spécialisé avec les références objet substituées pour les paramètres dans le MSIL.  Puis, chaque fois qu'un type construit est instancié avec un type référence comme son paramètre, indépendamment de son type, le runtime réutilise la version spécialisée créée précédemment pour le type générique.  Ceci est possible parce que toutes les références ont la même taille.  
  
 Par exemple, supposons que vous ayez deux types référence, une classe `Customer` et une classe `Order`, et supposons également que vous ayez créé une pile de types `Customer` :  
  
 [!code-cs[csProgGuideGenerics#47](../../../csharp/programming-guide/generics/codesnippet/csharp/generics-in-the-run-time_3.cs)]  
  
 [!code-cs[csProgGuideGenerics#44](../../../csharp/programming-guide/generics/codesnippet/csharp/generics-in-the-run-time_4.cs)]  
  
 À ce stade, le runtime génère une version spécialisée de la classe <xref:System.Collections.Generic.Stack%601> qui stocke des références d'objet qui seront remplies ultérieurement au lieu de stocker des données.  Supposons que la ligne suivante de code crée une pile d'un autre type référence, qui est nommée `Order` :  
  
 [!code-cs[csProgGuideGenerics#45](../../../csharp/programming-guide/generics/codesnippet/csharp/generics-in-the-run-time_5.cs)]  
  
 Contrairement aux types valeur, une autre version spécialisée de la classe <xref:System.Collections.Generic.Stack%601> n'est pas créée pour le type `Order`.  À la place, une instance de la version spécialisée de la classe <xref:System.Collections.Generic.Stack%601> est créée et la variable `orders` est définie pour la référencer.  Supposons que vous ayez rencontré ensuite une ligne de code pour créer une pile d'un type `Customer` :  
  
 [!code-cs[csProgGuideGenerics#46](../../../csharp/programming-guide/generics/codesnippet/csharp/generics-in-the-run-time_6.cs)]  
  
 Comme avec l'utilisation précédente de la classe <xref:System.Collections.Generic.Stack%601> créée à l'aide du type `Order`, une autre instance de la classe <xref:System.Collections.Generic.Stack%601> spécialisée est créée.  Les pointeurs contenus ici sont configurés pour référencer une zone de mémoire de la taille d'un type `Customer`.  Dans la mesure où le nombre de types référence peut varier de manière importante d'un programme à l'autre, l'implémentation C\# de génériques réduit sensiblement le volume du code en ramenant à une unité le nombre de classes spécialisées créées par le compilateur pour les classes génériques de types référence.  
  
 De plus, lorsqu'une classe C\# générique est instanciée à l'aide d'un paramètre de type valeur ou référence, la réflexion peut l'interroger au moment de l'exécution, et son type réel ainsi que son paramètre de type peuvent être vérifiés.  
  
## Voir aussi  
 <xref:System.Collections.Generic>   
 [Guide de programmation C\#](../../../csharp/programming-guide/index.md)   
 [Introduction aux génériques](../../../csharp/programming-guide/generics/introduction-to-generics.md)   
 [Génériques](../Topic/Generics%20in%20the%20.NET%20Framework.md)