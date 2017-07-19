---
title: "Conception d’&#233;v&#233;nements | Microsoft Docs"
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
  - "événements antérieurs"
  - "événements (.NET Framework), les règles de conception"
  - "règles de conception de membres, événements"
  - "gestionnaires d’événements (.NET Framework), instructions de conception d’événements"
  - "post-événements"
  - "signatures, la gestion des événements"
ms.assetid: 67b3c6e2-6a8f-480d-a78f-ebeeaca1b95a
caps.latest.revision: 15
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 15
---
# Conception d’&#233;v&#233;nements
Les événements sont la forme fréquemment des rappels \(constructions qui permettent l’infrastructure d’appeler dans du code utilisateur\). Autres mécanismes de rappel incluent les membres avec les délégués, les membres virtuels et plug\-ins basés sur une interface. Données d’études indiquent que la majorité des développeurs sont plus confortable l’utilisation des événements qu’ils sont à l’aide des autres méthodes de rappel. Les événements sont bien intégrées à Visual Studio et de nombreux langages.  
  
 Il est important de noter qu’il existe deux groupes d’événements : événements déclenchés avant un état des modifications système, appelé événements antérieurs et les événements déclenchés après un état change, appelée après les événements. Voici un exemple d’un événement avant `Form.Closing`, qui est déclenché avant la fermeture d’un formulaire. Voici un exemple d’un post\-événement `Form.Closed`, qui est déclenché lorsqu’un formulaire est fermé.  
  
 **✓ faire** utilisent le terme « déclenche » pour les événements plutôt que « fire » ou « déclenche ».  
  
 **✓ faire** utilisez <xref:System.EventHandler%601?displayProperty=fullName> au lieu de créer manuellement les nouveaux délégués à utiliser comme gestionnaires d’événements.  
  
 **✓ envisagez** à l’aide d’une sous\-classe de <xref:System.EventArgs> comme argument d’événement, sauf si vous êtes absolument certain que l’événement n’est jamais nécessaire de transporter des données à la méthode de gestion d’événements auquel cas vous pouvez utiliser la `EventArgs` taper directement.  
  
 Si vous expédiez une API via `EventArgs` directement, vous ne serez jamais en mesure d’ajouter des données à exécuter sans perdre la compatibilité avec l’événement. Si vous utilisez une sous\-classe, même si initialement vide, vous serez en mesure d’ajouter des propriétés à la sous\-classe lorsque nécessaire.  
  
 **✓ faire** utiliser une méthode virtuelle protégée pour déclencher chaque événement. Cela s’applique uniquement aux événements non statiques sur des classes unsealed, mais pas pour les structures, les classes sealed ou aux événements statiques.  
  
 L’objectif de la méthode consiste à fournir un moyen pour une classe dérivée pour gérer l’événement à l’aide d’un remplacement. La substitution est un moyen plus flexible, plus rapide et plus naturel pour gérer les événements de la classe de base dans les classes dérivées. Par convention, le nom de la méthode doit commencer par « On » et être suivi par le nom de l’événement.  
  
 La classe dérivée peut choisir ne pas à appeler l’implémentation de la méthode de base dans son remplacement. Face à cette situation en n’incluant aucun traitement dans la méthode qui est requise pour la classe de base fonctionne correctement.  
  
 **✓ faire** prendre un paramètre à la méthode protégée qui déclenche un événement.  
  
 Le paramètre doit être nommé `e` et la classe d’argument d’événement doit être de type.  
  
 **X ne pas** passez la valeur null en tant que l’expéditeur lors du déclenchement d’un événement non statique.  
  
 **✓ faire** passez la valeur null en tant que l’expéditeur lors du déclenchement d’un événement statique.  
  
 **X ne pas** transmettre null comme paramètre de données d’événement lors du déclenchement d’un événement.  
  
 Vous devez passer `EventArgs.Empty` Si vous ne souhaitez pas transmettre des données à la méthode de gestion d’événement. Les développeurs s’attendent à ce paramètre ne pas pour avoir la valeur null.  
  
 **✓ envisagez** le déclenchement d’événements de l’utilisateur final peut annuler. Cela s’applique uniquement aux événements antérieurs.  
  
 Utilisez <xref:System.ComponentModel.CancelEventArgs?displayProperty=fullName> ou sa sous\-classe comme argument d’événement pour permettre à l’utilisateur final d’annuler des événements.  
  
### Conception de gestionnaires d’événements personnalisés  
 Il existe des cas dans lesquels `EventHandler<T>` ne peuvent pas être utilisées, comme lorsque le framework doit fonctionner avec les versions antérieures du CLR, lequel ne prenait pas en charge les génériques. Dans ce cas, vous devez concevoir et développer un délégué de gestionnaire d’événements personnalisé.  
  
 **✓ faire** utiliser un type de retour void pour les gestionnaires d’événements.  
  
 Un gestionnaire d’événements peut appeler plusieurs méthodes, voire sur plusieurs objets de gestion d’événement. Si les méthodes de gestion des événements étaient autorisées à retourner une valeur, il y aura plusieurs valeurs de retour pour chaque appel de l’événement.  
  
 **✓ faire** utiliser `object` comme le type du premier paramètre du Gestionnaire d’événements et appelez\-le `sender`.  
  
 **✓ faire** utiliser <xref:System.EventArgs?displayProperty=fullName> ou sa sous\-classe en tant que le type du deuxième paramètre du Gestionnaire d’événements et appelez\-le `e`.  
  
 **X ne pas** avoir plus de deux paramètres sur les gestionnaires d’événements.  
  
 *Portions © 2005, 2009 Microsoft Corporation. Tous droits réservés.*  
  
 *Réimprimé avec l’autorisation de Pearson éducation, Inc. à partir de [Framework Design Guidelines : Conventions, langages et des modèles pour les bibliothèques .NET réutilisable, 2nd Edition](http://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina et Brad Abrams, publié le 22 octobre 2008 par Addison\-Wesley Professional dans le cadre de la série de développement de Microsoft Windows.*  
  
## Voir aussi  
 [Règles de conception de membres](../../../docs/standard/design-guidelines/member.md)   
 [Instructions de conception d’infrastructure](../../../docs/standard/design-guidelines/index.md)