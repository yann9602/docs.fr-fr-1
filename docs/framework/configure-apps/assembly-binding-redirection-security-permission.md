---
title: "Autorisation de sécurité pour la redirection de liaison d’assembly"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- side-by-side execution, assembly binding redirection
- assemblies [.NET Framework], binding redirection
ms.assetid: 24a5cdff-7ed9-4195-93f3-edf6899019fc
caps.latest.revision: "9"
author: mcleblanc
ms.author: markl
manager: markl
ms.workload: dotnet
ms.openlocfilehash: d2593df04b93db17f9ca61a98b21aaec1d534d46
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/19/2018
---
# <a name="assembly-binding-redirection-security-permission"></a>Autorisation de sécurité pour la redirection de liaison d’assembly
La redirection de liaison d’assembly explicite dans un fichier de configuration de l’application nécessite une autorisation de sécurité. Cela s'applique à la redirection des assemblys .NET Framework et des assemblys tiers. L’autorisation est accordée en définissant le <xref:System.Security.Permissions.SecurityPermissionFlag> indicateur sur le <xref:System.Security.Permissions.SecurityPermission>. Les assemblys managés ne possèdent aucuns autorisations par défaut.  
  
 L’autorisation de sécurité est accordée aux applications en cours d’exécution dans la Zone de confiance (ordinateur local) et de la Zone Intranet. Applications en cours d’exécution dans la Zone Internet sont strictement interdite d’effectuer la redirection de liaison d’assembly.  
  
 L’autorisation n’est pas nécessaire si la redirection d’assembly est exécutée dans un fichier de stratégie d’éditeur qui est contrôlé par l’éditeur de composant, ou dans le fichier de configuration d’ordinateur qui est contrôlé par l’administrateur. Toutefois, l’autorisation est nécessaire pour une application ignore explicitement la stratégie du serveur de publication à l’aide du [ \<publisherPolicy appliquer = « no » / >](../../../docs/framework/configure-apps/file-schema/runtime/publisherpolicy-element.md) élément dans le fichier de configuration d’application.  
  
 Le tableau suivant présente la valeur par défaut des paramètres de sécurité pour le **BindingRedirects** indicateur.  
  
|Zone|Paramètre d’indicateur BindingRedirects|  
|----------|-----------------------------------|  
|Zone de confiance (ordinateur local)|**ON**|  
|Zone intranet|**ON**|  
|Zone Internet|**OFF**|  
|Zones non fiables|**OFF**|  
  
 Un administrateur peut modifier ces paramètres de sécurité pour prendre en charge ou restreindre des scénarios spécifiques sur un ordinateur donné. Aucun outil permettant de modifier le **BindingRedirects** indicateur de définition à partir de la valeur par défaut ; un administrateur doit modifier manuellement le fichier Security.config sur l’ordinateur d’un utilisateur.  
  
## <a name="see-also"></a>Voir aussi  
 [Fichiers de stratégie d’éditeur et de l’exécution de côte à côte](http://msdn.microsoft.com/library/97a042be-4d72-40c3-91c0-76fd36bdf133)  
 [Comment : activer et désactiver la redirection de liaison automatique](../../../docs/framework/configure-apps/how-to-enable-and-disable-automatic-binding-redirection.md)  
 [Exécution côte à côte](../../../docs/framework/deployment/side-by-side-execution.md)
