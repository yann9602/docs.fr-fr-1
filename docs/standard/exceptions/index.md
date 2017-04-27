---
title: "Gestion et levée d’exceptions | Microsoft Docs"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework-4.6
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-bcl
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- exceptions [.NET Framework], handling
- runtime, exceptions
- filtering exceptions
- errors [.NET Framework], exceptions
- exceptions [.NET Framework], throwing
- exceptions [.NET Framework]
- common language runtime, exceptions
ms.assetid: f99a1d29-a2a8-47af-9707-9909f9010735
caps.latest.revision: 16
author: mairaw
ms.author: mairaw
manager: wpickett
translationtype: Human Translation
ms.sourcegitcommit: c50b3e328998b65ec47efe6d7457b36116813c77
ms.openlocfilehash: c3b47e61da914ebbe1106fcf45465a13b0521bb4
ms.lasthandoff: 04/08/2017

---
# <a name="handling-and-throwing-exceptions"></a>Gestion et levée des exceptions
<a name="top"></a> Les applications doivent pouvoir gérer de manière cohérente les erreurs qui se produisent au moment de l'exécution. Le Common Language Runtime fournit un modèle pour la notification des erreurs aux applications de façon uniforme. Toutes les opérations .NET Framework indiquent une erreur en levant des exceptions.  
  
 Cette rubrique contient les sections suivantes :  
  
