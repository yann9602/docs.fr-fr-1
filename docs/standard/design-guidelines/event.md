---
title: "Conception d'événements"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- pre-events
- events [.NET Framework], design guidelines
- member design guidelines, events
- event handlers [.NET Framework], event design guidelines
- post-events
- signatures, event handling
ms.assetid: 67b3c6e2-6a8f-480d-a78f-ebeeaca1b95a
caps.latest.revision: "15"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: a07392ba805b5f2a3913b01a15dd0e1668f0ccf7
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/23/2017
---
# <a name="event-design"></a>Conception d'événements
Les événements sont la forme couramment utilisée de rappels (les constructions qui autorisent l’infrastructure pour appeler dans du code de l’utilisateur). Autres mécanismes de rappel incluent les membres avec les délégués, les membres virtuels et basée sur l’interface de plug-ins. Les données à partir des études de convivialité indiquent que la majorité des développeurs sont plus à l’aise avec les événements qu’ils utilisent d’autres méthodes de rappel. Les événements sont bien intégrés à Visual Studio et de nombreux langages.  
  
 Il est important de noter qu’il n’y a deux groupes d’événements : événements déclenchés avant un état des modifications système, appelé pré-événements et les événements déclenchés après le change d’un état, appelée post événements. Un exemple d’un événement avant serait `Form.Closing`, qui est déclenché avant la fermeture d’un formulaire. Un exemple d’un post-événement `Form.Closed`, qui est déclenché lorsqu’un formulaire est fermé.  
  
 **✓ FAIRE** utiliser le terme « r » pour les événements plutôt que « fire » ou « déclenche ».  
  
 **✓ FAIRE** utiliser <xref:System.EventHandler%601?displayProperty=nameWithType> au lieu de créer manuellement les nouveaux délégués à utiliser en tant que gestionnaires d’événements.  
  
 **ENVISAGEZ de ✓** à l’aide d’une sous-classe de <xref:System.EventArgs> comme argument d’événement, sauf si vous êtes absolument que l’événement n’est jamais nécessaire de transporter des données à l’événement de gestion de la méthode, auquel cas vous pouvez utiliser la `EventArgs` taper directement.  
  
 Si vous livrez une à l’aide de l’API `EventArgs` directement, vous ne pourrez jamais ajouter des données à effectuer sans rompre la compatibilité avec l’événement. Si vous utilisez une sous-classe, même si initialement vide, vous serez en mesure d’ajouter des propriétés à la sous-classe si nécessaire.  
  
 **✓ FAIRE** utiliser une méthode virtuelle protégée pour déclencher chaque événement. Cela s’applique uniquement aux événements non statiques sur les classes non scellés, pas pour les structures, les classes sealed ou aux événements statiques.  
  
 L’objectif de la méthode est d’offrir un moyen d’une classe dérivée gérer l’événement à l’aide d’un remplacement. La substitution est un moyen plus naturel, plus rapide et plus souple pour gérer les événements de la classe de base dans les classes dérivées. Par convention, le nom de la méthode doit commencer par « On » et être suivi par le nom de l’événement.  
  
 La classe dérivée peut choisissez de ne pas appeler l’implémentation de la méthode de base dans son remplacement. Attendez-vous à cela en n’incluant aucun traitement dans la méthode qui est requise pour la classe de base fonctionne correctement.  
  
 **✓ FAIRE** doit accepter un paramètre à la méthode protégée qui déclenche un événement.  
  
 Le paramètre doit être nommé `e` et doit être tapé sous forme de la classe d’argument d’événement.  
  
 **X ne sont pas** passez la valeur null en tant que l’expéditeur lors du déclenchement d’un événement non statique.  
  
 **✓ FAIRE** passez la valeur null en tant que l’expéditeur lors du déclenchement d’un événement statique.  
  
 **X ne sont pas** passez la valeur null en tant que le paramètre de données d’événement lors du déclenchement d’un événement.  
  
 Vous devez passer `EventArgs.Empty` si vous ne souhaitez pas passer des données à la méthode de gestion d’événements. Les développeurs s’attendent à ce paramètre ne pas pour avoir la valeur null.  
  
 **✓ Envisagez** le déclenchement d’événements de l’utilisateur final peut annuler. Cela s’applique uniquement aux événements antérieurs.  
  
 Utilisez <xref:System.ComponentModel.CancelEventArgs?displayProperty=nameWithType> ou sa sous-classe comme argument d’événement pour autoriser l’utilisateur final d’annuler des événements.  
  
### <a name="custom-event-handler-design"></a>Conception de gestionnaires d’événements personnalisés  
 Il existe des cas dans lequel `EventHandler<T>` ne peut pas être utilisé, tel que lorsque l’infrastructure a besoin travailler avec les versions antérieures du CLR, ce qui ne prend pas en charge les génériques. Dans ce cas, vous devrez peut-être concevoir et développer un délégué de gestionnaire d’événements personnalisé.  
  
 **✓ FAIRE** utiliser un type de retour void pour les gestionnaires d’événements.  
  
 Un gestionnaire d’événements peut appeler plusieurs méthodes, éventuellement sur plusieurs objets de gestion d’événement. Si les méthodes de gestion des événements ont été autorisées pour retourner une valeur, il y aura plusieurs valeurs de retour pour chaque appel de l’événement.  
  
 **✓ FAIRE** utiliser `object` en tant que le type du premier paramètre du Gestionnaire d’événements et l’appeler `sender`.  
  
 **✓ FAIRE** utiliser <xref:System.EventArgs?displayProperty=nameWithType> ou sa sous-classe en tant que le type du deuxième paramètre du Gestionnaire d’événements et l’appeler `e`.  
  
 **X ne sont pas** avoir plus de deux paramètres sur les gestionnaires d’événements.  
  
 *Portions © 2005, 2009 Microsoft Corporation. Tous droits réservés.*  
  
 *Réimprimées avec l’autorisation de Pearson éducation, Inc. à partir de [règles de conception d’infrastructure : Conventions, idiomes et des modèles pour les bibliothèques .NET réutilisable, 2nd Edition](http://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina et Brad Abrams, publié le 22 octobre 2008 par Addison-Wesley Professional dans le cadre de la série de développement Microsoft Windows.*  
  
## <a name="see-also"></a>Voir aussi  
 [Instructions de conception des membres](../../../docs/standard/design-guidelines/member.md)  
 [Règles de conception de .NET Framework](../../../docs/standard/design-guidelines/index.md)
