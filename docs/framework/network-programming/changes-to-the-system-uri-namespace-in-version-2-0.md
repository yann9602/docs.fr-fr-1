---
title: "Modifications apportées à l’espace de noms System.Uri dans la Version 2.0"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 35883fe9-2d09-4d8b-80ca-cf23a941e459
caps.latest.revision: "9"
author: mcleblanc
ms.author: markl
manager: markl
ms.workload: dotnet
ms.openlocfilehash: 3ebf74fbe7f2e207af8bf861efece58026148e2f
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="changes-to-the-systemuri-namespace-in-version-20"></a>Modifications apportées à l’espace de noms System.Uri dans la Version 2.0
Plusieurs modifications ont été apportées à la classe <xref:System.Uri?displayProperty=nameWithType>. Ces modifications éliminent un comportement incorrect, améliorent la convivialité et renforcent la sécurité.  
  
## <a name="obsolete-and-deprecated-members"></a>Membres obsolètes et dépréciés  
 Constructeurs :  
  
-   Tous les constructeurs qui ont un paramètre `dontEscape`.  
  
 Méthodes :  
  
-   <xref:System.Uri.CheckSecurity%2A>  
  
-   <xref:System.Uri.Escape%2A>  
  
-   <xref:System.Uri.Canonicalize%2A>  
  
-   <xref:System.Uri.Parse%2A>  
  
-   <xref:System.Uri.IsReservedCharacter%2A>  
  
-   <xref:System.Uri.IsBadFileSystemCharacter%2A>  
  
-   <xref:System.Uri.IsExcludedCharacter%2A>  
  
-   <xref:System.Uri.EscapeString%2A>  
  
## <a name="changes"></a>Modifications  
  
-   Pour les schémas d’URI qui sont connus comme n’ayant aucune partie de requête (file, ftp, etc.), le caractère « ? » est toujours placé dans une séquence d’échappement et n’est pas considéré comme le début d’une partie <xref:System.Uri.Query%2A>.  
  
-   Pour les URI de fichiers implicites (au format « c:\directory\file@name.txt »), le caractère de fragment (« # ») est toujours placé dans une séquence d’échappement, sauf si l’absence totale de séquence d’échappement est demandée ou si <xref:System.Uri.LocalPath%2A> est `true`.  
  
-   La prise en charge des noms d’hôtes UNC a été supprimée ; la spécification IDN pour la représentation des noms d’hôtes internationaux a été adoptée.  
  
-   <xref:System.Uri.LocalPath%2A> retourne toujours une chaîne sans séquence d’échappement.  
  
-   <xref:System.Uri.ToString%2A> ne supprime pas la séquence d’échappement d’un caractère « % », « ? » ou « # » placé dans une séquence d’échappement.  
  
-   <xref:System.Uri.Equals%2A> inclut désormais la partie <xref:System.Uri.Query%2A> dans la vérification de l’égalité.  
  
-   Les opérateurs « = » et « != » sont substitués et liés à la méthode <xref:System.Uri.Equals%2A>.  
  
-   <xref:System.Uri.IsLoopback%2A> produit maintenant des résultats cohérents.  
  
-   L’URI « `file:///path` » n’est plus traduite en « file://path ».  
  
-   « # » est maintenant reconnu comme un terminateur de nom d’hôte. Autrement dit, « http://consoto.com#fragment » est désormais converti en « http://contoso.com/#fragment ».  
  
-   Un bogue présent lors de la combinaison d’un URI de base avec un fragment a été résolu.  
  
-   Un bogue dans <xref:System.Uri.HostNameType%2A> a été résolu.  
  
-   Un bogue dans l’analyse NNTP a été résolu.  
  
-   Un URI au format HTTP:contoso.com lève désormais une exception d’analyse.  
  
-   Le Framework gère correctement userinfo dans un URI.  
  
-   La compression de chemin d’URI a été résolue afin qu’un URI rompu ne puisse pas parcourir le système de fichiers au-dessus de la racine.  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.Uri?displayProperty=nameWithType>
