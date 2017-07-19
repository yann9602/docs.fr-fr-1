---
title: "CLR ETW Events | Microsoft Docs"
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
  - "CLR ETW events"
  - "ETW, common language runtime"
  - "ETW, CLR events"
ms.assetid: ef2b31c3-7426-43e7-9924-92339b96556d
caps.latest.revision: 45
author: "mairaw"
ms.author: "mairaw"
manager: "wpickett"
caps.handback.revision: 45
---
# CLR ETW Events
Les rubriques de cette section décrivent des événements de suivi d'événements pour Windows \(ETW\).  Chaque événement est associé à un mot clé et à un niveau décrits dans la rubrique [CLR ETW Keywords and Levels](../../../docs/framework/performance/clr-etw-keywords-and-levels.md).  Le CLR a deux fournisseurs pour les événements :  
  
-   Le fournisseur de runtime, qui déclenche des événements en fonction des mots clés \(catégories d'événements\) activés.  Le GUID du fournisseur de runtime du CLR est e13c0d23\-ccbc\-4e12\-931b\-d9cc2eee27e4.  
  
-   Le fournisseur d'arrêt, qui est utilisé dans certains cas bien précis.  Le GUID du fournisseur d'arrêt du CLR est a669021c\-c450\-4609\-a035\-5af59af4df18.  
  
 Pour plus d'informations sur les fournisseurs, consultez [CLR ETW Providers](../../../docs/framework/performance/clr-etw-providers.md).  
  
## Dans cette section  
 [Runtime Information Events](../../../docs/framework/performance/runtime-information-etw-events.md)  
 Capture des informations sur le runtime, notamment la référence, le numéro de version, le mode d'activation du runtime, les paramètres de ligne de commande avec lesquels il a été démarré, le GUID \(le cas échéant\) et d'autres informations pertinentes.  
  
 [Exception Thrown\_V1 Event](../../../docs/framework/performance/exception-thrown-v1-etw-event.md)  
 Capture des informations sur les exceptions levées.  
  
 [Contention Events](../../../docs/framework/performance/contention-etw-events.md)  
 Capture des informations sur les conflits de verrous du moniteur ou de verrous natifs utilisés par le runtime.  
  
 [Thread Pool Events](../../../docs/framework/performance/thread-pool-etw-events.md)  
 Capture des informations sur les pools de threads de travail et les pools de threads d'E\/S.  
  
 [Loader Events](../../../docs/framework/performance/loader-etw-events.md)  
 Capture des informations sur le chargement et le déchargement des domaines d'application, des assemblys et des modules.  
  
 [Method Events](../../../docs/framework/performance/method-etw-events.md)  
 Capture des informations sur les méthodes CLR pour la résolution des symboles.  
  
 [Garbage Collection Events](../../../docs/framework/performance/garbage-collection-etw-events.md)  
 Capture des informations concernant le garbage collection pour faciliter le diagnostic et le débogage.  
  
 [JIT Tracing Events](../../../docs/framework/performance/jit-tracing-etw-events.md)  
 Capture des informations sur l'incorporation \(inlining\) juste\-à\-temps \(JIT\) et les appels tail JIT.  
  
 [Interop Events](../../../docs/framework/performance/interop-etw-events.md)  
 Capture des informations sur la mise en cache et la génération du stub MSIL \(Microsoft Intermediate Language\).  
  
 [ARM Events](../../../docs/framework/performance/application-domain-resource-monitoring-arm-etw-events.md)  
 Capture des informations de diagnostic détaillées sur l'état d'un domaine d'application.  
  
 [Security Events](../../../docs/framework/performance/security-etw-events.md)  
 Capture des informations sur la vérification de nom fort et la vérification Authenticode.  
  
 [Stack Event](../../../docs/framework/performance/stack-etw-event.md)  
 Capture des informations utilisées avec d'autres événements pour générer des traces de pile après le déclenchement d'un événement.  
  
## Voir aussi  
 [Améliorer le débogage et le réglage des performances avec ETW](http://go.microsoft.com/fwlink/?LinkId=179696)   
 [Blog de performances Windows](http://go.microsoft.com/fwlink/?LinkId=179509)   
 [Controlling .NET Framework Logging](../../../docs/framework/performance/controlling-logging.md)   
 [CLR ETW Providers](../../../docs/framework/performance/clr-etw-providers.md)   
 [CLR ETW Keywords and Levels](../../../docs/framework/performance/clr-etw-keywords-and-levels.md)   
 [ETW Events in the Common Language Runtime](../../../docs/framework/performance/etw-events-in-the-common-language-runtime.md)