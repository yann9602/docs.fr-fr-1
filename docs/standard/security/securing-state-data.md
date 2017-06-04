---
title: "S&#233;curisation des donn&#233;es d&#39;&#233;tat | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-standard"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "sécurité du code, données d'état"
  - "codage sécurisé, données d'état"
  - "sécurité (.NET Framework), données d'état"
  - "données d'état (sécurité)"
ms.assetid: 12671309-2877-43fe-a3df-6863507e712d
caps.latest.revision: 9
author: "mairaw"
ms.author: "mairaw"
manager: "wpickett"
caps.handback.revision: 7
---
# S&#233;curisation des donn&#233;es d&#39;&#233;tat
Les applications qui gèrent des données confidentielles ou qui prennent des décisions de sécurité doivent conserver ces données sous leur contrôle et ne peuvent pas laisser un autre code potentiellement nuisible accéder directement aux données.  Le meilleur moyen de protéger les données de la mémoire est de déclarer celles\-ci sous forme de variables privées ou internes \(avec portée limitée au même assembly\).  Cependant, même ces données font l'objet d'un accès que vous devez connaître :  
  
-   À l'aide des mécanismes de réflexion, le code d'un niveau de confiance élevé pouvant référencer votre objet peut obtenir et définir des membres privés.  
  
-   À l'aide de la sérialisation, le code d'un niveau de confiance élevé peut obtenir et définir en pratique des membres privés s'il peut accéder aux données correspondantes dans la forme sérialisée de l'objet.  
  
-   En débogage, ces données peuvent être lues.  
  
 Assurez\-vous qu'aucune de vos propres méthodes ou propriétés n'expose ces valeurs involontairement.  
  
 Dans certains cas, des données peuvent être déclarées comme « protégées » avec un accès limité à la classe et ses dérivés.  Cependant, vous devez prendre les précautions supplémentaires suivantes en raison de l'exposition supplémentaire :  
  
-   Contrôlez le code autorisé à effectuer une dérivation de votre classe en le limitant au même assembly ou en utilisant la sécurité déclarative \(procédés décrits dans [Sécurisation de l'accès à la méthode](../../../docs/framework/misc/securing-method-access.md)\) pour exiger une identité ou des autorisations afin d'effectuer une dérivation du code à partir de votre classe.  
  
-   Assurez\-vous que toutes les classes dérivées implémentent une protection similaire ou soient sealed.  
  
## Voir aussi  
 [Instructions de codage sécurisé](../../../docs/standard/security/secure-coding-guidelines.md)