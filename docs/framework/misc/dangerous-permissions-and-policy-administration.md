---
title: "Autorisations dangereuses et administration de strat&#233;gie | Microsoft Docs"
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
  - "sécurité du code, autorisations dangereuses"
  - "autorisations (.NET Framework), dangereuses"
  - "autorisations (.NET Framework), administration de stratégie"
  - "codage sécurisé, autorisations dangereuses"
  - "sécurité (.NET Framework), autorisations dangereuses"
ms.assetid: 1929e854-23a0-4bb1-94be-e8aa3b609e32
caps.latest.revision: 11
author: "mairaw"
ms.author: "mairaw"
manager: "wpickett"
caps.handback.revision: 11
---
# Autorisations dangereuses et administration de strat&#233;gie
Plusieurs des opérations protégées pour lesquelles le .NET Framework fournit des autorisations risquent de permettre le contournement du système de sécurité. Ces autorisations dangereuses doivent être accordées uniquement à du code fiable, et seulement en cas de nécessité. Il n’existe généralement aucune défense contre du code malveillant, si ces autorisations sont accordées.  
  
> [!NOTE]
>  Dans le [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)], des modifications importantes ont été apportées à la terminologie et au modèle de sécurité du .NET Framework. Pour plus d’informations sur ces changements, consultez [Modifications de sécurité](../../../docs/framework/security/security-changes.md).  
  
 Les autorisations dangereuses sont expliquées dans le tableau suivant.  
  
|Autorisation|Risque potentiel|  
|------------------|----------------------|  
|<xref:System.Security.Permissions.SecurityPermission>||  
|<xref:System.Security.Permissions.SecurityPermissionFlag>|Permet au code managé d’appeler du code non managé, ce qui est souvent dangereux.|  
|<xref:System.Security.Permissions.SecurityPermissionFlag>|En l’absence de vérification, le code peut tout faire.|  
|<xref:System.Security.Permissions.SecurityPermissionFlag>|Les preuves invalidées peuvent tromper la stratégie de sécurité.|  
|<xref:System.Security.Permissions.SecurityPermissionFlag>|La modification de la stratégie de sécurité peut permettre de désactiver la sécurité.|  
|<xref:System.Security.Permissions.SecurityPermissionFlag>|L’utilisation de la sérialisation peut constituer un moyen de contourner les mécanismes d’accessibilité. Pour plus d’informations, consultez [Sécurité et sérialisation](../../../docs/framework/misc/security-and-serialization.md).|  
|<xref:System.Security.Permissions.SecurityPermissionFlag>|La capacité à définir le principal actuel peut permettre de tromper la sécurité basée sur les rôles.|  
|<xref:System.Security.Permissions.SecurityPermissionFlag>|La manipulation des threads est dangereuse en raison de l’état de sécurité associé aux threads.|  
|<xref:System.Security.Permissions.ReflectionPermission>||  
|<xref:System.MemberAccessException>|Permet d’utiliser des membres privés pour passer outre les mécanismes d’accessibilité.|  
  
## Voir aussi  
 [Instructions de codage sécurisé](../../../docs/standard/security/secure-coding-guidelines.md)