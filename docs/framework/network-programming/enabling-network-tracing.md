---
title: "Activation du suivi r&#233;seau | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "destinations de suivi"
  - "envoi de suivis à un fichier journal"
  - "écouteurs de suivi, suivi réseau"
  - "suivi réseau, activation"
  - "Débogueur CLR"
  - "écouteurs par défaut"
  - "journaux, suivi"
  - "destination de sortie de suivi"
ms.assetid: 5fff458c-51a6-4134-ba47-8a6137ddc41e
caps.latest.revision: 12
author: "mcleblanc"
ms.author: "markl"
manager: "markl"
caps.handback.revision: 12
---
# Activation du suivi r&#233;seau
Le traçage réseau fournit l'accès aux données sur les appels de méthode et le trafic réseau généré par une application managée.  Vous devez effectuer les tâches suivantes pour activer le traçage réseau dans votre application :  
  
-   Compilez votre code avec le traçage est activé.  Consultez [How to: Compile Conditionally with Trace and Debug](../../../docs/framework/debug-trace-profile/how-to-compile-conditionally-with-trace-and-debug.md) pour plus d'informations sur les commutateurs de compilation requis pour activer le traçage.  
  
-   Spécifiez une destination pour la sortie de traçage.  
  
-   Configurez le comportement du traçage réseau.  Consultez [Comment : Configurez le traçage réseau](../../../docs/framework/network-programming/how-to-configure-network-tracing.md) pour des informations détaillées.  
  
 Des destinations de traçage les plus courantes, également appelées écouteurs de la trace, sont l'écouteur par défaut et le fichier journal.  
  
 Le utilise l'écouteur par défaut si vous ne spécifiez pas un écouteur de la trace.  Vous pouvez afficher les messages envoyés à l'écouteur par défaut en exécutant le code dans un débogueur de code managé activé tel que le débogueur CLR fourni avec le kit de développement. NET Framework SDK, ou DBwin32.exe fourni avec le Kit de développement logiciel.  Avec le débogueur CLR, les messages de trace apparaissent dans la fenêtre de **Sortie** .  
  
 Si vous préférez utiliser un fichier pour recevoir des traces, vous pouvez spécifier un fichier journal à l'aide de les paramètres de configuration, comme indiqué dans l'exemple suivant.  \(Pour une discussion généralement des fichiers de configuration, consultez [fichiers de configuration](../../../docs/framework/configure-apps/index.md).\)  
  
 Pour envoyer des traces à un fichier journal, ajoutez le nœud suivant au nœud d' `<system.diagnostics>` du fichier de configuration approprié \(application ou l'ordinateur\).  Vous pouvez modifier le nom du fichier \(trace.log\) selon vos besoins.  
  
```  
<system.diagnostics>  
  <trace autoflush="true" indentsize="4">  
    <listeners>  
      <add name="file" type="System.Diagnostics.TextWriterTraceListener" initializeData="trace.log"/>  
    </listeners>   
  </trace>  
</system.diagnostics>  
```  
  
## Voir aussi  
 [Interprétation du traçage réseau](../../../docs/framework/network-programming/interpreting-network-tracing.md)   
 [Traçage réseau dans le .NET Framework](../../../docs/framework/network-programming/network-tracing.md)   
 [Introduction to Instrumentation and Tracing](http://msdn.microsoft.com/fr-fr/e924e57c-33cf-4b0e-9e7f-a45d13e38f2c)