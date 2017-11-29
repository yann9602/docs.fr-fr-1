---
title: "&lt;etwEnable&gt; élément"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- etwEnable element
- <etwEnable> element
ms.assetid: 29dde982-6d8b-4099-8867-ad0d7733f6dc
caps.latest.revision: "7"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: b36c52338754df0f4fd3c963848e36afeb140501
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="ltetwenablegt-element"></a>&lt;etwEnable&gt; élément
Indique s’il faut activer le Suivi d’événements pour Windows (ETW) pour les événements du common language runtime.  
  
 \<configuration > élément  
\<runtime > élément  
\<etwEnabled >  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<etwEnable enabled="true|false"/>  
```  
  
## <a name="attributes-and-elements"></a>Attributs et éléments  
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### <a name="attributes"></a>Attributs  
  
|Attribut|Description|  
|---------------|-----------------|  
|enabled|Attribut requis.<br /><br /> Spécifie si ETW doit être activé.|  
  
## <a name="enabled-attribute"></a>Attribut enabled  
  
|Valeur|Description|  
|-----------|-----------------|  
|true|Activer ETW. Il s’agit de la valeur par défaut pour les versions de Windows qui commence avec les systèmes d’exploitation Windows Vista et Windows Server 2008.|  
|False|Désactiver ETW. Il s’agit de la valeur par défaut pour les versions antérieures de Windows.|  
  
### <a name="child-elements"></a>Éléments enfants  
 Aucun.  
  
### <a name="parent-elements"></a>Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|`configuration`|Élément racine de chaque fichier de configuration utilisé par le Common Language Runtime et les applications .NET Framework.|  
|`runtime`|Contient des informations sur les liaisons d’assembly et l’opération garbage collection.|  
  
## <a name="remarks"></a>Remarques  
 À compter de Windows Vista, ETW est activé par défaut. Utilisez cet élément pour désactiver ETW pour une application. Dans les versions antérieures de Windows, utilisez cet élément pour activer ETW pour une application.  
  
> [!NOTE]
>  ETW peut être activé ou désactivé globalement sur un serveur à l’aide d’un paramètre du Registre. Consultez [contrôle de l’enregistrement .NET Framework](../../../../../docs/framework/performance/controlling-logging.md).  
  
## <a name="example"></a>Exemple  
 L’exemple suivant montre comment activer le suivi ETW pour une application.  
  
```xml  
<configuration>  
   <runtime>  
      <etwEnable enabled="true" />  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Schéma des paramètres d’exécution](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)  
 [Schéma des fichiers de configuration](../../../../../docs/framework/configure-apps/file-schema/index.md)  
 [Contrôle de l’enregistrement .NET Framework](../../../../../docs/framework/performance/controlling-logging.md)