-   [Exceptions dans le .NET Framework](#exceptions_in_the_net_framework)  
  
-   [Exceptions et méthodes traditionnelles de gestion des erreurs](#exceptions_vs_traditional_errorhandling_methods)  
  
-   [Gestion des exceptions par le runtime](#how_the_runtime_manages_exceptions)  
  
-   [Filtrage des exceptions du runtime](#filtering_runtime_exceptions)  
  
-   [Rubriques connexes](#related_topics)  
  
-   [Référence](#reference)  
  
<a name="exceptions_in_the_net_framework"></a>   
## <a name="exceptions-in-the-net-framework"></a>Exceptions dans le .NET Framework  
 Une exception est une condition d'erreur ou un comportement inattendu rencontré par un programme en cours d'exécution. Les exceptions peuvent être déclenchées à cause d'une erreur dans votre code ou dans le code que vous appelez (tel qu'une bibliothèque partagée), de ressources de système d'exploitation non disponibles, de conditions inattendues rencontrées par le Common Language Runtime (telles que du code qui ne peut pas être vérifié), etc. Votre application peut récupérer suite à certaines de ces conditions, mais pas toutes. Bien que vous puissiez récupérer suite à la plupart des exceptions d'application, vous ne pouvez pas récupérer suite à la plupart des exceptions runtime.  
  
 Dans le .NET Framework, une exception est un objet qui hérite de la classe <xref:System.Exception?displayProperty=fullName>. Une exception est levée à partir d'une partie du code où un problème s'est produit. L'exception remonte la pile jusqu'à sa prise en charge par l'application ou l'arrêt du programme.  
  
 [Retour au début](#top)  
  
<a name="exceptions_vs_traditional_errorhandling_methods"></a>   
## <a name="exceptions-vs-traditional-error-handling-methods"></a>Exceptions et méthodes traditionnelles de gestion des erreurs  
 Traditionnellement, le modèle de gestion des erreurs d'un langage reposait soit sur le mode unique utilisé par le langage en question pour détecter des erreurs et leur trouver des gestionnaires appropriés, soit sur le mécanisme de gestion des erreurs fourni par le système d'exploitation. Le runtime implémente la gestion des exceptions de la façon suivante :  
  
-   gère les exceptions sans tenir compte du langage qui génère l'exception ni du langage qui gère l'exception ;  
  
-   ne requiert aucune syntaxe particulière pour la gestion des exceptions, mais laisse chaque langage définir sa propre syntaxe ;  
  
-   accepte la levée d'exceptions interprocessus et même au-delà des limites d'ordinateur.  
  
 Les exceptions offrent plusieurs avantages par rapport à d'autres méthodes de notification d'erreurs, telles que les codes de retour. Les erreurs ne passent pas inaperçues. La propagation des valeurs non valides à travers le système est interrompue. Vous n'êtes pas obligé de vérifier les codes de retour. Un code de gestion des exceptions peut être aisément ajouté pour augmenter la fiabilité du programme. Enfin, la gestion des exceptions par le runtime est plus rapide que la gestion des erreurs C++ qui fait appel à Windows.  
  
 Dans la mesure où les threads d'exécution parcourent couramment des blocs de code managé et non managé, le runtime peut lever ou intercepter des exceptions dans du code managé ou non managé. Le code non managé peut comprendre à la fois des exceptions SEH de style C++ et des HRESULTS COM.  
  
<a name="how_the_runtime_manages_exceptions"></a>   
## <a name="how-the-runtime-manages-exceptions"></a>Gestion des exceptions par le runtime  
 Le runtime utilise un modèle de gestion des exceptions basé sur des objets exception et des blocs de code protégés. Un objet <xref:System.Exception> est créé pour représenter une exception quand celle-ci se produit.  
  
 Le runtime crée une table d'informations sur les exceptions pour chaque exécutable. Chaque méthode de l'exécutable a un tableau associé d'informations de gestion des exceptions (qui peut être vide) contenu dans la table d'informations sur les exceptions. Chaque entrée du tableau décrit un bloc de code protégé, d'éventuels filtres d'exceptions associés à ce code et d'éventuels gestionnaires d'exceptions (instructions `catch`). Cette table d'exceptions est extrêmement efficace et aucune dégradation des performances n'est constatée, que ce soit au niveau du temps du processeur ou de l'utilisation de la mémoire, quand une exception ne se produit pas. Les ressources sont utilisées uniquement quand une exception se produit.  
  
 La table d'informations sur les exceptions représente quatre types de gestionnaires d'exceptions pour les blocs protégés :  
  
-   Un gestionnaire `finally` qui s'exécute à chaque sortie du bloc, que cette situation soit le résultat d'un flux de contrôle normal ou d'une exception non gérée.  
  
-   Un gestionnaire de pannes qui doit s'exécuter quand une exception se produit, mais ne s'exécute pas à l'issue de l'achèvement du flux de contrôle normal.  
  
-   Un gestionnaire filtré par type qui gère toute exception d'une classe spécifiée ou l'une de ses classes dérivées.  
  
-   Un gestionnaire filtré par l'utilisateur qui exécute un code spécifié par l'utilisateur afin de déterminer si l'exception doit être gérée par le gestionnaire associé ou passée au bloc protégé suivant.  
  
 Chaque langage implémente ces gestionnaires d'exceptions selon ses propres spécifications. Par exemple, Visual Basic donne accès à un gestionnaire filtré par l'utilisateur via une comparaison de variables (en utilisant le mot clé `When`) dans l'instruction `catch` ; C# n'implémente pas le gestionnaire filtré par l'utilisateur.  
  
 Quand une exception se produit, le runtime déclenche un processus en deux étapes :  
  
1.  Le runtime recherche dans le tableau le premier bloc protégé qui :  
  
    -   protège une partie contenant l'instruction en cours d'exécution ;  
  
    -   contient un gestionnaire d'exceptions ou un filtre chargé de la gestion de l'exception.  
  
2.  En cas de correspondance, le runtime crée un objet <xref:System.Exception> qui décrit l'exception. Le runtime exécute ensuite toutes les instructions `finally` ou fault situées entre l'instruction où l'exception s'est produite et l'instruction qui gère l'exception. Notez que l'ordre des gestionnaires d'exceptions est important : le gestionnaire d'exceptions le plus profond est évalué en premier. Notez également que les gestionnaires d'exceptions peuvent accéder aux variables locales et à la mémoire locale de la routine qui intercepte l'exception, mais les éventuelles valeurs intermédiaires survenant au moment où l'exception est levée sont perdues.  
  
     Si aucune correspondance n'est trouvée dans la méthode actuelle, le runtime explore chaque appelant de la méthode actuelle, puis poursuit ce chemin en remontant la pile. Si aucun appelant n'a de correspondance, le runtime autorise le débogueur à accéder à l'exception. Si le débogueur ne s'attache pas à l'exception, le runtime déclenche l'événement <xref:System.AppDomain.UnhandledException?displayProperty=fullName>. Si aucun écouteur n'existe pour cet événement, le runtime vide une trace de la pile et arrête l'application.  
  
 [Retour au début](#top)  
  
<a name="filtering_runtime_exceptions"></a>   
## <a name="filtering-runtime-exceptions"></a>Filtrage des exceptions du runtime  
 Vous pouvez filtrer les exceptions que vous interceptez et gérez soit par type soit par des critères définis par l'utilisateur.  
  
 Les gestionnaires filtrés par type gèrent un type particulier d'exception (ou de classes qui en sont dérivées). L'exemple suivant illustre un gestionnaire filtré par type conçu pour intercepter une exception spécifique, en l'occurrence <xref:System.IO.FileNotFoundException>.  
  
 [!code-cpp[CatchException#5](../../../samples/snippets/cpp/VS_Snippets_CLR/CatchException/CPP/catchexception3.cpp#5)]
 [!code-csharp[CatchException#5](../../../samples/snippets/csharp/VS_Snippets_CLR/CatchException/CS/catchexception3.cs#5)]
 [!code-vb[CatchException#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CatchException/VB/catchexception3.vb#5)]  
  
 Les gestionnaires d’exceptions filtrés par l’utilisateur interceptent et gèrent les exceptions selon des critères que vous définissez pour l’exception. Pour plus d'informations sur ce type de filtrage des exceptions, consultez [Utilisation d'exceptions spécifiques dans un bloc catch](../../../docs/standard/exceptions/how-to-use-specific-exceptions-in-a-catch-block.md).  
  
 [Retour au début](#top)  
  
<a name="related_topics"></a>   
## <a name="related-topics"></a>Rubriques connexes  
  
|Titre|Description|  
|-----------|-----------------|  
|[Classe et propriétés d’exception](../../../docs/standard/exceptions/exception-class-and-properties.md)|Décrit les éléments d'un objet exception.|  
|[Hiérarchie des exceptions](../../../docs/standard/exceptions/exception-hierarchy.md)|Décrit les exceptions à partir desquelles dérivent la plupart des exceptions.|  
|[Notions de base de la gestion des exceptions](../../../docs/standard/exceptions/exception-handling-fundamentals.md)|Explique comment gérer les exceptions à l'aide des instructions catch, throw et finally.|  
|[Meilleures pratiques pour les exceptions](../../../docs/standard/exceptions/best-practices-for-exceptions.md)|Décrit les méthodes suggérées pour gérer les exceptions.|  
|[Gestion des exceptions COM Interop](../../../docs/standard/exceptions/handling-com-interop-exceptions.md)|Décrit comment gérer les exceptions levées et interceptées dans du code non managé.|  
|[Guide pratique pour mapper des HRESULT et des exceptions](../../../docs/framework/interop/how-to-map-hresults-and-exceptions.md)|Décrit le mappage des exceptions entre le code managé et le code non managé.|  
  
<a name="reference"></a>   
## <a name="reference"></a>Référence  
 <xref:System.Exception?displayProperty=fullName>  
  
 <xref:System.ApplicationException?displayProperty=fullName>  
  
 <xref:System.SystemException?displayProperty=fullName>
