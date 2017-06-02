---
title: "Runtime Information ETW Events | Microsoft Docs"
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
  - "runtime information events [.NET Framework]"
  - "ETW, runtime information events"
ms.assetid: 68b4edbc-7f3b-45f6-ab75-4fd066d6af9a
caps.latest.revision: 6
author: "mairaw"
ms.author: "mairaw"
manager: "wpickett"
caps.handback.revision: 6
---
# Runtime Information ETW Events
Ces événements ETW journalisent des informations sur le runtime, notamment la référence, le numéro de version, le mode d'activation du runtime, les paramètres de ligne de commande avec lesquels il a été démarré, le GUID \(le cas échéant\) et d'autres informations pertinentes.  Si plusieurs runtimes sont exécutés dans un processus, les informations fournies par ces événements \(ClrInstanceID\) permettent de les distinguer.  
  
 Le tableau suivant répertorie les deux événements d'informations sur les runtimes.  Les événements peuvent être déclenchés sous n'importe quel mot clé ou masque. \(Pour plus d'informations, consultez [CLR ETW Keywords and Levels](../../../docs/framework/performance/clr-etw-keywords-and-levels.md).\)  
  
|Événement|ID d'événement|Fournisseur|Description|  
|---------------|--------------------|-----------------|-----------------|  
|`RuntimeInformationEvent`|187|CLRRuntime|Déclenché lorsqu'un runtime est chargé.|  
|`RuntimeInformationDCStart`|187|CLRRundown|Énumère les runtimes chargés.|  
  
 Le tableau suivant répertorie les données d'événement.  
  
|Nom du champ|Type de données|Description|  
|------------------|---------------------|-----------------|  
|ClrInstanceID|win:UInt16|ID unique pour l'instance de CLR ou CoreCLR.|  
|Sku|win:UInt16|1 – CLR de bureau.<br /><br /> 2 – CoreCLR.|  
|BclVersion – Version principale|win:UInt16|Version principale de mscorlib.dll.|  
|BclVersion – Version secondaire|win:UInt16|Numéro de version secondaire de mscorlib.dll.|  
|BclVersion – Numéro de build|win:UInt16|Numéro de build de mscorlib.dll.|  
|BclVersion – QFE|win:UInt16|Numéro de version de correctif de mscorlib.dll.|  
|VMVersion – Version principale|win:UInt16|Version de clr.dll ou coreclr.dll, en fonction de SKU.|  
|VMVersion – Version secondaire|win:UInt16|Version secondaire de clr.dll ou coreclr.dll, en fonction de SKU.|  
|VMVersion – Numéro de build|win:UInt16|Numéro de build de clr.dll ou coreclr.dll.|  
|VMVersion – QFE|win:UInt16|Numéro de version de correctif de clr.dll ou coreclr.dll.|  
|StartupFlags|win:UInt32|Indicateurs de démarrage définis dans mscoree.h.|  
|StartupMode|win:UInt8|0x01 \- Exécutable managé.<br /><br /> 0x02 \- CLR hébergé.<br /><br /> 0x04 \- Interopérabilité managée C\+\+.<br /><br /> 0x08 \- Activé pour COM.<br /><br /> 0x10 \- Autre.|  
|CommandLine|win:UnicodeString|Non Null uniquement si StartupMode\=0x01.|  
|ComObjectGUID|win:GUID|Non Null uniquement si StartupMode\=0x08.|  
|RuntimeDLLPath|win:UnicodeString|Chemin d'accès au fichier .dll du CLR chargé dans le processus.|  
  
## Voir aussi  
 [CLR ETW Events](../../../docs/framework/performance/clr-etw-events.md)