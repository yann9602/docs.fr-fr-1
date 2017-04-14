---
title: "Att&#233;nuation&#160;: appels de la m&#233;thode EventSource.WriteEvent | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 327a9fdb-ba8e-40f7-89e5-4c89b46e594f
caps.latest.revision: 6
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 6
---
# Att&#233;nuation&#160;: appels de la m&#233;thode EventSource.WriteEvent
[!INCLUDE[net_v451](../../../includes/net-v451-md.md)] impose un contrat entre une méthode d'événement ETW dans une classe dérivée de <xref:System.Diagnostics.Tracing.EventSource?displayProperty=fullName> et la méthode <xref:System.Diagnostics.Tracing.EventSource.WriteEvent%2A> de sa classe de base. La méthode d'événement ETW doit passer à la méthode <xref:System.Diagnostics.Tracing.EventSource.WriteEvent%2A> l'ID d'événement suivi des mêmes arguments que ceux passés à la méthode d'événement.  
  
## Impact  
 Une méthode d'événement ETW définie de la façon suivante rompt le contrat :  
  
```  
  
[Event(2, Level = EventLevel.Informational)] public void Info2(string message) { base.WriteEvent(2, message, "-"); }  
  
```  
  
 Lorsque ce contrat est violé, une exception <xref:System.IndexOutOfRangeException> est levée au moment de l'exécution si un objet <xref:System.Diagnostics.Tracing.EventListener> lit les données <xref:System.Diagnostics.Tracing.EventSource> dans le processus.  
  
 La définition de cette méthode d'événement ETW doit suivre le modèle suivant :  
  
```  
  
[Event(2, Level = EventLevel.Informational)] public void Info2(string message) { base.WriteEvent(2, message); }  
  
```  
  
## Atténuation  
 Vous devez modifier le code existant pour respecter le modèle requis.  
  
 Vous pouvez réduire la quantité de code à modifier en définissant deux méthodes pour appeler la méthode <xref:System.Diagnostics.Tracing.EventSource.WriteEvent%2A>, comme suit :  
  
```  
  
[NonEvent] public void Info2(string message) { Info2Internal(message, "-"); } public void Info2Internal(string message, string prefix) { WriteEvent(2, message, prefix); }  
  
```  
  
## Voir aussi  
 [Modifications du runtime](../../../docs/framework/migration-guide/runtime-changes-in-the-net-framework-4-5-1.md)