---
title: "Remplacement d&#39;un objet Principal | Microsoft Docs"
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
  - "objets principaux, remplacer"
  - "sécurité (.NET Framework), principaux"
  - "sécurité (.NET Framework), remplacer des objets principaux"
ms.assetid: c323687e-b196-487b-beba-f38f9b3f961b
caps.latest.revision: 13
author: "mairaw"
ms.author: "mairaw"
manager: "wpickett"
caps.handback.revision: 13
---
# Remplacement d&#39;un objet Principal
Les applications qui fournissent des services d’authentification doivent pouvoir remplacer l’objet **Principal** \(<xref:System.Security.Principal.IPrincipal>\) d’un thread donné. En outre, le système de sécurité doit permettre de protéger la possibilité de remplacer les objets **Principal** si un **Principal** malveillant et incorrect attaché compromet la sécurité de votre application en simulant une fausse identité ou un faux rôle. Par conséquent, les applications ayant besoin de pouvoir remplacer les objets **Principal** doivent se voir attribuer l’objet <xref:System.Security.Permissions.SecurityPermission?displayProperty=fullName> pour le contrôle du principal. \(Notez que cette autorisation n’est pas obligatoire pour effectuer des vérifications de sécurité basée sur les rôles ou créer des objets **Principal**.\)  
  
 L’objet **Principal** actuel peut être remplacé en effectuant les tâches suivantes :  
  
1.  Créer l’objet **Principal** de remplacement et l’objet **Identity** associé.  
  
2.  Attacher le nouvel objet **Principal** au contexte d’appel.  
  
## Exemple  
 L’exemple suivant montre comment créer un objet principal générique et l’utiliser pour définir le principal d’un thread.  
  
 [!code-csharp[SetCurrentPrincipal#1](../../../samples/snippets/csharp/VS_Snippets_CLR/SetCurrentPrincipal/CS/program.cs#1)]
 [!code-vb[SetCurrentPrincipal#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/SetCurrentPrincipal/VB/program.vb#1)]  
  
## Voir aussi  
 <xref:System.Security.Permissions.SecurityPermission?displayProperty=fullName>   
 [Objets Principal et Identity](../../../docs/standard/security/principal-and-identity-objects.md)