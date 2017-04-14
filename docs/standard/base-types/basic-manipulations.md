---
title: "Comment&#160;: effectuer des manipulations de cha&#238;nes de base dans .NET Framework | Microsoft Docs"
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
  - "chaînes (.NET Framework), exemples"
ms.assetid: 121d1eae-251b-44c0-8818-57da04b8215e
caps.latest.revision: 7
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 7
---
# Comment&#160;: effectuer des manipulations de cha&#238;nes de base dans .NET Framework
L'exemple suivant utilise certaines des méthodes étudiées dans les rubriques des [Opérations de chaînes de base](../../../docs/standard/base-types/basic-string-operations.md) pour construire une classe capable d'effectuer des manipulations de chaînes similaires à celles qui se rencontrent dans les applications réelles.  La classe `MailToData` stocke le nom et l'adresse d'une personne dans des propriétés séparées et fournit une façon de combiner les champs `City`, `State` et `Zip` dans une seule chaîne à afficher pour l'utilisateur.  En outre, la classe permet à l'utilisateur d'entrer les informations concernant la ville, la province ou le département et le code postal sous la forme d'une chaîne unique ; l'application analyse automatiquement la chaîne unique et entre les informations appropriées dans la propriété correspondante.  
  
 Pour la simplicité, cet exemple utilise une application console équipée d'une interface de ligne de commande .  
  
## Exemple  
 [!code-csharp[Conceptual.String.BasicOps#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.basicops/cs/basicops.cs#1)]
 [!code-vb[Conceptual.String.BasicOps#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.basicops/vb/basicops.vb#1)]  
  
 Lors de l'exécution du code ci\-dessus, l'utilisateur est invité à entrer son nom et son adresse.  L'application place les informations dans les propriétés correspondantes et les affiche à nouveau pour l'utilisateur en créant une chaîne unique qui reprend les données de la ville, de la province ou du département, ainsi que le code postal.  
  
## Voir aussi  
 [Opérations de chaînes de base](../../../docs/standard/base-types/basic-string-operations.md)