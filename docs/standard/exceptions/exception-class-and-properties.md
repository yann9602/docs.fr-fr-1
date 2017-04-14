---
title: "Classe et propri&#233;t&#233;s d&#39;exception | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-standard"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Exception (classe)"
  - "exceptions, Exception (classe)"
ms.assetid: e2e1f8c4-e7b4-467d-9a66-13c90861221d
caps.latest.revision: 9
author: "mairaw"
ms.author: "mairaw"
manager: "wpickett"
caps.handback.revision: 9
---
# Classe et propri&#233;t&#233;s d&#39;exception
La classe <xref:System.Exception> est la classe de base dont les exceptions héritent.  La plupart des objets exception sont des instances d'une classe dérivée d'**Exception**, mais vous pouvez lever n'importe quel objet qui dérive de la classe <xref:System.Object> en tant qu'exception.  Notez que certains langages ne prennent pas en charge la levée et l'interception d'objets ne dérivant pas de la classe **Exception**.  Dans la plupart des cas, il est recommandé de lever et d'intercepter uniquement des objets **Exception**.  
  
 La classe **Exception** possède plusieurs propriétés qui permettent de mieux comprendre une exception.  Il s'agit notamment des propriétés suivantes :  
  
-   La propriété <xref:System.Exception.StackTrace%2A>.  
  
     Cette propriété contient une trace de la pile qui peut être utilisée pour déterminer l'emplacement où une erreur s'est produite.  La trace de la pile comprend le nom du fichier source et le numéro de ligne du programme si les informations de débogage sont disponibles.  
  
-   La propriété <xref:System.Exception.InnerException%2A>.  
  
     Cette propriété peut servir à créer et à conserver une série d'exceptions pendant la gestion des exceptions.  Vous pouvez utiliser cette propriété pour créer une nouvelle exception qui contient des exceptions interceptées précédemment.  L'exception d'origine peut être saisie par la deuxième exception dans la propriété **InnerException**, permettant ainsi au code qui gère la deuxième exception d'examiner les informations supplémentaires.  
  
     Par exemple, prenons le cas d'une méthode qui lit un fichier et met en forme les données.  Le code essaie de lire le fichier, mais une FileException est levée.  La méthode intercepte FileException et lève une BadFormatException.  En ce cas, FileException peut être enregistrée dans la propriété **InnerException** de BadFormatException.  
  
     Pour améliorer la capacité de l'appelant à déterminer la raison pour laquelle une exception a été levée, il est parfois souhaitable qu'une méthode intercepte une exception levée par le biais d'une routine d'assistance puis lève une exception plus indicative de l'erreur qui s'est produite.  Une exception nouvelle et plus significative peut être créée, où la référence d'exception interne peut avoir comme valeur l'exception d'origine.  Cette exception plus significative peut ensuite être levée pour l'appelant.  Notez que cette fonctionnalité permet de créer une série d'exceptions liées qui se termine par l'exception levée en premier.  
  
-   La propriété <xref:System.Exception.Message%2A>.  
  
     Cette propriété fournit des détails sur la cause d'une exception.  Le **Message** est dans la langue spécifiée par la propriété <xref:System.Threading.Thread.CurrentUICulture%2A?displayProperty=fullName> du thread qui lève l'exception.  
  
-   La propriété <xref:System.Exception.HelpLink%2A>.  
  
     Cette propriété peut contenir une URL \(ou une URN\) vers un fichier d'aide qui fournit des informations extensives sur la cause d'une exception.  
  
-   La propriété <xref:System.Exception.Data%2A>  
  
     Cette propriété est un IDictionary qui peut conserver des données arbitraires dans des paires clé\/valeur.  
  
 La plupart des classes qui héritent de la classe **Exception** n'implémentent pas de membre supplémentaire et ne fournissent pas de fonctionnalité additionnelle ; elles héritent simplement de la classe **Exception**.  Par conséquent, l'information la plus importante concernant une exception se trouve dans la hiérarchie des exceptions, le nom de l'exception et les informations contenues dans l'exception.  
  
## Voir aussi  
 [Hiérarchie des exceptions](../../../docs/standard/exceptions/exception-hierarchy.md)   
 [Notions de base de la gestion des exceptions](../../../docs/standard/exceptions/exception-handling-fundamentals.md)   
 [Meilleures pratiques pour les exceptions](../../../docs/standard/exceptions/best-practices-for-exceptions.md)   
 [Exceptions](../../../docs/standard/exceptions/index.md)