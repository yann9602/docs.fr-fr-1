---
title: "&lt;runtime&gt;, &#233;l&#233;ment | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "http://schemas.microsoft.com/.NetConfiguration/v2.0#runtime"
  - "http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/runtime"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "<runtime> (élément)"
  - "balises conteneurs, <runtime> (élément)"
  - "runtime (élément)"
ms.assetid: 1eb2fae3-de4b-45b6-852f-517c39b751bd
caps.latest.revision: 70
author: "mcleblanc"
ms.author: "markl"
manager: "markl"
caps.handback.revision: 62
---
# &lt;runtime&gt;, &#233;l&#233;ment
Contient des informations sur les liaisons d'assembly et l'opération garbage collection.  
  
## Syntaxe  
  
```  
<runtime>  
</runtime>  
```  
  
## Attributs et éléments  
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### Attributs  
 Aucun.  
  
### Éléments enfants  
  
|Élément|Description|  
|-------------|-----------------|  
|[\<alwaysFlowImpersonationPolicy\>](../../../../../docs/framework/configure-apps/file-schema/runtime/alwaysflowimpersonationpolicy-element.md)|Spécifie que l'identité Windows est toujours transmise entre des points asynchrones, indépendamment du mode d'exécution de l'emprunt d'identité.|  
|[\<appDomainManagerAssembly\>](../../../../../docs/framework/configure-apps/file-schema/runtime/appdomainmanagerassembly-element.md)|Spécifie l'assembly qui fournit le gestionnaire de domaine d'application pour le domaine d'application par défaut dans le processus.|  
|[\<appDomainManagerType\>](../../../../../docs/framework/configure-apps/file-schema/runtime/appdomainmanagertype-element.md)|Spécifie le type qui sert de gestionnaire de domaine d'application pour le domaine d'application par défaut.|  
|[\<appDomainResourceMonitoring\>](../../../../../docs/framework/configure-apps/file-schema/runtime/appdomainresourcemonitoring-element.md)|Indique au runtime de collecter des statistiques sur tous les domaines d'application du processus pendant la durée de vie du processus.|  
|[\<assemblyBinding\>](../../../../../docs/framework/configure-apps/file-schema/runtime/assemblybinding-element-for-runtime.md)|Contient des informations sur la redirection des versions des assemblys et sur l'emplacement de ces derniers.|  
|[\<bypassTrustedAppStrongNames\>](../../../../../docs/framework/configure-apps/file-schema/runtime/bypasstrustedappstrongnames-element.md)|Spécifie si la vérification de nom fort pour les assemblys fiables doit être ignorée.|  
|[\<CompatSortNLSVersion\>](../../../../../docs/framework/configure-apps/file-schema/runtime/compatsortnlsversion-element.md)|Spécifie que le runtime doit utiliser le comportement de tri hérité lors de l'exécution de comparaisons de chaînes.|  
|[\<developmentMode\>](../../../../../docs/framework/configure-apps/file-schema/runtime/developmentmode-element.md)|Spécifie si le runtime recherche les assemblys dans les répertoires spécifiés par la variable d'environnement DEVPATH.|  
|[\<disableCachingBindingFailures\>](../../../../../docs/framework/configure-apps/file-schema/runtime/disablecachingbindingfailures-element.md)|Spécifie si la mise en cache des échecs de liaison, qui est le comportement par défaut dans la version 2.0 du .NET Framework, est désactivée.|  
|[\<disableCommitThreadStack\>](../../../../../docs/framework/configure-apps/file-schema/runtime/disablecommitthreadstack-element.md)|Spécifie si la pile des threads complète est validée lorsqu'un thread est démarré.|  
|[\<disableFusionUpdatesFromADManager\>](../../../../../docs/framework/configure-apps/file-schema/runtime/disablefusionupdatesfromadmanager-element.md)|Spécifie si le comportement par défaut, qui consiste à autoriser l'hôte du runtime à substituer les paramètres de configuration pour un domaine d'application, est désactivé.|  
|[\<enforceFIPSPolicy\>](../../../../../docs/framework/configure-apps/file-schema/runtime/enforcefipspolicy-element.md)|Spécifie s'il faut appliquer une condition de configuration de l'ordinateur que les algorithmes de chiffrement doivent être conformes aux normes FIPS \(Federal Information Processing Standards\).|  
|[\<etwEnable\>](../../../../../docs/framework/configure-apps/file-schema/runtime/etwenable-element.md)|Spécifie s'il convient d'activer le traçage d'événements pour Windows \(ETW\) pour les événements Common Language Runtime.|  
|[\<forcePerformanceCounterUniqueSharedMemoryReads\>](../../../../../docs/framework/configure-apps/file-schema/runtime/forceperformancecounteruniquesharedmemoryreads-element.md)|Spécifie si PerfCounter.dll utilise le paramètre du Registre CategoryOptions dans une application .NET Framework version 1.1 pour déterminer s'il faut charger des données de compteur de performance à partir de la mémoire partagée spécifique à la catégorie ou de la mémoire globale.|  
|[\<gcAllowVeryLargeObjects\>](../../../../../docs/framework/configure-apps/file-schema/runtime/gcallowverylargeobjects-element.md)|Sur les plateformes 64 bits, active les tableaux supérieurs à 2 gigaoctets \(GB\) en taille totale.|  
|[\<gcConcurrent\>](../../../../../docs/framework/configure-apps/file-schema/runtime/gcconcurrent-element.md)|Spécifie si le Common Language Runtime exécute l'opération garbage collection simultanément.|  
|[\<GCCpuGroup\>](../../../../../docs/framework/configure-apps/file-schema/runtime/gccpugroup-element.md)|Spécifie si le garbage collection prend en charge des groupes d'UC multiples.|  
|[\<gcServer\>](../../../../../docs/framework/configure-apps/file-schema/runtime/gcserver-element.md)|Spécifie si le Common Language Runtime exécute le garbage collection côté serveur.|  
|[\<generatePublisherEvidence\>](../../../../../docs/framework/configure-apps/file-schema/runtime/generatepublisherevidence-element.md)|Spécifie si le runtime utilise la stratégie de sécurité d'accès du code \(CAS, Code Access Security\).|  
|[\<legacyCorruptedStateExceptionsPolicy\>](../../../../../docs/framework/configure-apps/file-schema/runtime/legacycorruptedstateexceptionspolicy-element.md)|Spécifie si le runtime permet au code managé d'intercepter les violations d'accès et d'autres exceptions d'état endommagé.|  
|[\<legacyImpersonationPolicy\>](../../../../../docs/framework/configure-apps/file-schema/runtime/legacyimpersonationpolicy-element.md)|Spécifie que l'identité Windows n'est pas transmise entre des points asynchrones, quels que soient les paramètres de flux du contexte d'exécution sur le thread actif.|  
|[\<loadFromRemoteSources\>](../../../../../docs/framework/configure-apps/file-schema/runtime/loadfromremotesources-element.md)|Spécifie si les assemblys provenant de sources distantes sont chargés avec une confiance totale.|  
|[\<NetFx40\_LegacySecurityPolicy\>](../../../../../docs/framework/configure-apps/file-schema/runtime/netfx40-legacysecuritypolicy-element.md)|Spécifie si le runtime utilise la stratégie de sécurité d'accès du code héritée \(legacy\) \(CAS, Code Access Security\).|  
|[\<NetFx40\_PInvokeStackResilience\>](../../../../../docs/framework/configure-apps/file-schema/runtime/netfx40-pinvokestackresilience-element.md)|Spécifie si le runtime résout automatiquement les déclarations d'appel de code non managé au moment de l'exécution, au prix de transitions plus lentes entre le code managé et non managé.|  
|[\<NetFx45\_CultureAwareComparerGetHashCode\_LongStringst\>](../../../../../docs/framework/configure-apps/file-schema/runtime/netfx45-cultureawarecomparergethashcode-longstrings-element.md)|Spécifie si le runtime utilise une quantité fixe de mémoire pour le code de hachage pour la méthode <xref:System.StringComparer.GetHashCode%2A?displayProperty=fullName>.|  
|[\<PreferComInsteadOfRemoting\>](../../../../../docs/framework/configure-apps/file-schema/runtime/prefercominsteadofmanagedremoting-element.md)|Indique que le runtime va utiliser COM Interop au lieu de la communication à distance au\-delà des limites du domaine d'application.|  
|[\<relativeBindForResources\>](../../../../../docs/framework/configure-apps/file-schema/runtime/relativebindforresources-element.md)|Optimise le test des assemblys satellites.|  
|[\<shadowCopyVerifyByTimeStamp\>](../../../../../docs/framework/configure-apps/file-schema/runtime/shadowcopyverifybytimestamp-element.md)|Spécifie si les clichés instantanés utilisent le comportement au démarrage par défaut introduit par le [!INCLUDE[net_v40_long](../../../../../includes/net-v40-long-md.md)] ou rétablissent le comportement au démarrage des versions antérieures du .NET Framework.|  
|[\<supportPortability\>](../../../../../docs/framework/configure-apps/file-schema/runtime/supportportability-element.md)|Spécifie qu'une application peut référencer le même assembly dans deux implémentations différentes du .NET Framework en désactivant le comportement par défaut qui considère les assemblys comme équivalents à des fins de portabilité de l'application.|  
|[\<system.runtime.caching\>](../../../../../docs/framework/configure-apps/file-schema/runtime/system-runtime-caching-element-cache-settings.md)|Fournit des informations de configuration pour le cache d'objets en mémoire par défaut.|  
|[\<Thread\_UseAllCpuGroups\>](../../../../../docs/framework/configure-apps/file-schema/runtime/thread-useallcpugroups-element.md)|Spécifie si le runtime distribue des threads managés dans tous les groupes d'UC.|  
|[\<ThrowUnobservedTaskException\>](../../../../../docs/framework/configure-apps/file-schema/runtime/throwunobservedtaskexceptions-element.md)|Spécifie si les exceptions non gérées de tâche doivent arrêter un processus en cours de exécution.|  
|[\<TimeSpan\_LegacyFormatMode\>](../../../../../docs/framework/configure-apps/file-schema/runtime/runtime-element.md)|Spécifie si l'exécution utilise la mise en forme héritée pour les valeurs <xref:System.TimeSpan>.|  
|[\<UseRandomizedStringHashAlgorithm\>](../../../../../docs/framework/configure-apps/file-schema/runtime/userandomizedstringhashalgorithm-element.md)|Spécifie si les codes de hachage pour les chaînes sont calculés par le Runtime pour le domaine d'application.|  
|[\<UseSmallInternalThreadStacks\>](../../../../../docs/framework/configure-apps/file-schema/runtime/usesmallinternalthreadstacks-element.md)|Demande que le runtime utilise des tailles de piles explicites lorsqu'il crée certains threads qu'il utilise en interne, au lieu de la taille de pile par défaut.|  
  
### Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|`configuration`|Élément racine de chaque fichier de configuration utilisé par le Common Language Runtime et les applications .NET Framework.|  
  
## Notes  
 Dans la version 2.0 du .NET Framework, l'identité empruntée est transmise entre des points asynchrones dans un domaine d'application.  Dans la version 2.0 du .NET Framework, vous pouvez activer ou désactiver la transmission de l'emprunt d'identité entre des points asynchrones en configurant correctement l'élément runtime dans le fichier machine.config ou dans le fichier de configuration de l'application.  Pour ASP.NET, la transmission de l'emprunt d'identité peut être configurée dans le fichier aspnet.config du répertoire \<Dossier Windows\>\\Microsoft.NET\\Framework\\vx.x.xxxx.  
  
 Par défaut, ASP.NET désactive la transmission de l'emprunt d'identité dans le fichier aspnet.config à l'aide des paramètres de configuration suivants :  
  
```  
configuration>  
   <runtime>  
      <legacyImpersonationPolicy enabled="true"/>  
      <alwaysFlowImpersonationPolicy enabled="false"/>  
   </runtime>  
</configuration>  
```  
  
 Dans ASP.NET, si vous souhaitez plutôt autoriser la transmission de l'emprunt d'identité, vous devez explicitement utiliser les paramètres de configuration suivants :  
  
