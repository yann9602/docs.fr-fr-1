---
title: "Troubleshooting: Debugging Windows Services | Microsoft Docs"
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
  - "debugging Windows Service applications"
  - "debugging [Visual Studio], Windows services"
  - "troubleshooting service applications"
  - "services, troubleshooting"
  - "troubleshooting debugging, Windows Services"
  - "Windows Service applications, debugging"
  - "services, debugging"
  - "Windows Service applications, troubleshooting"
ms.assetid: cf859d4c-f04c-4cb7-81e3-bc7de8bea190
caps.latest.revision: 8
author: "ghogen"
ms.author: "ghogen"
manager: "douge"
caps.handback.revision: 8
---
# Troubleshooting: Debugging Windows Services
Lorsque vous déboguez une application de service Windows, votre service entre en interaction avec le **Gestionnaire de services Windows**.  Le **Gestionnaire de services** démarre votre service en appelant la méthode <xref:System.ServiceProcess.ServiceBase.OnStart%2A>, puis il attend trente secondes le retour de la méthode <xref:System.ServiceProcess.ServiceBase.OnStart%2A>.  Si passé ce délai la méthode n'a rien retourné, le Gestionnaire affiche un message d'erreur indiquant que le service ne peut pas être démarré.  
  
 Lorsque vous déboguez la méthode <xref:System.ServiceProcess.ServiceBase.OnStart%2A> comme décrit à la rubrique [How to: Debug Windows Service Applications](../../../docs/framework/windows-services/how-to-debug-windows-service-applications.md), vous devez tenir compte de ce délai d'attente de 30 secondes.  Si vous placez un point d'arrêt dans la méthode <xref:System.ServiceProcess.ServiceBase.OnStart%2A> et que vous ne le franchissez pas dans un délai de 30 secondes, le gestionnaire ne démarre pas le service.  
  
## Voir aussi  
 [How to: Debug Windows Service Applications](../../../docs/framework/windows-services/how-to-debug-windows-service-applications.md)   
 [Introduction to Windows Service Applications](../../../docs/framework/windows-services/introduction-to-windows-service-applications.md)