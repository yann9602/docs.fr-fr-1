---
title: "Modifications apport&#233;es &#224; l’espace de noms System.Uri dans la Version&#160;2.0 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
ms.assetid: 35883fe9-2d09-4d8b-80ca-cf23a941e459
caps.latest.revision: 9
author: "mcleblanc"
ms.author: "markl"
manager: "markl"
caps.handback.revision: 9
---
# Modifications apport&#233;es &#224; l’espace de noms System.Uri dans la Version&#160;2.0
Plusieurs modifications ont été apportées à la classe d' <xref:System.Uri?displayProperty=fullName> .  Ces modifications ont résolu le comportement incorrect, la facilité d'utilisation améliorée, et la sécurité renforcée.  
  
## Membres obsolètes et déconseillés  
 Constructeurs :  
  
-   Tous les constructeurs qui ont un paramètre d' `dontEscape`.  
  
 Méthodes :  
  
-   <xref:System.Uri.CheckSecurity%2A>  
  
-   <xref:System.Uri.Escape%2A>  
  
-   <xref:System.Uri.Canonicalize%2A>  
  
-   <xref:System.Uri.Parse%2A>  
  
-   <xref:System.Uri.IsReservedCharacter%2A>  
  
-   <xref:System.Uri.IsBadFileSystemCharacter%2A>  
  
-   <xref:System.Uri.IsExcludedCharacter%2A>  
  
-   <xref:System.Uri.EscapeString%2A>  
  
## Modifications  
  
-   Pour les modèles URI connus pour ne pas avoir une partie de requête \(fichier, FTP, etc.\), « ? » le caractère d'échappement est toujours et n'est pas considéré comme le début d'une partie d' <xref:System.Uri.Query%2A> .  
  
-   Pour le fichier implicite URI \(sous la forme « c:\\directory\\file @name.txt »\), le \(" \# "\) de caractère de fragment est toujours d'échappement à moins qu'unescaping complet est demandé ou <xref:System.Uri.LocalPath%2A> est `true`.  
  
-   La prise en charge de hostname UNC a été supprimé ; la spécification IDN pour représenter les hostnames internationales a été adopté.  
  
-   <xref:System.Uri.LocalPath%2A> retourne toujours une chaîne complètement sans séquence d'échappement.  
  
-   <xref:System.Uri.ToString%2A> n'est pas unescape un échappement « % », « ?  », ou « &#124; ».  
  
-   <xref:System.Uri.Equals%2A> inclut désormais la partie d' <xref:System.Uri.Query%2A> dans le contrôle d'égalité.  
  
-   « \=\= » D'opérateurs et « \! \= » sont remplacés et liés à <xref:System.Uri.Equals%2A> la méthode.  
  
-   <xref:System.Uri.IsLoopback%2A> produit désormais des résultats cohérents.  
  
-   L'URI « `file:///path` » n'est plus traduit en « file:\/\/path ».  
  
-   « &#124; » est maintenant reconnu comme une Terminator de nom d'hôte.  Autrement dit, « http:\/\/consoto.com\#fragment » est maintenant converti en « http:\/\/contoso.com\/\#fragment ».  
  
-   Un bogue une combinaison URI de base avec un fragment a été résolu.  
  
-   Un bogue dans <xref:System.Uri.HostNameType%2A> est résolu.  
  
-   Un bogue dans l'analyse de NNTP est résolu.  
  
-   URI de la forme HTTP:contoso.com lève maintenant une exception d'analyse.  
  
-   L'infrastructure gère correctement l'userinfo dans un URI.  
  
-   La compression de chemin d'URI est résolu afin que l'URI rompu ne puisse pas parcourir le système de fichiers au\-dessus de la racine.  
  
## Voir aussi  
 <xref:System.Uri?displayProperty=fullName>