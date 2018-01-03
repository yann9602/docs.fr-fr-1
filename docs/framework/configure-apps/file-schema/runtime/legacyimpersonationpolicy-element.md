---
title: "&lt;legacyImpersonationPolicy&gt; élément"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#legacyImpersonationPolicy
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/runtime/legacyImpersonationPolicy
helpviewer_keywords:
- <legacyImpersonationPolicy> element
- legacyImpersonationPolicy element
ms.assetid: 6e00af10-42f3-4235-8415-1bb2db78394e
caps.latest.revision: "15"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: caeede11d8128af00beb5b1b3426e8c4a5406520
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="ltlegacyimpersonationpolicygt-element"></a>&lt;legacyImpersonationPolicy&gt; élément
Spécifie que l’identité Windows n’est pas transmise entre des points asynchrones, indépendamment des paramètres de flux du contexte d’exécution sur le thread actif.  
  
 \<configuration>  
\<runtime >  
\<legacyImpersonationPolicy >  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<legacyImpersonationPolicy    
   enabled="true|false"/>  
```  
  
## <a name="attributes-and-elements"></a>Attributs et éléments  
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### <a name="attributes"></a>Attributs  
  
|Attribut|Description|  
|---------------|-----------------|  
|`enabled`|Attribut requis.<br /><br /> Spécifie que le <xref:System.Security.Principal.WindowsIdentity> n’est pas transmis entre des points asynchrones, quel que soit le <xref:System.Threading.ExecutionContext> de flux de paramètres sur le thread actuel.|  
  
## <a name="enabled-attribute"></a>Attribut enabled  
  
|Valeur|Description|  
|-----------|-----------------|  
|`false`|<xref:System.Security.Principal.WindowsIdentity>flux entre des points asynchrones en fonction de la <xref:System.Threading.ExecutionContext> de flux de paramètres pour le thread actuel. Il s'agit de la valeur par défaut.|  
|`true`|<xref:System.Security.Principal.WindowsIdentity>n’est pas transmis entre des points asynchrones, quel que soit le <xref:System.Threading.ExecutionContext> de flux de paramètres sur le thread actuel.|  
  
### <a name="child-elements"></a>Éléments enfants  
 Aucun.  
  
### <a name="parent-elements"></a>Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|`configuration`|Élément racine de chaque fichier de configuration utilisé par le Common Language Runtime et les applications .NET Framework.|  
|`runtime`|Contient des informations sur les liaisons d’assembly et l’opération garbage collection.|  
  
## <a name="remarks"></a>Notes  
 Dans les versions du .NET Framework 1.0 et 1.1, la <xref:System.Security.Principal.WindowsIdentity> n’est pas transmis entre des points asynchrones définis par l’utilisateur. À compter de .NET Framework version 2.0, il existe un <xref:System.Threading.ExecutionContext> flux d’objet qui contient des informations sur le thread en cours d’exécution et il entre des points asynchrones dans un domaine d’application. Le <xref:System.Security.Principal.WindowsIdentity> est inclus dans ce contexte d’exécution et donc également transmise entre des points asynchrones, ce qui signifie que si un contexte d’emprunt d’identité existe, il transmet également.  
  
 À compter de .NET Framework 2.0, vous pouvez utiliser la `<legacyImpersonationPolicy>` élément pour spécifier que <xref:System.Security.Principal.WindowsIdentity> n’est pas transmis entre des points asynchrones.  
  
> [!NOTE]
>  Le common language runtime (CLR) est informé de l’emprunt d’identité opérations effectuées avec uniquement du code managé, pas de l’emprunt d’identité effectuée en dehors du code managé, comme par plate-forme code non managé au code non managé ou via des appels directs aux fonctions Win32. Managé <xref:System.Security.Principal.WindowsIdentity> objets peuvent être transmis entre des points asynchrones, à moins que le `alwaysFlowImpersonationPolicy` élément a été défini sur true (`<alwaysFlowImpersonationPolicy enabled="true"/>`). Définition de la `alwaysFlowImpersonationPolicy` élément true spécifie que l’identité Windows est toujours transmise entre des points asynchrones, quelle que soit la façon dont l’emprunt d’identité a été effectuée. Pour plus d’informations sur la transmission non managé à l’emprunt d’identité entre des points asynchrones, consultez [ \<alwaysFlowImpersonationPolicy > élément](../../../../../docs/framework/configure-apps/file-schema/runtime/alwaysflowimpersonationpolicy-element.md).  
  
 Vous pouvez modifier ce comportement par défaut de deux manières différentes :  
  
1.  Dans le code managé sur une base par thread.  
  
     Vous pouvez supprimer le flux sur une base par thread en modifiant le <xref:System.Threading.ExecutionContext> et <xref:System.Security.SecurityContext> paramètres à l’aide de la <xref:System.Threading.ExecutionContext.SuppressFlow%2A?displayProperty=nameWithType>, <xref:System.Security.SecurityContext.SuppressFlowWindowsIdentity%2A?displayProperty=nameWithType> ou <xref:System.Security.SecurityContext.SuppressFlow%2A?displayProperty=nameWithType> (méthode).  
  
2.  Dans l’appel à l’interface d’hébergement non managée pour charger le common language runtime (CLR).  
  
     Si une interface d’hébergement non managée (au lieu d’un simple fichier exécutable managé) est utilisée pour charger le CLR, vous pouvez spécifier un indicateur spécial dans l’appel à la [fonction CorBindToRuntimeEx](../../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md) (fonction). Pour activer le mode de compatibilité pour l’ensemble du processus, définissez la `flags` paramètre [fonction CorBindToRuntimeEx](../../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md) valeur STARTUP_LEGACY_IMPERSONATION au.  
  
 Pour plus d’informations, consultez la [ \<alwaysFlowImpersonationPolicy > élément](../../../../../docs/framework/configure-apps/file-schema/runtime/alwaysflowimpersonationpolicy-element.md).  
  
## <a name="configuration-file"></a>Fichier de configuration  
 Dans une application .NET Framework, cet élément peut être utilisé uniquement dans le fichier de configuration d’application.  
  
 Pour une application ASP.NET, le flux de l’emprunt d’identité peut être configuré dans le fichier aspnet.config trouvé dans le \<dossier Windows > \Microsoft.NET\Framework\vx.x.xxxx active.  
  
 ASP.NET par défaut désactive le flux de l’emprunt d’identité dans le fichier aspnet.config à l’aide de paramètres de configuration suivants :  
  
```  
configuration>  
   <runtime>  
      <legacyImpersonationPolicy enabled="true"/>  
      <alwaysFlowImpersonationPolicy enabled="false"/>  
   </runtime>  
</configuration>  
```  
  
 Dans ASP.NET, si vous souhaitez autoriser le flux d’emprunt d’identité à la place, vous devez utiliser explicitement les paramètres de configuration suivants :  
  
```xml  
<configuration>  
   <runtime>  
      <legacyImpersonationPolicy enabled="false"/>  
      <alwaysFlowImpersonationPolicy enabled="true"/>  
   </runtime>  
</configuration>  
```  
  
## <a name="example"></a>Exemple  
 L’exemple suivant montre comment spécifier le comportement hérité qui ne transmet pas l’identité Windows entre des points asynchrones.  
  
```xml  
<configuration>  
   <runtime>  
      <legacyImpersonationPolicy enabled="true"/>  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Schéma des paramètres d’exécution](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)  
 [Schéma des fichiers de configuration](../../../../../docs/framework/configure-apps/file-schema/index.md)  
 [\<alwaysFlowImpersonationPolicy > élément](../../../../../docs/framework/configure-apps/file-schema/runtime/alwaysflowimpersonationpolicy-element.md)
