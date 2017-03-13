---
title: "Cr&#233;ation et lev&#233;e d&#39;exceptions (Guide de programmation&#160;C#) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.technology: 
  - "devlang-csharp"
ms.topic: "article"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "intercepter des exceptions (C#)"
  - "exceptions (C#), créer"
  - "exceptions (C#), lever"
  - "lever des exceptions (C#)"
ms.assetid: 6bbba495-a115-4c6d-90cc-1f4d7b5f39e2
caps.latest.revision: 28
author: "BillWagner"
ms.author: "wiwagn"
caps.handback.revision: 28
---
# Cr&#233;ation et lev&#233;e d&#39;exceptions (Guide de programmation&#160;C#)
Les exceptions sont utilisées pour indiquer qu'une erreur s'est produite pendant l'exécution du programme.  Les objets exception qui décrivent une erreur sont créés puis *levés* avec le mot clé [throw](../../../csharp/language-reference/keywords/throw.md).  Le runtime recherche ensuite le gestionnaire d'exceptions le plus compatible.  
  
 Les programmeurs doivent lever des exceptions lorsqu'une ou plusieurs des conditions suivantes est vraie :  
  
-   La méthode ne peut pas réaliser sa fonctionnalité définie.  
  
     Par exemple, si un paramètre de méthode possède une valeur non valide :  
  
     [!code-cs[csProgGuideExceptions#12](../../../csharp/programming-guide/exceptions/codesnippet/CSharp/creating-and-throwing-exceptions_1.cs)]  
  
-   Un appel inapproprié à un objet est fait, suivant l'état de l'objet.  
  
     Par exemple, en tentant d'écrire dans un fichier en lecture seule.  Dans les cas où un état d'objet n'autorise pas d'opération, levez une instance de <xref:System.InvalidOperationException> ou un objet basé sur une dérivation de cette classe.  Voici un exemple d'une méthode qui lève un objet <xref:System.InvalidOperationException> :  
  
     [!code-cs[csProgGuideExceptions#13](../../../csharp/programming-guide/exceptions/codesnippet/CSharp/creating-and-throwing-exceptions_2.cs)]  
  
-   Lorsqu'un argument de méthode provoque une exception.  
  
     Dans ce cas, l'exception d'origine doit être interceptée et une instance <xref:System.ArgumentException> doit être créée.  L'exception d'origine doit être passée au constructeur de <xref:System.ArgumentException> en tant que paramètre <xref:System.Exception.InnerException%2A> :  
  
     [!code-cs[csProgGuideExceptions#14](../../../csharp/programming-guide/exceptions/codesnippet/CSharp/creating-and-throwing-exceptions_3.cs)]  
  
 Les exceptions contiennent une propriété nommée <xref:System.Exception.StackTrace%2A>.  Cette chaîne contient le nom des méthodes sur la pile des appels actuelle, avec le nom de fichier et le numéro de ligne où l'exception a été levée pour chaque méthode.  Un objet <xref:System.Exception.StackTrace%2A> étant créé automatiquement par le Common Language Runtime \(CLR\) à partir du point de l'instruction `throw`, les exceptions doivent être levées à partir du point où la trace de la pile doit commencer.  
  
 Toutes les exceptions contiennent une propriété nommée <xref:System.Exception.Message%2A>.  Cette chaîne doit être configurée pour expliquer la raison de l'exception.  Notez que les informations sensibles du point de vue de la sécurité ne doivent pas être placées dans le texte du message.  Outre <xref:System.Exception.Message%2A>, <xref:System.ArgumentException> contient une propriété nommée <xref:System.ArgumentException.ParamName%2A> qui doit être définie au nom de l'argument qui a provoqué la levée de l'exception.  Dans le cas d'un accesseur Set de propriété, <xref:System.ArgumentException.ParamName%2A> doit avoir la valeur `value`.  
  
 Les membres de méthodes publiques et protégées doivent lever des exceptions dès qu'ils ne peuvent pas réaliser leur fonction prévue.  La classe d'exception qui est levée doit être l'exception la plus spécifique disponible répondant aux conditions d'erreur.  Ces exceptions doivent être documentées dans le cadre de la fonctionnalité de la classe ; les classes dérivées ou les mises à jour de la classe d'origine doivent conserver le même comportement afin d'assurer la compatibilité descendante.  
  
## Pratiques à éviter lors de la levée des exceptions  
 La liste suivante identifie les pratiques à éviter lors de la levée des exceptions :  
  
-   Les exceptions ne doivent pas être utilisées pour modifier le flux d'un programme dans le cadre d'une exécution ordinaire.  Les exceptions doivent être utilisées uniquement pour signaler et gérer les conditions d'erreur.  
  
-   Les exceptions ne doivent pas être retournées en tant que valeur de retour ou paramètre au lieu d'être levées.  
  
-   Ne levez pas intentionnellement <xref:System.Exception?displayProperty=fullName>, <xref:System.SystemException?displayProperty=fullName>, <xref:System.NullReferenceException?displayProperty=fullName> ou <xref:System.IndexOutOfRangeException?displayProperty=fullName> à partir de votre propre code source.  
  
-   Ne créez pas d'exceptions qui peuvent être levées en mode Debug mais pas en mode Release.  Pour identifier des erreurs d'exécution pendant la phase de développement, utilisez plutôt Debug Assert.  
  
## Définition de classes d'exceptions  
 Les programmes peuvent lever une classe d'exception prédéfinie dans l'espace de noms <xref:System> \(sauf dans les endroits précédemment notés\) ou créer leurs propres classes d'exception en les dérivant de <xref:System.Exception>.  Les classes dérivées doivent définir au moins quatre constructeurs : un constructeur par défaut, un qui définit la propriété du message et un qui définit les deux propriétés <xref:System.Exception.Message%2A> et <xref:System.Exception.InnerException%2A>.  Le quatrième constructeur est utilisé pour sérialiser l'exception.  Les nouvelles classes d'exception doivent être sérialisables.  Par exemple :  
  
 [!code-cs[csProgGuideExceptions#15](../../../csharp/programming-guide/exceptions/codesnippet/CSharp/creating-and-throwing-exceptions_4.cs)]  
  
 Les nouvelles propriétés doivent uniquement être ajoutées à la classe d'exceptions lorsque les données qu'elles fournissent sont utiles à la résolution de l'exception.  Si les nouvelles propriétés sont ajoutées à la classe d'exceptions dérivée, `ToString()` doit être substitué pour retourner les informations ajoutées.  
  
## Spécification du langage C\#  
 [!INCLUDE[CSharplangspec](../../../csharp/language-reference/keywords/includes/csharplangspec-md.md)]  
  
## Voir aussi  
 [Guide de programmation C\#](../../../csharp/programming-guide/index.md)   
 [Exceptions et gestion des exceptions](../../../csharp/programming-guide/exceptions/exceptions-and-exception-handling.md)   
 [Hiérarchie des exceptions](../Topic/Exception%20Hierarchy.md)   
 [Gestion des exceptions](../../../csharp/programming-guide/exceptions/exception-handling.md)