---
title: "disconnectedContext MDA | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
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
  - "DisconnectedContext MDA"
  - "MDAs (managed debugging assistants), disconnected context"
  - "dead context"
  - "transitioning disconnected apartment or context"
  - "context disconnections"
  - "managed debugging assistants (MDAs), disconnected context"
ms.assetid: 1887d31d-7006-4491-93b3-68fd5b05f71d
caps.latest.revision: 14
author: "mairaw"
ms.author: "mairaw"
manager: "wpickett"
caps.handback.revision: 14
---
# disconnectedContext MDA
L'Assistant Débogage managé `disconnectedContext` est activé quand le CLR essaie d'effectuer une transition vers un contexte ou un cloisonnement déconnecté pendant le traitement d'une demande concernant un objet COM.  
  
## Symptômes  
 Les appels effectués sur un [Runtime Callable Wrapper](../../../docs/framework/interop/runtime-callable-wrapper.md) \(Runtime Callable Wrapper\) sont fournis au composant COM sous\-jacent dans le contexte ou cloisonnement actuel plutôt qu'à celui où ils se trouvent.  Cela peut entraîner une altération et\/ou une perte de données si le composant COM n'est pas multithread, comme dans le cas de composants de thread cloisonné.  Par ailleurs, si le wrapper RCW est lui\-même un proxy, l'appel peut se traduire par la levée d'une <xref:System.Runtime.InteropServices.COMException> avec un HRESULT de valeur RPC\_E\_WRONG\_THREAD.  
  
## Cause  
 Le contexte ou cloisonnement OLE a été arrêté au moment où le CLR a essayé d'effectuer une transition vers ce contexte ou cloisonnement.  En règle générale, cela se produit quand les threads cloisonnés sont arrêtés avant que tous les composants COM détenus par le cloisonnement ne soient complètement libérés. Cela peut être dû à un appel explicite à partir du code utilisateur sur un wrapper RCW ou à la manipulation du composant COM par le CLR lui\-même, par exemple quand le CLR libère le composant COM alors que le wrapper RCW associé a été récupéré par le Garbage Collector.  
  
## Solution  
 Pour éviter ce problème, assurez\-vous que le thread qui détient le thread cloisonné ne prend pas fin tant que l'application n'a pas terminé de traiter tous les objets qui se trouvent dans le cloisonnement.  Il en va de même pour les contextes ; assurez\-vous qu'un contexte n'est pas arrêté tant que l'application n'a pas complètement terminé de traiter tous les composants COM qui appartiennent à ce contexte.  
  
## Effet sur le runtime  
 Cet Assistant Débogage managé n'a aucun effet sur le CLR.  Il fournit uniquement des informations sur le contexte déconnecté.  
  
## Sortie  
 Indique le cookie de contexte du contexte ou du cloisonnement déconnecté.  
  
## Configuration  
  
```  
<mdaConfig>  
  <assistants>  
    <disconnectedContext />  
  </assistants>  
</mdaConfig>  
```  
  
## Voir aussi  
 <xref:System.Runtime.InteropServices.MarshalAsAttribute>   
 [Diagnosing Errors with Managed Debugging Assistants](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)   
 [Interop Marshaling](../../../docs/framework/interop/interop-marshaling.md)