---
title: "&lt;disableFusionUpdatesFromADManager&gt; élément"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- disableFusionUpdatesFromADManager element
- <disableFusionUpdatesFromADManager> element
ms.assetid: 58d2866c-37bd-4ffa-abaf-ff35926a2939
caps.latest.revision: "7"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: d4aa3343e7f3f60bbf6a57340d858c1ef12197bb
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="ltdisablefusionupdatesfromadmanagergt-element"></a>&lt;disableFusionUpdatesFromADManager&gt; élément
Indique si le comportement par défaut, qui consiste à permettre à l’hôte du runtime de remplacer les paramètres de configuration d’un domaine d’application, est désactivé.  
  
 \<configuration > élément  
\<runtime > élément  
\<disableFusionUpdatesFromADManager >  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<disableFusionUpdatesFromADManager enabled="0|1"/>  
```  
  
## <a name="attributes-and-elements"></a>Attributs et éléments  
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### <a name="attributes"></a>Attributs  
  
|Attribut|Description|  
|---------------|-----------------|  
|enabled|Attribut requis.<br /><br /> Spécifie si la possibilité de valeur par défaut pour remplacer les paramètres de Fusion est désactivée.|  
  
## <a name="enabled-attribute"></a>Attribut enabled  
  
|Valeur|Description|  
|-----------|-----------------|  
|0|Ne désactivez pas la possibilité de remplacer les paramètres de Fusion. Il s’agit du comportement par défaut, en commençant par le [!INCLUDE[net_v40_long](../../../../../includes/net-v40-long-md.md)].|  
|1|Désactiver la possibilité de remplacer les paramètres de Fusion. Cela rétablit le comportement des versions antérieures du .NET Framework.|  
  
### <a name="child-elements"></a>Éléments enfants  
 Aucun.  
  
### <a name="parent-elements"></a>Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|`configuration`|Élément racine de chaque fichier de configuration utilisé par le Common Language Runtime et les applications .NET Framework.|  
|`runtime`|Contient des informations sur les liaisons d’assembly et l’opération garbage collection.|  
  
## <a name="remarks"></a>Remarques  
 En commençant par le [!INCLUDE[net_v40_long](../../../../../includes/net-v40-long-md.md)], le comportement par défaut consiste à autoriser la <xref:System.AppDomainManager> objet à remplacer les paramètres de configuration à l’aide de la <xref:System.AppDomainSetup.ConfigurationFile%2A> propriété ou le <xref:System.AppDomainSetup.SetConfigurationBytes%2A> méthode de la <xref:System.AppDomainSetup> objet est passé à votre implémentation de la <xref:System.AppDomainManager.InitializeNewDomain%2A?displayProperty=nameWithType> (méthode), dans votre sous-classe de <xref:System.AppDomainManager>. Pour le domaine d’application par défaut, les paramètres que vous modifiez remplacent les paramètres qui ont été spécifiés par le fichier de configuration d’application. Pour les autres domaines d’application, ils remplacent les paramètres de configuration qui ont été passés à la <xref:System.AppDomainManager.CreateDomain%2A?displayProperty=nameWithType> ou <xref:System.AppDomain.CreateDomain%2A?displayProperty=nameWithType> (méthode).  
  
 Vous pouvez passer de nouvelles informations de configuration, ou passez la valeur null (`Nothing` en Visual Basic) pour éliminer les informations de configuration qui a été passées.  
  
 Ne passez pas d’informations de configuration à la fois à la <xref:System.AppDomainSetup.ConfigurationFile%2A> propriété et la <xref:System.AppDomainSetup.SetConfigurationBytes%2A> (méthode). Si vous transmettez des informations de configuration à la fois, les informations que vous passez à la <xref:System.AppDomainSetup.ConfigurationFile%2A> propriété est ignorée, car le <xref:System.AppDomainSetup.SetConfigurationBytes%2A> méthode substitue les informations de configuration à partir du fichier de configuration d’application. Si vous utilisez la <xref:System.AppDomainSetup.ConfigurationFile%2A> propriété, vous pouvez passer null (`Nothing` en Visual Basic) pour le <xref:System.AppDomainSetup.SetConfigurationBytes%2A> méthode pour éliminer les octets de configuration qui ont été spécifiés dans l’appel à la <xref:System.AppDomainManager.CreateDomain%2A?displayProperty=nameWithType> ou <xref:System.AppDomain.CreateDomain%2A?displayProperty=nameWithType> (méthode).  
  
 En plus des informations de configuration, vous pouvez modifier les paramètres suivants sur le <xref:System.AppDomainSetup> objet qui est passé à votre implémentation de la <xref:System.AppDomainManager.InitializeNewDomain%2A?displayProperty=nameWithType> méthode : <xref:System.AppDomainSetup.ApplicationBase%2A>, <xref:System.AppDomainSetup.ApplicationName%2A>, <xref:System.AppDomainSetup.CachePath%2A>, <xref:System.AppDomainSetup.DisallowApplicationBaseProbing%2A>, <xref:System.AppDomainSetup.DisallowBindingRedirects%2A> , <xref:System.AppDomainSetup.DisallowCodeDownload%2A>, <xref:System.AppDomainSetup.DisallowPublisherPolicy%2A>, <xref:System.AppDomainSetup.DynamicBase%2A>, <xref:System.AppDomainSetup.LoaderOptimization%2A>, <xref:System.AppDomainSetup.PrivateBinPath%2A>, <xref:System.AppDomainSetup.PrivateBinPathProbe%2A>, <xref:System.AppDomainSetup.ShadowCopyDirectories%2A>, et <xref:System.AppDomainSetup.ShadowCopyFiles%2A>.  
  
 En guise d’alternative à l’utilisation de la `<disableFusionUpdatesFromADManager>` élément, vous pouvez désactiver le comportement par défaut en créant un paramètre de Registre ou en définissant une variable d’environnement. Dans le Registre, créez une valeur DWORD nommée `COMPLUS_disableFusionUpdatesFromADManager` sous `HKCU\Software\Microsoft\.NETFramework` ou `HKLM\Software\Microsoft\.NETFramework`et définissez la valeur sur 1. Sur la ligne de commande, définissez la variable d’environnement `COMPLUS_disableFusionUpdatesFromADManager` sur 1.  
  
## <a name="example"></a>Exemple  
 L’exemple suivant montre comment désactiver la possibilité de remplacer les paramètres de Fusion à l’aide de la `<disableFusionUpdatesFromADManager>` élément.  
  
```xml  
<configuration>  
   <runtime>  
      <disableFusionUpdatesFromADManager enabled="1" />  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Schéma des paramètres d’exécution](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)  
 [Schéma des fichiers de configuration](../../../../../docs/framework/configure-apps/file-schema/index.md)  
 [Méthode de localisation des assemblys par le runtime](../../../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md)
