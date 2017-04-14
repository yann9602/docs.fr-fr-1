---
title: "JIT Tracing ETW Events | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "JIT tracing events [.NET Framework]"
  - "ETW, JIT tracing events (CLR)"
ms.assetid: 926adde2-c123-452e-bf4f-4b977bf06ffb
caps.latest.revision: 8
author: "mairaw"
ms.author: "mairaw"
manager: "wpickett"
caps.handback.revision: 8
---
# JIT Tracing ETW Events
<a name="top"></a> Ces événements collectent des informations sur la réussite ou l'échec de l'incorporation \(inlining\) juste\-à\-temps \(JIT\) et des appels tail JIT.  
  
 Les événements de traçage JIT se composent des deux catégories suivantes :  
  
-   [Événements d’incorporation \(inlining\) JIT](#jit_inlining_events)  
  
-   [Événements d'appel tail JIT](#jit_tail_call_events)  
  
<a name="jit_inlining_events"></a>   
## Événements d’incorporation \(inlining\) JIT  
  
### Événement MethodJitInliningFailed  
 Le tableau suivant montre les mots clés et les niveaux. \(Pour plus d'informations, consultez [CLR ETW Keywords and Levels](../../../docs/framework/performance/clr-etw-keywords-and-levels.md).\)  
  
|Mot clé pour déclencher l'événement|Niveau|  
|-----------------------------------------|------------|  
|`JITTracingKeyword` \(0x10\)|Détaillé \(5\)|  
  
 Le tableau ci\-dessous montre les informations liées aux événements.  
  
|Événement|ID d'événement|Moment du déclenchement|  
|---------------|--------------------|-----------------------------|  
|`MethodJitInliningFailed`|186|L’incorporation JIT a échoué.|  
  
 Le tableau ci\-dessous montre les données liées aux événements.  
  
|Nom du champ|Type de données|Description|  
|------------------|---------------------|-----------------|  
|MethodBeingCompiledNameSpace|win:UnicodeString|Espace de noms de la méthode en cours de compilation.|  
|MethodBeingCompiledName|win:UnicodeString|Nom de la méthode en cours de compilation.|  
|MethodBeingCompiledNameSignature|win:UnicodeString|Signature de la méthode en cours de compilation.|  
|InlinerNamespace|win:UnicodeString|Espace de noms de la méthode pour laquelle le compilateur JIT essaie de générer du code.|  
|InlinerName|win:UnicodeString|Nom de la méthode pour laquelle le compilateur essaie de générer du code. Ce n’est peut\-être pas le même que `MethodBeingCompiledName` si le compilateur essaie d'incorporer du code dans `MethodBeingCompiledName` au lieu de générer un appel à `InlinerName`.|  
|InlinerNameSignature|win:UnicodeString|Signature de l’incorporateur.|  
|InlineeNamespace|win:UnicodeString|Espace de noms de l’inlinee.|  
|InlineeName|win:UnicodeString|Méthode que le compilateur essaie d'incorporer \(ne pas générer d’appel vers cette méthode\).|  
|InlineeNameSignature|win:UnicodeString|Signature de l’inlinee.|  
|FailAlways|win:Boolean|Indication destinée au compilateur JIT signalant que l’incorporation \(inlining\) échouera toujours pour l’inlinee.|  
|FailReason|win:UnicodeString|INLINE\_NEVER signifie qu'une tentative d'incorporation \(inlining\) précédente a déterminé que l'incorporation ne réussirait jamais pour une autre raison ; sinon, texte de forme libre.|  
|ClrInstanceID|win:UnicodeString|ID unique de l'instance de CLR ou CoreCLR.|  
  
### Événement MethodJitInliningSucceeded  
 Le tableau suivant montre les mots clés et les niveaux.  
  
|Mot clé pour déclencher l'événement|Niveau|  
|-----------------------------------------|------------|  
|`JITTracingKeyword` \(0x10\)|Détaillé \(5\)|  
  
 Le tableau ci\-dessous montre les informations liées aux événements.  
  
|Événement|ID d'événement|Moment du déclenchement|  
|---------------|--------------------|-----------------------------|  
|`MethodJitInliningSucceeded`|185|L'incorporation de méthode a réussi.|  
  
 Le tableau ci\-dessous montre les données liées aux événements.  
  
|Nom du champ|Type de données|Description|  
|------------------|---------------------|-----------------|  
|MethodBeingCompiledNameSpace|win:UnicodeString|Espace de noms de la méthode en cours de compilation.|  
|MethodBeingCompiledName|win:UnicodeString|Nom de la méthode en cours de compilation.|  
|MethodBeingCompiledNameSignature|win:UnicodeString|Signature de la méthode en cours de compilation.|  
|InlinerNamespace|win:UnicodeString|Espace de noms de la méthode pour laquelle le compilateur JIT essaie de générer du code.|  
|InlinerName|win:UnicodeString|Nom de la méthode pour laquelle le compilateur essaie de générer du code. Ce n’est peut\-être pas le même que `MethodBeingCompiledName` si le compilateur essaie d'incorporer du code dans `MethodBeingCompiledName` au lieu de générer un appel à `InlinerName`.|  
|InlinerNameSignature|win:UnicodeString|Signature de l’incorporateur.|  
|InlineeNamespace|win:UnicodeString|Espace de noms de l’inlinee.|  
|InlineeName|win:UnicodeString|Méthode que le compilateur essaie d'incorporer \(ne pas générer d’appel vers cette méthode\).|  
|InlineeNameSignature|win:UnicodeString|Signature de l’inlinee.|  
|ClrInstanceID|win:UInt16|ID unique de l'instance de CLR ou CoreCLR.|  
  
 [Retour au début](#top)  
  
<a name="jit_tail_call_events"></a>   
## Événements d'appel tail JIT  
  
### Événement MethodJITTailCallFailed  
 Le tableau suivant montre les mots clés et les niveaux.  
  
|Mot clé pour déclencher l'événement|Niveau|  
|-----------------------------------------|------------|  
|`JITTracingKeyword` \(0x10\)|Détaillé \(5\)|  
  
 Le tableau ci\-dessous montre les informations liées aux événements.  
  
|Événement|ID d'événement|Moment du déclenchement|  
|---------------|--------------------|-----------------------------|  
|`MethodJitTailCallFailed`|189|L'appel tail de méthode a échoué.|  
  
 Le tableau ci\-dessous montre les données liées aux événements.  
  
|Nom du champ|Type de données|Description|  
|------------------|---------------------|-----------------|  
|MethodBeingCompiledNameSpace|win:UnicodeString|Espace de noms de la méthode en cours de compilation.|  
|MethodBeingCompiledName|win:UnicodeString|Nom de la méthode en cours de compilation.|  
|MethodBeingCompiledNameSignature|win:UnicodeString|Signature de la méthode en cours de compilation.|  
|CallerNamespace|win:UnicodeString|Espace de noms de la méthode pour laquelle le compilateur JIT essaie de générer du code.|  
|CallerName|win:UnicodeString|Nom de la méthode pour laquelle le compilateur essaie de générer du code.|  
|CallerNameSignature|win:UnicodeString|Signature de l’appelant.|  
|CalleeNamespace|win:UnicodeString|Espace de noms de l’appelé.|  
|CalleeName|win:UnicodeString|Méthode pour laquelle le compilateur essaie d'effectuer un appel tail \(ne pas générer d'appel vers cette méthode\).|  
|CalleeNameSignature|win:UnicodeString|Signature de l’appelé.|  
|TailPrefix|win:Boolean|Préfixe de l'appel tail.|  
|FailReason|win:UnicodeString|Raison pour laquelle l'appel tail a échoué.|  
|ClrInstanceID|win:UInt16|ID unique de l'instance de CLR ou CoreCLR.|  
  
### Événement MethodJITTailCallSucceeded  
 Le tableau suivant montre les mots clés et les niveaux.  
  
|Mot clé pour déclencher l'événement|Niveau|  
|-----------------------------------------|------------|  
|`JITTracingKeyword` \(0x10\)|Détaillé \(5\)|  
  
 Le tableau ci\-dessous montre les informations liées aux événements.  
  
|Événement|ID d'événement|Moment du déclenchement|  
|---------------|--------------------|-----------------------------|  
|`MethodJitTailCallSucceeded`|188|L'appel tail de méthode a réussi.|  
  
 Le tableau ci\-dessous montre les données liées aux événements.  
  
|Nom du champ|Type de données|Description|  
|------------------|---------------------|-----------------|  
|MethodBeingCompiledNameSpace|win:UnicodeString|Espace de noms de la méthode en cours de compilation.|  
|MethodBeingCompiledName|win:UnicodeString|Nom de la méthode en cours de compilation.|  
|MethodBeingCompiledNameSignature|win:UnicodeString|Signature de la méthode en cours de compilation.|  
|CallerNamespace|win:UnicodeString|Espace de noms de la méthode pour laquelle le compilateur JIT essaie de générer du code.|  
|CallerName|win:UnicodeString|Nom de la méthode pour laquelle le compilateur essaie de générer du code.|  
|CallerNameSignature|win:UnicodeString|Signature de l’appelant.|  
|CalleeNamespace|win:UnicodeString|Espace de noms de l’appelé.|  
|CalleeName|win:UnicodeString|Méthode pour laquelle le compilateur essaie d'effectuer un appel tail \(ne pas générer d'appel vers cette méthode\).|  
|CalleeNameSignature|win:UnicodeString|Signature de l’appelé.|  
|TailPrefix|win:Boolean|Préfixe de l’appel tail.|  
|TailCallType|win:UnicodeString|Type de l’appel tail.|  
|ClrInstanceID|win:UInt16|ID unique de l'instance de CLR ou CoreCLR.|  
  
## Voir aussi  
 [CLR ETW Events](../../../docs/framework/performance/clr-etw-events.md)