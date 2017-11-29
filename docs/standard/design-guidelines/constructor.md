---
title: Conception de constructeurs
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- member design guidelines, constructors
- constructors, design guidelines
- instance constructors
- type constructors
- virtual members
- constructors, types
- default constructors
- static constructors
ms.assetid: b4496afe-5fa7-4bb0-85ca-70b0ef21e6fc
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: a46bf111b76ef6d07fa99cc3b19684a0726b7062
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="constructor-design"></a>Conception de constructeurs
Il existe deux types de constructeurs : constructeurs et les constructeurs d’instance de type.  
  
 Constructeurs de type sont statiques et sont exécutées par le CLR, avant que le type est utilisé. Constructeurs d’instance exécuté lorsqu’une instance d’un type est créée.  
  
 Constructeurs de type ne peut pas prendre des paramètres. Constructeurs d’instance peuvent. Constructeurs d’instance qui n’acceptent aucun paramètre sont souvent appelés des constructeurs par défaut.  
  
 Les constructeurs sont la façon la plus naturelle pour créer des instances d’un type. La plupart des développeurs recherche et essayez d’utiliser un constructeur avant d’autres méthodes pour créer des instances (par exemple, les méthodes de fabrique).  
  
 **✓ Envisagez** fournissant simple, dans l’idéal, par défaut, les constructeurs.  
  
 Un constructeur simple possède un très petit nombre de paramètres, et tous les paramètres sont des primitives ou enums. Ces constructeurs simples faciliter l’utilisation de l’infrastructure.  
  
 **✓ Envisagez** à l’aide d’une méthode de fabrique statique au lieu d’un constructeur si la sémantique de l’opération requise ne correspond pas directement à la construction d’une nouvelle instance, ou si les règles de conception du constructeur vous semblent pas naturelles.  
  
 **✓ FAIRE** utiliser les paramètres du constructeur en tant que raccourcis pour définir les propriétés principales.  
  
 Il ne doit y avoir aucune différence de sémantique entre l’utilisation du constructeur vide suivi de certains jeux de propriétés et à l’aide d’un constructeur avec plusieurs arguments.  
  
 **✓ FAIRE** utiliser le même nom pour les paramètres du constructeur et une propriété si les paramètres du constructeur sont utilisés pour définir simplement la propriété.  
  
 La seule différence entre ces paramètres et les propriétés est la casse.  
  
 **✓ FAIRE** travail minimal dans le constructeur.  
  
 Les constructeurs ne quantité de travail autre que capture les paramètres du constructeur. Le coût de tout autre traitement doit être différé jusqu'à ce que nécessaire.  
  
 **✓ FAIRE** lever des exceptions à partir des constructeurs d’instance, le cas échéant.  
  
 **✓ FAIRE** déclarer explicitement le constructeur public par défaut dans les classes, si un tel constructeur est nécessaire.  
  
 Si vous ne déclarez explicitement de constructeur sur un type, plusieurs langues (par exemple, en c#) ajoute automatiquement un constructeur public par défaut. (Les classes abstraites obtenir un constructeur protégé.)  
  
 Ajout d’un constructeur paramétrable à une classe d’empêche le compilateur d’ajouter le constructeur par défaut. Cela entraîne souvent des modifications avec rupture accidentelle.  
  
 **X Évitez** définition explicite des constructeurs par défaut sur les structures.  
  
 Cela rend la création de tableau plus rapide, car si le constructeur par défaut n’est pas défini, il n’a pas à être exécuté sur tous les emplacements dans le tableau. Notez que de nombreux compilateurs, notamment c#, ne pas autoriser les structs peuvent avoir des constructeurs sans paramètre pour cette raison.  
  
 **X Évitez** appel des membres virtuels sur un objet à l’intérieur de son constructeur.  
  
 Appel d’un membre virtuel entraînera le remplacement de la plus dérivé à appeler, même si le constructeur du type plus dérivé a été entièrement s’exécute pas encore.  
  
### <a name="type-constructor-guidelines"></a>Instructions de constructeur de type  
 **✓ FAIRE** rendre les constructeurs statiques privé.  
  
 Un constructeur statique, également appelé constructeur de classe, est utilisé pour initialiser un type. Le CLR appelle le constructeur statique avant la création de la première instance du type ou de tout membre statique de ce type est appelées. L’utilisateur n’a aucun contrôle sur lorsque le constructeur statique est appelé. Si un constructeur statique n’est pas privé, il peut être appelé par du code autre que le CLR. Selon les opérations effectuées dans le constructeur, cela peut provoquer un comportement inattendu. Le compilateur c# force les constructeurs statiques privé.  
  
 **X ne sont pas** lever des exceptions à partir des constructeurs statiques.  
  
 Si une exception est levée à partir d’un constructeur de type, le type n’est pas utilisable dans le domaine d’application actuel.  
  
 **✓ Envisagez** initialiser les champs statiques inline au lieu d’utiliser explicitement des constructeurs statiques, car le runtime peut optimiser les performances des types qui n’ont pas un constructeur statique explicitement défini.  
  
 *Portions © 2005, 2009 Microsoft Corporation. Tous droits réservés.*  
  
 *Réimprimées avec l’autorisation de Pearson éducation, Inc. à partir de [règles de conception d’infrastructure : Conventions, idiomes et des modèles pour les bibliothèques .NET réutilisable, 2nd Edition](http://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina et Brad Abrams, publié le 22 octobre 2008 par Addison-Wesley Professional dans le cadre de la série de développement Microsoft Windows.*  
  
## <a name="see-also"></a>Voir aussi  
 [Règles de conception de membres](../../../docs/standard/design-guidelines/member.md)  
 [Règles de conception de .NET Framework](../../../docs/standard/design-guidelines/index.md)
