---
title: "Utilisation d&#39;exceptions (Guide de programmation C#) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.technology: 
  - "devlang-csharp"
ms.topic: "article"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "gestion d'exceptions (C#), à propos de la gestion d'exceptions"
  - "exceptions (C#), à propos des exceptions"
ms.assetid: 71472c62-320a-470a-97d2-67995180389d
caps.latest.revision: 15
author: "BillWagner"
ms.author: "wiwagn"
caps.handback.revision: 15
---
# Utilisation d&#39;exceptions (Guide de programmation C#)
En C\#, les erreurs qui se produisent dans le programme au moment de l'exécution sont propagées à travers le programme à l'aide du mécanisme des exceptions.  Les exceptions sont levées par le code qui rencontre une erreur et interceptées par le code qui peut corriger l'erreur.  Les exceptions peuvent être levées par le CLR \(Common Language Runtime\) du .NET Framework, ou par code dans un programme.  Une fois qu'une exception est levée, elle se propage jusqu'en haut de pile des appels, jusqu'à ce qu'une instruction `catch` soit trouvée pour l'exception.  Les exceptions non interceptées sont traitées par un gestionnaire d'exceptions générique fourni par le système qui affiche une boîte de dialogue.  
  
 Les exceptions sont représentées par des classes dérivées de <xref:System.Exception>.  Cette classe identifie le type d'exception et contient les propriétés détaillées sur l'exception.  Lever une exception implique de créer une instance d'une classe dérivée d'exception, de configurer les propriétés de l'exception, le cas échéant, puis de lever l'objet à l'aide du mot clé `throw`.  Par exemple :  
  
 [!code-cs[csProgGuideExceptions#1](../../../csharp/programming-guide/exceptions/codesnippet/csharp/using-exceptions_1.cs)]  
  
 Après avoir levé une exception, le runtime vérifie l'instruction actuelle pour voir si elle se trouve au sein d'un bloc `try`.  Si tel est le cas, tous les blocs `catch` associés au bloc `try` font l'objet d'un contrôle permettant de déterminer s'ils peuvent intercepter l'exception.  Les blocs `Catch` spécifient généralement des types d'exception ; si le type du bloc `catch` est identique à celui de l'exception, ou d'une classe de base de l'exception, le bloc `catch` peut gérer la méthode.  Par exemple :  
  
 [!code-cs[csProgGuideExceptions#2](../../../csharp/programming-guide/exceptions/codesnippet/csharp/using-exceptions_2.cs)]  
  
 Si l'instruction qui lève une exception ne se trouve pas à l'intérieur d'un bloc `try`, ou si le bloc `try` qui la contient n'a pas de bloc `catch` correspondant, le runtime vérifie que la méthode d'appel dispose d'une instruction `try` et de blocs `catch`.  Le runtime continue jusqu'à la pile appelante, à la recherche d'un bloc `catch` compatible.  Une fois le bloc `catch` trouvé et exécuté, le contrôle est passé à l'instruction suivante après le bloc `catch`.  
  
 Une instruction `try` peut contenir plusieurs blocs `catch`.  La première instruction `catch` qui peut gérer l'exception est exécutée ; toutes les instructions `catch` suivantes, même compatibles, sont ignorées.  Par conséquent, les blocs catch doivent toujours être classés du plus spécifique \(ou plus dérivé\) au moins spécifique.  Par exemple :  
  
 [!code-cs[csProgGuideExceptions#3](../../../csharp/programming-guide/exceptions/codesnippet/csharp/using-exceptions_3.cs)]  
  
 Avant que le bloc `catch` ne soit exécuté, le runtime vérifie la présence de blocs `finally`.  Les blocs `Finally` permettent au programmeur de nettoyer tout état ambigu qui pourrait subsister après l'abandon d'un bloc `try` ou de libérer les ressources externes \(telles que les handles graphiques, les connexions de bases de données ou les flux de fichiers\) sans attendre que le garbage collector du runtime ne finalise les objets.  Par exemple :  
  
 [!code-cs[csProgGuideExceptions#4](../../../csharp/programming-guide/exceptions/codesnippet/csharp/using-exceptions_4.cs)]  
  
 Si `WriteByte()` a levé une exception, le code du deuxième bloc `try` qui essaie de rouvrir le fichier échoue si `file.Close()` n'est pas appelé et le fichier reste verrouillé.  Étant donné que les blocs `finally` sont exécutés même lorsqu'une exception est levée, le bloc `finally` de l'exemple précédent autorise le fichier à être fermé correctement et permet d'éviter une erreur.  
  
 Si aucun bloc `catch` compatible n'est trouvé sur la pile des appels après qu'une exception ait été levée, l'une des trois situations suivantes se produit :  
  
-   Si l'exception se trouve dans un destructeur, le destructeur est abandonné et le destructeur de base, s'il y en a un, est appelé.  
  
-   Si la pile des appels contient un constructeur statique, ou un initialiseur de champ statique, une <xref:System.TypeInitializationException> est levée, avec l'exception d'origine assignée à la propriété <xref:System.Exception.InnerException%2A> de la nouvelle exception.  
  
-   Si le début du thread est atteint, le thread est terminé.  
  
## Voir aussi  
 [Guide de programmation C\#](../../../csharp/programming-guide/index.md)   
 [Exceptions et gestion des exceptions](../../../csharp/programming-guide/exceptions/exceptions-and-exception-handling.md)