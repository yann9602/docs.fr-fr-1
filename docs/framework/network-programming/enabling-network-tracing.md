---
title: "Activation du suivi réseau"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- trace destinations
- sending traces to log file
- trace listeners, network tracing
- network tracing, enabling
- CLR Debugger
- default listeners
- logs, trace
- destination for tracing output
ms.assetid: 5fff458c-51a6-4134-ba47-8a6137ddc41e
caps.latest.revision: 12
author: mcleblanc
ms.author: markl
manager: markl
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 15cee0244dc06f6eea03b333e01380953a616947
ms.contentlocale: fr-fr
ms.lasthandoff: 08/21/2017

---
# <a name="enabling-network-tracing"></a>Activation du suivi réseau
Le traçage réseau fournit l’accès aux informations sur les appels de méthodes et le trafic réseau généré par une application managée. Vous devez effectuer les tâches suivantes pour activer le traçage réseau dans votre application :  
  
-   Compiler votre code avec le traçage activé. Pour plus d’informations sur les commutateurs du compilateur nécessaires pour activer le traçage, consultez [Guide pratique pour effectuer une compilation conditionnelle avec Trace et Debug](../../../docs/framework/debug-trace-profile/how-to-compile-conditionally-with-trace-and-debug.md).  
  
-   Spécifier une destination de sortie de traçage.  
  
-   Configurer le comportement du traçage réseau. Pour obtenir des informations détaillées, consultez [Guide pratique pour configurer le traçage réseau](../../../docs/framework/network-programming/how-to-configure-network-tracing.md).  
  
 Les destinations de trace les plus courantes, également appelées écouteurs de suivi, sont l’écouteur par défaut et le fichier journal.  
  
 Le traçage utilise l’écouteur par défaut si vous ne spécifiez pas d’écouteur de suivi. Vous pouvez afficher les messages envoyés à l’écouteur par défaut en exécutant votre code dans un débogueur compatible avec le code managé tel que le débogueur CLR fourni avec le SDK .NET Framework ou DBwin32.exe fourni avec le SDK Windows. Avec le débogueur CLR, les messages de trace s’affichent dans la fenêtre **Sortie**.  
  
 Si vous préférez utiliser un fichier pour recevoir des traces, vous pouvez spécifier un fichier journal à l’aide des paramètres de configuration, comme indiqué dans l’exemple suivant. (Pour obtenir une présentation générale des fichiers de configuration, consultez [Fichiers de configuration](../../../docs/framework/configure-apps/index.md).)  
  
 Pour envoyer des traces vers un fichier journal, ajoutez le nœud suivant au nœud `<system.diagnostics>` du fichier de configuration approprié (application ou ordinateur). Vous pouvez modifier le nom du fichier (trace.log) en fonction de vos besoins.  
  
```xml  
<system.diagnostics>  
  <trace autoflush="true" indentsize="4">  
    <listeners>  
      <add name="file" type="System.Diagnostics.TextWriterTraceListener" initializeData="trace.log"/>  
    </listeners>   
  </trace>  
</system.diagnostics>  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Interprétation du traçage réseau](../../../docs/framework/network-programming/interpreting-network-tracing.md)   
 [Traçage réseau dans le .NET Framework](../../../docs/framework/network-programming/network-tracing.md)   
 [Introduction à l’instrumentation et au traçage](http://msdn.microsoft.com/en-us/e924e57c-33cf-4b0e-9e7f-a45d13e38f2c)