```  
<configuration>  
   <runtime>  
      <legacyImpersonationPolicy enabled="false"/>  
      <alwaysFlowImpersonationPolicy enabled="true"/>  
   </runtime>  
</configuration>  
```  
  
 Pour plus d’informations, consultez [\<legacyImpersonationPolicy\>, élément](../../../../../docs/framework/configure-apps/file-schema/runtime/legacyimpersonationpolicy-element.md) et [\<alwaysFlowImpersonationPolicy\>, élément](../../../../../docs/framework/configure-apps/file-schema/runtime/alwaysflowimpersonationpolicy-element.md).  
  
## Exemple  
 L'exemple suivant montre comment rediriger une version d'assembly vers une autre.  
  
```  
<configuration>  
   <runtime>  
      <assemblyBinding xmlns="urn:schemas-microsoft-com:asm.v1">  
         <dependentAssembly>  
            <assemblyIdentity name="myAssembly"  
                              publicKeyToken="32ab4ba45e0a69a1"  
                              culture="neutral" />  
             <bindingRedirect oldVersion="1.0.0.0"  
                              newVersion="2.0.0.0"/>  
         </dependentAssembly>  
      </assemblyBinding>  
   </runtime>  
</configuration>  
```  
  
## Voir aussi  
 [Schéma des paramètres d'exécution](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)   
 [Schéma des fichiers de configuration](../../../../../docs/framework/configure-apps/file-schema/index.md)   
 [Redirection des versions d'assemblys](../../../../../docs/framework/configure-apps/redirect-assembly-versions.md)   
 [How to: Disable Concurrent Garbage Collection](http://msdn.microsoft.com/fr-fr/ba2c6c67-5778-497c-9fac-5f793b5500c7)