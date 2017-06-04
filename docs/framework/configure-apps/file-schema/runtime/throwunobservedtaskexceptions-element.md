---
title: "&lt;ThrowUnobservedTaskExceptions&gt;, &#201;l&#233;ment | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
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
  - "<ThrowUnobservedTaskExceptions> (élément)"
  - "ThrowUnobservedTaskExceptions (élément)"
ms.assetid: cea7e588-8b8d-48d2-9ad5-8feaf3642c18
caps.latest.revision: 6
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 6
---
# &lt;ThrowUnobservedTaskExceptions&gt;, &#201;l&#233;ment
Spécifie si les exceptions non gérées de tâche doivent arrêter un processus en cours de exécution.  
  
## Syntaxe  
  
```vb  
<ThrowUnobservedTaskExceptions  
   enabled="true|false"/>  
```  
  
## Attributs et éléments  
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### Attributs  
  
|Attribut|Description|  
|--------------|-----------------|  
|`enabled`|Attribut requis.<br /><br /> Spécifie si les exceptions non gérées de tâche doivent arrêter le processus en cours de exécution.|  
  
## Attribut enabled  
  
|Valeur|Description|  
|------------|-----------------|  
|`false`|N'interrompt pas le traitement en cours pour une exception non prise en charge de travail.  Il s'agit de la valeur par défaut.|  
|`true`|Interrompt le traitement en cours pour une exception non prise en charge de travail.|  
  
### Éléments enfants  
 Aucun.  
  
### Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|`configuration`|Élément racine de chaque fichier de configuration utilisé par le Common Language Runtime et les applications .NET Framework.|  
|`runtime`|Contient des informations sur les options d'initialisation du runtime.|  
|||  
  
## Notes  
 Si une exception associée à <xref:System.Threading.Tasks.Task> n'a pas été chaîne observée, aucune opération <xref:System.Threading.Tasks.Task.Wait%2A>, le parent n'est pas attachée, et la propriété <xref:System.Threading.Tasks.Task.Exception%2A?displayProperty=fullName> n'a pas été lue l'exception de la tâche est considérée inaperçue.  
  
 Dans [!INCLUDE[net_v40_long](../../../../../includes/net-v40-long-md.md)], par défaut, si <xref:System.Threading.Tasks.Task> qui a une exception inaperçue est récupéré par le garbage collector, un finaliseur lève une exception et met fin au processus.  L'arrêt du processus est déterminé par celle du garbage collection et la finalisation.  
  
 Pour qu'il soit plus simple pour les développeurs d'écrire du code asynchrone basé sur des tâches, le [!INCLUDE[net_v45](../../../../../includes/net-v45-md.md)] modifie ce comportement par défaut pour les exceptions inaperçues.  Les exceptions inaperçues provoquent toujours l'événement <xref:System.Threading.Tasks.TaskScheduler.UnobservedTaskException> à déclencher, mais par défaut, le processus ne se termine pas.  Au lieu de cela, l'exception est ignorée après que l'événement soit déclenché, même si un gestionnaire d'événements respecte l'exception.  
  
 Dans [!INCLUDE[net_v45](../../../../../includes/net-v45-md.md)], vous pouvez utiliser [\<ThrowUnobservedTaskExceptions\> élément](../../../../../docs/framework/configure-apps/file-schema/runtime/throwunobservedtaskexceptions-element.md) dans un fichier de configuration de l'application pour activer le comportement [!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)] de lever une exception.  
  
 Vous pouvez également spécifier le comportement d'exception de l'une des manières suivantes :  
  
-   En définissant la variable d'environnement `COMPlus_ThrowUnobservedTaskExceptions` \(`set COMPlus_ThrowUnobservedTaskExceptions=1`\).  
  
-   En définissant la valeur DWORD ThrowUnobservedTaskExceptions de Registre \= 1 dans la clé d'HKEY\_LOCAL\_MACHINE\\SOFTWARE\\Microsoft\\.NETFramework.  
  
## Exemple  
 Le code exemple suivant illustre l'activation de lever des exceptions dans les tâches en utilisant un fichier de configuration de l'application.  
  
```  
<configuration>   
    <runtime>   
        <ThrowUnobservedTaskExceptions enabled="true"/>   
    </runtime>   
</configuration>  
  
```  
  
## Exemple  
 L'exemple suivant montre comment une exception inaperçue est levée depuis une tâche.  Le code doit être exécuté en tant que programme publié pour pouvoir fonctionner correctement.  
  
 [!code-csharp[ThrowUnobservedTaskExceptions#1](../../../../../samples/snippets/csharp/VS_Snippets_CLR/throwunobservedtaskexceptions/cs/program.cs#1)]
 [!code-vb[ThrowUnobservedTaskExceptions#1](../../../../../samples/snippets/visualbasic/VS_Snippets_CLR/throwunobservedtaskexceptions/vb/program.vb#1)]  
  
## Voir aussi  
 [Schéma des paramètres d'exécution](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)   
 [Schéma des fichiers de configuration](../../../../../docs/framework/configure-apps/file-schema/index.md)