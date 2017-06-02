---
title: "failedQI MDA | Microsoft Docs"
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
  - "failed QueryInterface"
  - "FailedQI MDA"
  - "QueryInterface call failures"
  - "MDAs (managed debugging assistants), failed QueryInterface"
  - "managed debugging assistants (MDAs), failed QueryInterface"
ms.assetid: 902dc863-34b3-477c-b433-b8a6bb6133c6
caps.latest.revision: 15
author: "mairaw"
ms.author: "mairaw"
manager: "wpickett"
caps.handback.revision: 15
---
# failedQI MDA
L'Assistant Débogage managé \(MDA\) `failedQI` est activé quand le runtime appelle `QueryInterface` sur un pointeur d'interface COM au nom d'un wrapper RCW et que l'appel à `QueryInterface` échoue.  
  
## Symptômes  
 Un cast sur un RCW échoue ou un appel à COM à partir d'un RCW échoue de manière inattendue.  
  
## Cause  
  
-   L'appel est effectué à partir du contexte incorrect.  
  
-   Le proxy inscrit fait échouer l'appel à `QueryInterface`, car la tentative d'appel a été effectuée dans le contexte incorrect.  
  
-   Un proxy détenu par OLE a retourné une erreur HRESULT.  
  
## Résolution  
 Consultez la documentation MSDN sur les règles COM.  
  
## Effet sur le runtime  
 Si un appel à `QueryInterface` échoue, le contexte est changé et une nouvelle tentative d'appel à `QueryInterface` est effectuée pour déterminer si un contexte incorrect était en cause.  
  
## Sortie  
 Nom managé de l'interface, GUID de l'interface et valeur HRESULT de l'échec.  
  
## Configuration  
  
```  
<mdaConfig>  
  <assistants>  
    <failedQI/>  
  </assistants>  
</mdaConfig>  
```  
  
## Voir aussi  
 <xref:System.Runtime.InteropServices.MarshalAsAttribute>   
 [Diagnosing Errors with Managed Debugging Assistants](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)   
 [Interop Marshaling](../../../docs/framework/interop/interop-marshaling.md)