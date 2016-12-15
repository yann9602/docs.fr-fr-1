---
title: "Comment&#160;: d&#233;clarer, instancier et utiliser un d&#233;l&#233;gu&#233; (Guide de programmation C#) | Microsoft Docs"
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
  - "délégués (C#), déclarer et instancier"
ms.assetid: 61c4895f-f785-48f8-8bfe-db73b411c4ae
caps.latest.revision: 21
caps.handback.revision: 21
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Comment&#160;: d&#233;clarer, instancier et utiliser un d&#233;l&#233;gu&#233; (Guide de programmation C#)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Dans C\# 1.0 et dans les versions ultérieures, les délégués peuvent être déclarés comme indiqué dans l'exemple suivant.  
  
 [!code-cs[csProgGuideDelegates#13](../../../csharp/programming-guide/delegates/codesnippet/CSharp/how-to-declare-instantiate-and-use-a-delegate_1.cs)]  
  
 [!code-cs[csProgGuideDelegates#14](../../../csharp/programming-guide/delegates/codesnippet/CSharp/how-to-declare-instantiate-and-use-a-delegate_2.cs)]  
  
 C\# 2.0 offre un moyen plus simple d'écrire la déclaration précédente, comme indiqué dans l'exemple suivant.  
  
 [!code-cs[csProgGuideDelegates#32](../../../csharp/programming-guide/delegates/codesnippet/CSharp/how-to-declare-instantiate-and-use-a-delegate_3.cs)]  
  
 Dans C\# 2.0 et les versions ultérieures, il est également possible d'utiliser une méthode anonyme pour déclarer et initialiser un délégué [](../../../csharp/language-reference/keywords/delegate.md "delegate (C# Reference)"), comme indiqué dans l'exemple suivant.  
  
 [!code-cs[csProgGuideDelegates#15](../../../csharp/programming-guide/delegates/codesnippet/CSharp/how-to-declare-instantiate-and-use-a-delegate_4.cs)]  
  
 Dans C\# 3.0 et les versions ultérieures, les délégués peuvent également être déclarés et instanciés à l'aide d'une expression lambda, comme indiqué dans l'exemple suivant.  
  
 [!code-cs[csProgGuideDelegates#31](../../../csharp/programming-guide/delegates/codesnippet/CSharp/how-to-declare-instantiate-and-use-a-delegate_5.cs)]  
  
 Pour plus d'informations, consultez [Expressions lambda](../../../csharp/programming-guide/statements-expressions-operators/lambda-expressions.md).  
  
 L'exemple suivant illustre la déclaration, l'instanciation et l'utilisation d'un délégué.  La classe `BookDB` encapsule une base de données de librairie qui gère une base de données de livres.  Elle expose une méthode `ProcessPaperbackBooks`, qui recherche tous les livres de poche dans la base de données et appelle un délégué pour chacun d'entre eux.  Le type `delegate` qui est utilisé est nommé `ProcessBookDelegate`.  La classe `Test` utilise cette classe pour imprimer les titres et le prix moyen des livres de poche.  
  
 L'utilisation de délégués favorise une bonne séparation des fonctionnalités entre la base de données de la librairie et le code client.  Le code client ignore complètement comment les livres sont stockés et comment le code libraire recherche les livres de poche.  Inversement, le code libraire ignore quel traitement est effectué sur les livres de poche lorsqu'il les a trouvés.  
  
## Exemple  
 [!code-cs[csProgGuideDelegates#12](../../../csharp/programming-guide/delegates/codesnippet/CSharp/how-to-declare-instantiate-and-use-a-delegate_6.cs)]  
  
## Programmation fiable  
  
-   Déclaration d'un délégué.  
  
     L'instruction suivante déclare un nouveau type délégué.  
  
     [!code-cs[csProgGuideDelegates#16](../../../csharp/programming-guide/delegates/codesnippet/CSharp/how-to-declare-instantiate-and-use-a-delegate_7.cs)]  
  
     Chaque type délégué décrit le nombre et les types des arguments, ainsi que le type de la valeur de retour des méthodes qu'il peut encapsuler.  Chaque fois qu'un nouvel ensemble de types d'argument ou qu'un nouveau type de valeur de retour est requis, un nouveau type délégué doit être déclaré.  
  
-   Instanciation d'un délégué.  
  
     Après qu'un type délégué a été déclaré, un objet délégué doit être créé et associé à une méthode particulière.  Dans l'exemple précédent, pour ce faire, vous passez la méthode `PrintTitle` à la méthode `ProcessPaperbackBooks` comme dans l'exemple suivant :  
  
     [!code-cs[csProgGuideDelegates#17](../../../csharp/programming-guide/delegates/codesnippet/CSharp/how-to-declare-instantiate-and-use-a-delegate_8.cs)]  
  
     Cela crée un objet de délégué associé à la méthode [statique](../../../csharp/language-reference/keywords/static.md) `Test.PrintTitle`.  De la même manière, la méthode non statique `AddBookToTotal` sur l'objet `totaller` est passée comme dans l'exemple suivant :  
  
     [!code-cs[csProgGuideDelegates#18](../../../csharp/programming-guide/delegates/codesnippet/CSharp/how-to-declare-instantiate-and-use-a-delegate_9.cs)]  
  
     Dans les deux cas, un nouvel objet délégué est passé à la méthode `ProcessPaperbackBooks`.  
  
     Après qu'un délégué est créé, la méthode à laquelle il est associé ne change jamais ; les objets délégués sont immuables.  
  
-   Appel d'un délégué.  
  
     Après qu'un objet délégué est créé, il est normalement transmis à un autre code qui appellera le délégué.  Vous pouvez appeler un objet délégué en utilisant son nom, suivi, entre parenthèses, des arguments qui doivent être transmis au délégué.  Un exemple d'appel de délégué est fourni ci\-dessous :  
  
     [!code-cs[csProgGuideDelegates#19](../../../csharp/programming-guide/delegates/codesnippet/CSharp/how-to-declare-instantiate-and-use-a-delegate_10.cs)]  
  
     Un délégué peut faire l'objet d'un appel synchrone, comme dans cet exemple, ou d'un appel asynchrone à l'aide des méthodes `BeginInvoke` et `EndInvoke`.  
  
## Voir aussi  
 [Guide de programmation C\#](../../../csharp/programming-guide/index.md)   
 [Événements](../../../csharp/programming-guide/events/index.md)   
 [Délégués](../../../csharp/programming-guide/delegates/index.md)