---
title: "&lt;system.serviceModel.activation&gt; | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: c0cae85f-56cb-4030-8807-6f96edff8d2d
caps.latest.revision: 9
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 9
---
# &lt;system.serviceModel.activation&gt;
Cette section de configuration représente les paramètres de configuration définis pour l'outil SMSvcHost.exe.  Les éléments de configuration peuvent être configurés dans le fichier SMSvcHost.exe.config.  Spécifiquement, cela inclut tous les paramètres à l'échelle de ordinateur qui doivent être configurés.  
  
## Exemple de fichier de configuration  
 Les éléments suivants constituent un exemple de fichier de configuration \(SMSvcHost.exe.config\), utilisé par le processus de l'écouteur SMSvcHost.exe.  
  
```  
<configuration>  
   <runtime>  
      <gcConcurrent enabled="false" />  
   </runtime>  
   <system.serviceModel.activation>  
       <net.tcp listenBacklog="10"  
          maxPendingAccepts="2"  
          maxPendingConnections="100"  
          receiveTimeout="00:00:10"  
          teredoEnabled="false">  
          <allowAccounts>  
             <!-- LocalSystem account -->  
             <add securityIdentifier="S-1-5-18"/>  
             <!-- LocalService account -->  
             <add securityIdentifier="S-1-5-19"/>  
             <!-- Network Service account -->  
            <add securityIdentifier="S-1-5-20"/>   
             <!-- Administrators account -->  
            <add securityIdentifier="S-1-5-32-544" />   
             <!-- IIS_IUSRS account (Vista only) -->  
             <add securityIdentifier="S-1-5-32-568"/>  
           </allowAccounts>  
       </net.tcp>  
       <net.pipe maxConnectionsPendingDispatch="100"  
          maxPendingAccepts="2"  
          receiveTimeout="00:00:10">  
          <allowAccounts>  
             <!-- LocalSystem account -->  
             <add securityIdentifier="S-1-5-18"/>  
             <!-- LocalService account -->  
             <add securityIdentifier="S-1-5-19"/>  
             <!-- Network Service account -->  
            <add securityIdentifier="S-1-5-20"/>   
             <!-- Administrators account -->  
            <add securityIdentifier="S-1-5-32-544" />   
             <!-- IIS_IUSRS account (Vista only) -->  
             <add securityIdentifier="S-1-5-32-568"/>  
           </allowAccounts>  
       </net.pipe>  
       <diagnostics performanceCountersEnabled="true" />  
   </system.serviceModel.activation>  
</configuration>  
```  
  
## Voir aussi  
 <xref:System.ServiceModel.Activation.Configuration>