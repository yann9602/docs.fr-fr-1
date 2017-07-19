---
title: "S&#233;curit&#233; et champs de tableau en lecture seule publics | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "sécurité (.NET Framework), champs de tableau en lecture seule publics"
ms.assetid: 3df28dee-2a9f-40ff-9852-bfdbe59c27f3
caps.latest.revision: 7
author: "mairaw"
ms.author: "mairaw"
manager: "wpickett"
caps.handback.revision: 7
---
# S&#233;curit&#233; et champs de tableau en lecture seule publics
N'utilisez jamais les champs de tableau publics en lecture seule issus de bibliothèques managées pour définir le comportement des limites ou la sécurité de vos applications, car ces champs sont susceptibles d'être modifiés.  
  
## Remarques  
 Certaines classes .NET Framework incluent des champs publics en lecture seule qui contiennent des paramètres relatifs aux limites spécifiques à la plateforme.  Par exemple, le champ <xref:System.IO.Path.InvalidPathChars> est un tableau qui décrit les caractères non autorisés dans une chaîne de chemin d'accès.  De nombreux champs semblables sont présents dans le .NET Framework.  
  
 Les valeurs des champs publics en lecture seule, par exemple <xref:System.IO.Path.InvalidPathChars>, peuvent être modifiées par votre code ou par un code qui partage le domaine d'application de votre code.  Vous ne devez pas utiliser de champs de tableau publics en lecture seule pour définir le comportement des limites de vos applications.  Si vous le faites, un code malveillant risque de modifier les définitions des limites et d'utiliser votre code de façon inattendue.  
  
 Dans les versions 2.0 et ultérieures du .NET Framework, vous devez utiliser des méthodes qui retournent un nouveau tableau au lieu d'utiliser des champs de tableau publics.  Par exemple, au lieu d'utiliser le champ <xref:System.IO.Path.InvalidPathChars>, vous devez utiliser la méthode <xref:System.IO.Path.GetInvalidPathChars%2A>.  
  
 Notez que les types .NET Framework n'utilisent pas les champs publics pour définir des types de limites en interne.  Le .NET Framework utilise plutôt des champs privés séparés.  La modification des valeurs de ces champs publics ne modifie pas le comportement des types .NET Framework.  
  
## Voir aussi  
 [Instructions de codage sécurisé](../../../docs/standard/security/secure-coding-guidelines.md)