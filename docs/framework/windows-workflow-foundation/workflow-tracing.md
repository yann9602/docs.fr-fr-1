---
title: "Suivi de workflow | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 18737989-0502-4367-b5f6-617ebfb77c96
caps.latest.revision: 12
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 12
---
# Suivi de workflow
Le suivi de workflow offre une méthode de capture des informations de diagnostic à l'aide d'écouteurs de suivi .NET Framework.Le suivi peut être activé si un problème a été détecté dans l'application, puis désactivé de nouveau une fois le problème résolu.Deux méthodes s'offrent à vous pour activer le suivi de débogage pour les flux de travail.Vous pouvez le configurer à l'aide de la visionneuse de suivi d'événements ou bien utiliser l'objet <xref:System.Diagnostics> pour envoyer des événements de suivi à un fichier.  
  
## Activation du suivi de débogage dans ETW  
 Pour activer le suivi à l'aide d'ETW, activez le canal de débogage dans l'Observateur d'événements :  
  
1.  Dans l'Observateur d'événements, naviguez vers le nœud des journaux d'analyse et de débogage.  
  
2.  Dans l'arborescence de l'Observateur d'événements, naviguez vers **Observateur d'événements\-\>Journaux des applications et des services\-\>Microsoft\-\>Windows\-\>Serveur d'applications\-Applications**.Cliquez avec le bouton droit sur **Serveur d'applications\-Applications** et sélectionnez **Afficher\-\>Afficher les journaux d'analyse et de débogage**.Cliquez avec le bouton droit sur **Débogage** et sélectionnez **Activer le journal**.  
  
3.  Lorsqu'un flux de travail exécute le débogage et qu'un suivi est émis vers le canal de débogage ETW, le suivi peut être affiché dans l'Observateur d'événements.Naviguez vers **Observateur d'événements\-\>Journaux des applications et des services\-\>Microsoft\-\>Windows\-\>Serveur d'applications\-Applications**.Cliquez avec le bouton droit sur **Débogage** et sélectionnez **Actualiser**.  
  
4.  La taille de la mémoire tampon de trace analytique par défaut est de 4 kilo\-octet \(Ko\) seulement. Il est recommandé d'augmenter la taille à 32 Ko.Pour ce faire, effectuez les étapes suivantes.  
  
    1.  Exécutez la commande suivante dans le répertoire de l'infrastructure actuelle \(par exemple, C:\\Windows\\Microsoft.NET\\Framework\\v4.0.21203\) : `wevtutil um Microsoft.Windows.ApplicationServer.Applications.man`  
  
    2.  Remplacez la valeur \<bufferSize\> du fichier Windows.ApplicationServer.Applications.man par 32.  
  
        ```  
        <channel name="Microsoft-Windows-Application Server-Applications/Analytic" chid="ANALYTIC_CHANNEL" symbol="ANALYTIC_CHANNEL" type="Analytic" enabled="false" isolation="Application" message="$(string.MICROSOFT_WINDOWS_APPLICATIONSERVER_APPLICATIONS.channel.ANALYTIC_CHANNEL.message)" >  
                    <publishing>  
                      <bufferSize>32</bufferSize>  
                    </publishing>  
                  </channel>  
  
        ```  
  
    3.  Exécutez la commande suivante dans le répertoire de l'infrastructure actuelle \(par exemple, C:\\Windows\\Microsoft.NET\\Framework\\v4.0.21203\) : `wevtutil im Microsoft.Windows.ApplicationServer.Applications.man`  
  
> [!NOTE]
>  Si vous utilisez .NET Framework 4 Client Profile, vous devez d'abord enregistrer le manifeste ETW en exécutant la commande suivante à partir du répertoire du .NET Framework 4 : `ServiceModelReg.exe –i –c:etw`  
  
## Activation du suivi de débogage à l'aide de System.Diagnostics  
 Ces écouteurs peuvent être configurés dans le fichier App.config de l'application de workflow ou le fichier Web.config pour un service de workflow.Dans cet exemple, un [TextWriterTraceListener](http://go.microsoft.com/fwlink/?LinkId=165424) \(en anglais\) est configuré pour enregistrer les informations de traçage dans le fichier MyTraceLog.txt du répertoire actif.  
  
```  
<configuration>  
  <system.diagnostics>  
    <sources>  
      <source name="System.Activities" switchValue="Information">  
        <listeners>  
          <add name="textListener" />  
          <remove name="Default" />  
        </listeners>  
      </source>  
    </sources>  
    <sharedListeners>  
      <add name="textListener"  
           type="System.Diagnostics.TextWriterTraceListener"  
           initializeData="MyTraceLog.txt"  
           traceOutputOptions="ProcessId, DateTime" />  
    </sharedListeners>  
    <trace autoflush="true" indentsize="4">  
      <listeners>  
        <add name="textListener" />  
      </listeners>  
    </trace>  
  </system.diagnostics>  
</configuration>  
```  
  
## Voir aussi  
 [Analyse Windows Server AppFabric](http://go.microsoft.com/fwlink/?LinkId=201273)   
 [Analyse d'applications avec AppFabric](http://go.microsoft.com/fwlink/?LinkId=201275)