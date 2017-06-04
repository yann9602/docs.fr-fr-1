---
title: "Troubleshooting: Service Application Won&#39;t Install | Microsoft Docs"
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
  - "troubleshooting service applications"
  - "services, troubleshooting"
  - "services, debugging"
  - "Windows NT services, troubleshooting"
  - "troubleshooting NT services"
  - "Windows Service applications, troubleshooting"
ms.assetid: 45c48e2e-b97d-44bc-8896-14f328e0ce33
caps.latest.revision: 8
author: "ghogen"
ms.author: "ghogen"
manager: "douge"
caps.handback.revision: 8
---
# Troubleshooting: Service Application Won&#39;t Install
Si votre application de service ne s'installe pas correctement, vérifiez que la valeur de la propriété <xref:System.ServiceProcess.ServiceBase.ServiceName%2A> de la classe de service est identique à celle qui est indiquée dans le programme d'installation de ce service.  Cette valeur doit être identique pour que votre service s'installe correctement.  
  
> [!NOTE]
>  Vous pouvez également consulter le journal d'installation pour obtenir des informations sur le déroulement du processus.  
  
 Vérifiez également qu'un autre service portant le même nom n'est pas déjà installé.  Pour que l'installation puisse normalement s'effectuer, le nom du service doit être unique.  
  
## Voir aussi  
 [Introduction to Windows Service Applications](../../../docs/framework/windows-services/introduction-to-windows-service-applications.md)