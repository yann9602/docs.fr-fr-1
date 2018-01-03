---
title: IAppDomainSetup, interface
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IAppDomainSetup
api_location: mscoree.dll
api_type: COM
f1_keywords: IAppDomainSetup
helpviewer_keywords: IAppDomainSetup interface [.NET Framework hosting]
ms.assetid: 1844da85-c031-40bf-bea4-1a3d12a36c8c
topic_type: apiref
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 9db1b787015231b3d9053d4ed316cb70c5db96ec
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="iappdomainsetup-interface"></a>IAppDomainSetup, interface
Fournit des propriétés qui permettent à l’hôte configurer un <xref:System.AppDomain?displayProperty=nameWithType> type avant d’appeler le [ICorRuntimeHost::CreateDomainEx](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-createdomainex-method.md) méthode pour le créer.  
  
## <a name="properties"></a>Propriétés  
  
|Propriété|Description|  
|--------------|-----------------|  
|<xref:System.AppDomainSetup.ApplicationBase%2A>|Obtient ou définit le nom du répertoire qui contient l’application.|  
|<xref:System.AppDomainSetup.ApplicationName%2A>|Obtient ou définit le nom de l'application.|  
|<xref:System.AppDomainSetup.CachePath%2A>|Obtient ou définit le nom d’une zone spécifique à l’application où les fichiers sont copiés de clichés instantanés.|  
|<xref:System.AppDomainSetup.ConfigurationFile%2A>|Obtient ou définit le nom du fichier de configuration pour une application.|  
|<xref:System.AppDomainSetup.DynamicBase%2A>|Obtient ou définit le nom du répertoire où les fichiers générés de manière dynamique sont stockés et accessibles.|  
|<xref:System.AppDomainSetup.LicenseFile%2A>|Obtient ou définit le chemin d’accès du fichier de licence associé à ce domaine.|  
|<xref:System.AppDomainSetup.PrivateBinPath%2A>|Obtient ou définit la liste des répertoires associés la <xref:System.AppDomainSetup.ApplicationBase%2A> active pour détecter les assemblys privés.|  
|<xref:System.AppDomainSetup.PrivateBinPathProbe%2A>|Obtient ou définit une valeur de chaîne qui inclut ou exclut <xref:System.AppDomainSetup.ApplicationBase%2A> du chemin de recherche pour l’application.|  
|<xref:System.AppDomainSetup.ShadowCopyDirectories%2A>|Obtient ou définit les noms des répertoires qui contiennent des assemblys pour être le cliché instantané.|  
|<xref:System.AppDomainSetup.ShadowCopyFiles%2A>|Obtient ou définit une chaîne qui indique si la copie de clichés instantanés est activée ou désactivée. Les valeurs valides sont « true » ou « false ».|  
  
## <a name="remarks"></a>Notes  
 Le `IAppDomainSetup` interface correspond à managé <xref:System.IAppDomainSetup> d’interface, ce qui le <xref:System.AppDomainSetup> type implémente. Consultez <xref:System.IAppDomainSetup?displayProperty=nameWithType> pour une description détaillée de ses propriétés.  
  
 `IAppDomainSetup`représente des informations de liaison d’assembly qui peuvent être ajoutées à un <xref:System.AppDomain> instance avant sa création. Par exemple, un hôte peut définir le <xref:System.AppDomainSetup.ApplicationBase%2A> propriété pour définir un répertoire racine dans lequel le common language runtime (CLR) recherche des assemblys managés.  
  
## <a name="requirements"></a>Configuration requise  
 **Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** MSCorEE.h  
  
 **Bibliothèque :** inclus en tant que ressource dans MSCorEE.dll  
  
 **Versions du .NET framework :**[!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.AppDomain>  
 <xref:System.AppDomainSetup>  
 <xref:System.IAppDomainSetup>  
 [Interfaces d’hébergement](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
