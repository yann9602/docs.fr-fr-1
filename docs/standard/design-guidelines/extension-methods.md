---
title: "méthodes d’extension."
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 5de945cb-88f4-49d7-b0e6-f098300cf357
caps.latest.revision: "4"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 28ce4451f9f8cc634ab76b3b4ef845103ea55e35
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/23/2017
---
# <a name="extension-methods"></a>méthodes d’extension.
Méthodes d’extension sont une fonctionnalité de langage qui permet des méthodes statiques pour être appelée à l’aide de la syntaxe de méthode d’appel d’instance. Ces méthodes doivent disposer d’au moins un paramètre, qui représente l’instance de sur que la méthode consiste à opérer.  
  
 La classe qui définit des méthodes d’extension est considérée comme la classe « parrain », et elle doit être déclarée comme statique. Pour utiliser les méthodes d’extension, un doit importer l’espace de noms définissant la classe sponsor.  
  
 **X Évitez** leurs intentions soient amicales définissant les méthodes d’extension, en particulier sur les types que vous ne possédez pas.  
  
 Si vous possédez le code source d’un type, envisagez d’utiliser les méthodes d’instance régulière à la place. Si vous ne possédez pas, et que vous souhaitez ajouter une méthode, soyez très prudent. L’utilisation répandue des méthodes d’extension est susceptible d’encombrer les API de types qui n’ont pas été conçues pour que ces méthodes.  
  
 **✓ Envisagez** à l’aide des méthodes d’extension dans un des scénarios suivants :  
  
-   Pour fournir d’assistance fonctionnalités pertinentes pour chaque implémentation d’une interface, si on dit que les fonctionnalités peuvent être écrits en termes de l’interface. Il s’agit, car les implémentations concrètes sinon ne peut pas être attribuées aux interfaces. Par exemple, le `LINQ to Objects` opérateurs sont implémentés en tant que méthodes d’extension pour tous les <xref:System.Collections.Generic.IEnumerable%601> types. Par conséquent, les `IEnumerable<>` implémentation est automatiquement prenant en charge LINQ.  
  
-   Lorsqu’une méthode d’instance créerait une dépendance sur un type, mais une telle dépendance compromettrait les règles de dépendance de gestion. Par exemple, une dépendance à partir de <xref:System.String> à <xref:System.Uri?displayProperty=nameWithType> n’est probablement pas souhaitable et donc `String.ToUri()` retour de méthode d’instance `System.Uri` serait la mauvaise conception à partir d’un point de vue de gestion de dépendance. Une méthode d’extension statique `Uri.ToUri(this string str)` retour `System.Uri` serait une bien meilleure conception.  
  
 **X Évitez** définition des méthodes d’extension sur <xref:System.Object?displayProperty=nameWithType>.  
  
 Les utilisateurs de Visual Basic ne seront pas en mesure d’appeler ces méthodes sur les références d’objet à l’aide de la syntaxe de méthode d’extension. VB ne prend pas en charge l’appel de ces méthodes car, en Visual Basic, déclaration comme objet oblige tous les appels de méthode sur qu’il soit à la fin d’une référence liée (membre réel appelé est déterminé lors de l’exécution), tandis que les liaisons à des méthodes d’extension sont déterminés au moment de la compilation (anticipée lié).  
  
 Notez que la règle s’applique à d’autres langages, où le même comportement de liaison est présent, ou lorsque les méthodes d’extension ne sont pas pris en charge.  
  
 **X ne sont pas** méthodes d’extension dans le même espace de noms en tant que le type étendu est utilisée pour ajouter des méthodes aux interfaces ou pour la gestion des dépendances.  
  
 **X Évitez** définissant deux ou plusieurs méthodes d’extension avec la même signature, même s’ils résident dans différents espaces de noms.  
  
 **✓ Envisagez** définition des méthodes d’extension dans le même espace de noms en tant que le type étendu si le type est une interface et si les méthodes d’extension sont destinés à être utilisés dans la plupart des cas.  
  
 **X ne sont pas** définir des méthodes d’extension mise en œuvre d’une fonctionnalité dans les espaces de noms normalement avec d’autres fonctionnalités. Au lieu de cela, les définir dans l’espace de noms associé à la fonctionnalité qu'auquel ils appartiennent.  
  
 **X Évitez** générique d’affectation de noms d’espaces de noms dédié aux méthodes d’extension (par exemple, « Extensions »). Utilisez un nom descriptif (par exemple, « routage ») à la place.  
  
 *Portions © 2005, 2009 Microsoft Corporation. Tous droits réservés.*  
  
 *Réimprimées avec l’autorisation de Pearson éducation, Inc. à partir de [règles de conception d’infrastructure : Conventions, idiomes et des modèles pour les bibliothèques .NET réutilisable, 2nd Edition](http://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina et Brad Abrams, publié le 22 octobre 2008 par Addison-Wesley Professional dans le cadre de la série de développement Microsoft Windows.*  
  
## <a name="see-also"></a>Voir aussi  
 [Instructions de conception des membres](../../../docs/standard/design-guidelines/member.md)  
 [Règles de conception de .NET Framework](../../../docs/standard/design-guidelines/index.md)
