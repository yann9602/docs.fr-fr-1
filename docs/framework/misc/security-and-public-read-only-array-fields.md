---
title: "Sécurité et champs de tableau en lecture seule publics"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: security [.NET Framework], public read-only array fields
ms.assetid: 3df28dee-2a9f-40ff-9852-bfdbe59c27f3
caps.latest.revision: "7"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: d86d054d3a5a4e10b8efcc3292f3a18ea37f9b87
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="security-and-public-read-only-array-fields"></a>Sécurité et champs de tableau en lecture seule publics
Utilisez jamais les champs de tableau publics en lecture seule à partir de bibliothèques managées pour définir le comportement de limites ou la sécurité de vos applications, car les champs de tableau publics en lecture seule peuvent être modifiés.  
  
## <a name="remarks"></a>Notes  
 Certaines classes .NET framework incluent des champs publics en lecture seule qui contiennent des paramètres spécifiques à la plateforme limite.  Par exemple, le <xref:System.IO.Path.InvalidPathChars> champ est un tableau qui décrit les caractères qui ne sont pas autorisés dans une chaîne de chemin d’accès de fichier.  De nombreux champs semblables sont présents dans le .NET Framework.  
  
 Les valeurs des champs publics en lecture seule comme <xref:System.IO.Path.InvalidPathChars> peut être modifié par votre code ou le code qui partage le domaine d’application de votre code.  Vous ne devez pas utiliser les champs de tableau publics en lecture seule comme suit pour définir le comportement des limites de vos applications.  Si vous le faites, un code malveillant peut modifier les définitions des limites et votre code de façon inattendue.  
  
 Dans la version 2.0 et ultérieures du .NET Framework, vous devez utiliser des méthodes qui retournent un nouveau tableau au lieu d’utiliser les champs de tableau publics.  Par exemple, au lieu d’utiliser le <xref:System.IO.Path.InvalidPathChars> champ, vous devez utiliser le <xref:System.IO.Path.GetInvalidPathChars%2A> (méthode).  
  
 Notez que les types .NET Framework n’utilisent pas de champs publics pour définir des types de limites en interne.  Au lieu de cela, le .NET Framework utilise des champs privés séparés.  Modification des valeurs de ces champs publics ne modifie pas le comportement des types .NET Framework.  
  
## <a name="see-also"></a>Voir aussi  
 [Instructions de codage sécurisé](../../../docs/standard/security/secure-coding-guidelines.md)
