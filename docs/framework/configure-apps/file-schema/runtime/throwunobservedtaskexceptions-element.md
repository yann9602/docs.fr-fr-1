---
title: "&lt;ThrowUnobservedTaskExceptions&gt; élément"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- ThrowUnobservedTaskExceptions element
- <ThrowUnobservedTaskExceptions> element
ms.assetid: cea7e588-8b8d-48d2-9ad5-8feaf3642c18
caps.latest.revision: "6"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 635270a6461b573663b7719843d81ff2b23e63dd
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="ltthrowunobservedtaskexceptionsgt-element"></a>&lt;ThrowUnobservedTaskExceptions&gt; élément
Indique si les exceptions de tâches non gérées doivent arrêter un processus en cours d’exécution.  
  
 \<configuration>  
\<runtime >  
\<ThrowUnobservedTaskExceptions >  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<ThrowUnobservedTaskExceptions  
   enabled="true|false"/>  
```  
  
## <a name="attributes-and-elements"></a>Attributs et éléments  
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### <a name="attributes"></a>Attributs  
  
|Attribut|Description|  
|---------------|-----------------|  
|`enabled`|Attribut requis.<br /><br /> Spécifie si les exceptions de tâche non gérée doivent s’arrêter le processus en cours d’exécution.|  
  
## <a name="enabled-attribute"></a>Attribut enabled  
  
|Valeur|Description|  
|-----------|-----------------|  
|`false`|N’arrête pas le processus en cours d’exécution pour une exception de tâche non gérée. Il s'agit de la valeur par défaut.|  
|`true`|Termine le processus en cours d’exécution pour une exception de tâche non gérée.|  
  
### <a name="child-elements"></a>Éléments enfants  
 Aucun.  
  
### <a name="parent-elements"></a>Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|`configuration`|Élément racine de chaque fichier de configuration utilisé par le Common Language Runtime et les applications .NET Framework.|  
|`runtime`|Contient des informations sur les options d'initialisation du runtime.|  
|||  
  
## <a name="remarks"></a>Notes  
 Si une exception qui est associée à un <xref:System.Threading.Tasks.Task> n’a pas été respectées, il est sans <xref:System.Threading.Tasks.Task.Wait%2A> opération, le parent n’est pas attachée et le <xref:System.Threading.Tasks.Task.Exception%2A?displayProperty=nameWithType> propriété n’a pas lu à l’exception de la tâche est considérée comme défaillante.  
  
 Dans le [!INCLUDE[net_v40_long](../../../../../includes/net-v40-long-md.md)], par défaut, si un <xref:System.Threading.Tasks.Task> qui a un défaillante exception est le garbage collector, le finaliseur lève une exception et met fin au processus. L’arrêt du processus est déterminée par la durée du garbage collection et la finalisation.  
  
 Pour le rendre plus facile pour les développeurs d’écrire du code asynchrone basé sur les tâches, les [!INCLUDE[net_v45](../../../../../includes/net-v45-md.md)] modifie ce comportement par défaut pour les exceptions non prise en charge. Non prises en charge les exceptions d’entraînent toujours le <xref:System.Threading.Tasks.TaskScheduler.UnobservedTaskException> événement soit déclenché, mais par défaut, le processus s’arrête. Au lieu de cela, l’exception est ignorée une fois que l’événement est déclenché, indépendamment de si un gestionnaire d’événements observe l’exception.  
  
 Dans le [!INCLUDE[net_v45](../../../../../includes/net-v45-md.md)], vous pouvez utiliser la [ \<ThrowUnobservedTaskExceptions > élément](../../../../../docs/framework/configure-apps/file-schema/runtime/throwunobservedtaskexceptions-element.md) dans un fichier de configuration d’application pour activer la [!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)] comportement de lever une exception.  
  
 Vous pouvez également spécifier le comportement d’exception dans une des manières suivantes :  
  
-   En définissant la variable d’environnement `COMPlus_ThrowUnobservedTaskExceptions` (`set COMPlus_ThrowUnobservedTaskExceptions=1`).  
  
-   En définissant le Registre DWORD value ThrowUnobservedTaskExceptions = 1 dans le HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\\. NETFramework clé.  
  
## <a name="example"></a>Exemple  
 L’exemple suivant montre comment activer la levée d’exceptions dans les tâches à l’aide d’un fichier de configuration.  
  
```xml  
<configuration>   
    <runtime>   
        <ThrowUnobservedTaskExceptions enabled="true"/>   
    </runtime>   
</configuration>  
```  
  
## <a name="example"></a>Exemple  
 L’exemple suivant montre comment une propagation de l’exception est levée à partir d’une tâche. Le code doit être exécuté comme un programme lancé fonctionne correctement.  
  
 [!code-csharp[ThrowUnobservedTaskExceptions#1](../../../../../samples/snippets/csharp/VS_Snippets_CLR/throwunobservedtaskexceptions/cs/program.cs#1)]
 [!code-vb[ThrowUnobservedTaskExceptions#1](../../../../../samples/snippets/visualbasic/VS_Snippets_CLR/throwunobservedtaskexceptions/vb/program.vb#1)]  
  
## <a name="see-also"></a>Voir aussi  
 [Schéma des paramètres d’exécution](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)  
 [Schéma des fichiers de configuration](../../../../../docs/framework/configure-apps/file-schema/index.md)
