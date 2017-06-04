---
title: "m&#233;thodes d’extension. | Microsoft Docs"
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
ms.assetid: 5de945cb-88f4-49d7-b0e6-f098300cf357
caps.latest.revision: 4
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 4
---
# m&#233;thodes d’extension.
Méthodes d’extension sont une fonctionnalité de langage qui permet des méthodes statiques pour être appelée à l’aide de la syntaxe de méthode d’appel d’instance. Ces méthodes doivent disposer d’au moins un paramètre, qui représente l’instance de que la méthode consiste à utiliser.  
  
 La classe qui définit ces méthodes d’extension est appelée à la classe « parrain », et elle doit être déclarée comme static. Pour utiliser les méthodes d’extension, un doit importer l’espace de noms définit la classe commanditaire.  
  
 **X éviter** leurs intentions soient amicales définissant les méthodes d’extension, en particulier sur les types que vous ne possédez pas.  
  
 Si vous n’êtes pas propriétaire le code source d’un type, pensez à l’aide des méthodes d’instance standard à la place. Si vous ne possédez pas, et que vous souhaitez ajouter une méthode, soyez très prudent. L’utilisation répandue des méthodes d’extension a le potentiel d’encombrer l’API de types qui n’ont pas été conçues pour que ces méthodes.  
  
 **✓ envisagez** à l’aide des méthodes d’extension dans un des scénarios suivants :  
  
-   Pour fournir l’assistance fonctionnalités pertinentes pour chaque implémentation d’une interface, si a les fonctionnalités peuvent être écrites en termes de l’interface principale. Il s’agit, car les implémentations concrètes sinon ne peuvent pas être attribuées aux interfaces. Par exemple, le `LINQ to Objects` les opérateurs sont implémentés en tant que méthodes d’extension pour tous les <xref:System.Collections.Generic.IEnumerable%601> types. Par conséquent, les `IEnumerable<>` implémentation est automatiquement activée pour LINQ.  
  
-   Lorsqu’une méthode d’instance créerait une dépendance sur un type, mais une telle dépendance ne fonctionneraient pas les règles de dépendance de gestion. Par exemple, une dépendance à partir de <xref:System.String> à <xref:System.Uri?displayProperty=fullName> n’est probablement pas souhaitable et ainsi `String.ToUri()` retour de méthode d’instance `System.Uri` serait la conception incorrecte du point de vue Gestion des dépendances. Une méthode d’extension statique `Uri.ToUri(this string str)` retour `System.Uri` serait une bien meilleure conception.  
  
 **X éviter** définition de méthodes d’extension sur <xref:System.Object?displayProperty=fullName>.  
  
 Visual Basic ne sera pas en mesure d’appeler des méthodes sur les références d’objet à l’aide de la syntaxe de méthode d’extension. VB ne prend pas en charge l’appeler ces méthodes, car, dans VB, déclaration une référence d’objet oblige tous les appels de méthode sur ce retard lié \(réel membre appelée est déterminée lors de l’exécution\), tandis que les liaisons aux méthodes d’extension sont déterminés au moment de la compilation \(liaison anticipée\).  
  
 Notez que la règle s’applique à d’autres langages, où le même comportement de liaison est présent, ou lorsque les méthodes d’extension ne sont pas pris en charge.  
  
 **X ne pas** place les méthodes d’extension dans le même espace de noms en tant que le type étendu que si elle pour ajouter des méthodes aux interfaces ou pour la gestion des dépendances.  
  
 **X éviter** définition de deux ou plusieurs méthodes d’extension avec la même signature, même si elles se trouvent dans différents espaces de noms.  
  
 **✓ envisagez** définition des méthodes d’extension dans le même espace de noms en tant que le type étendu si le type est une interface et si les méthodes d’extension sont destinés à être utilisés dans la plupart des cas.  
  
 **X ne pas** définir des méthodes d’extension l’implémentation d’une fonctionnalité dans les espaces de noms normalement avec d’autres fonctionnalités. Au lieu de cela, les définir dans l’espace de noms associé à la fonctionnalité qu'auquel ils appartiennent.  
  
 **X éviter** générique d’affectation de noms d’espaces de noms dédié aux méthodes d’extension \(par exemple, « Extensions »\). Utilisez un nom descriptif \(par exemple, « routage »\) à la place.  
  
 *Portions © 2005, 2009 Microsoft Corporation. Tous droits réservés.*  
  
 *Réimprimé avec l’autorisation de Pearson éducation, Inc. à partir de [Framework Design Guidelines : Conventions, langages et des modèles pour les bibliothèques .NET réutilisable, 2nd Edition](http://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina et Brad Abrams, publié le 22 octobre 2008 par Addison\-Wesley Professional dans le cadre de la série de développement de Microsoft Windows.*  
  
## Voir aussi  
 [Règles de conception de membres](../../../docs/standard/design-guidelines/member.md)   
 [Instructions de conception d’infrastructure](../../../docs/standard/design-guidelines/index.md)