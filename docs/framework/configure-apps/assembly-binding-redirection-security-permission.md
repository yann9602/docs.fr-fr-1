---
title: "Autorisation de s&#233;curit&#233; pour la redirection de liaison d&#39;assembly | Microsoft Docs"
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
  - "assemblys (.NET Framework), redirection de liaison"
  - "exécution côte à côte, redirection de liaison d'assembly"
ms.assetid: 24a5cdff-7ed9-4195-93f3-edf6899019fc
caps.latest.revision: 9
author: "mcleblanc"
ms.author: "markl"
manager: "markl"
caps.handback.revision: 8
---
# Autorisation de s&#233;curit&#233; pour la redirection de liaison d&#39;assembly
La redirection de liaison d'assembly explicite dans un fichier de configuration de l'application nécessite une autorisation de sécurité.  Cela s'applique à la redirection des assemblys .NET Framework et des assemblys tiers.  L'autorisation est accordée en définissant l'indicateur [BindingRedirects](frlrfSystemSecurityPermissionsSecurityPermissionFlagClassTopic) sur la [classe SecurityPermission](frlrfSystemSecurityPermissionsSecurityPermissionClassTopic).  Les assemblys managés n'ont pas d'autorisations par défaut.  
  
 L'autorisation de sécurité est accordée aux applications qui s'exécutent dans la Zone Intranet et la Zone de confiance \(ordinateur local\).  Les applications qui s'exécutent dans la Zone Internet ne sont pas autorisées à effectuer de redirection de liaison d'assembly.  
  
 L'autorisation n'est pas nécessaire si la redirection d'assembly s'effectue dans un fichier de stratégie d'éditeur contrôlé par l'éditeur de composant ou dans le fichier de configuration machine contrôlé par l'administrateur.  Cependant, l'autorisation est nécessaire pour qu'une application ignore explicitement la stratégie de l'éditeur à l'aide de l'élément [\<publisherPolicy apply\="no"\/\>](../../../docs/framework/configure-apps/file-schema/runtime/publisherpolicy-element.md) dans le fichier de configuration de l'application.  
  
 Le tableau suivant illustre les paramètres de sécurité par défaut pour l'indicateur **BindingRedirects**.  
  
|Zone|Paramètre d'indicateur BindingRedirects|  
|----------|---------------------------------------------|  
|Zone de confiance \(ordinateur local\)|**ON**|  
|Zone Intranet|**ON**|  
|Zone Internet|**OFF**|  
|Zones non fiables|**OFF**|  
  
 Un administrateur peut changer ces paramètres de sécurité pour prendre en charge ou restreindre des scénarios spécifiques sur un ordinateur donné.  Il n'existe pas d'outils permettant de changer le paramètre par défaut de l'indicateur **BindingRedirects**; un administrateur doit éditer manuellement le fichier Security.config sur l'ordinateur d'un utilisateur.  
  
## Voir aussi  
 [Publisher Policy Files and Side\-by\-Side Execution](http://msdn.microsoft.com/fr-fr/97a042be-4d72-40c3-91c0-76fd36bdf133)   
 [Comment : activer et désactiver la redirection de liaison automatique](../../../docs/framework/configure-apps/how-to-enable-and-disable-automatic-binding-redirection.md)   
 [Exécution côte à côte](../../../docs/framework/deployment/side-by-side-execution.md)