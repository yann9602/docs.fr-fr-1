---
title: "Developing Windows Service Applications | Microsoft Docs"
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
  - "ServiceInstaller class, Windows Service applications"
  - "Service class, Windows Service applications"
  - "Windows Service applications"
  - "Windows NT services"
  - "ServiceProcessInstaller class, Windows Service applications"
  - "services"
  - ".NET applications, Windows applications"
ms.assetid: ba72d648-9553-4849-b829-069ad5ea014b
caps.latest.revision: 18
author: "ghogen"
ms.author: "ghogen"
manager: "douge"
caps.handback.revision: 18
---
# Developing Windows Service Applications
[!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] et le Kit de développement Microsoft [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] SDK vous permettent de créer facilement une application installée en tant que service.  Les applications de ce type sont appelées des « services Windows ».  Les fonctionnalités de Microsoft .NET Framework vous permettent de créer des services, de les installer, de les démarrer, de les arrêter et de contrôler à chaque instant leur comportement.  
  
> [!WARNING]
>  Le modèle de service windows pour C\+\+ n'a pas été inclus dans Visual Studio 2010.  Pour créer un service windows, vous pouvez créer un service en code managé dans visual C\# ou Visual Basic, qui peut interagir avec le code C\+\+ existant si nécessaire, vous pouvez créer un service windows en C\+\+ natif à l'aide de [Assistant Projet ATL](../Topic/ATL%20Project%20Wizard.md).  
  
## Dans cette section  
 [Introduction to Windows Service Applications](../../../docs/framework/windows-services/introduction-to-windows-service-applications.md)  
 Fournit une vue d'ensemble des applications de service windows, la durée de vie d'un service, et comment les applications de service diffèrent des autres types de projet commun.  
  
 [Walkthrough: Creating a Windows Service Application in the Component Designer](../../../docs/framework/windows-services/walkthrough-creating-a-windows-service-application-in-the-component-designer.md)  
 Présente un exemple illustrant la création d'un service en [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)] et en Visual C\#.  
  
 [Service Application Programming Architecture](../../../docs/framework/windows-services/service-application-programming-architecture.md)  
 Présente les éléments de langage intervenant dans la programmation des services.  
  
 [How to: Create Windows Services](../../../docs/framework/windows-services/how-to-create-windows-services.md)  
 Décrit le processus de création et de configurer des services windows à l'aide de le modèle de projet de service windows.  
  
## Rubriques connexes  
 <xref:System.ServiceProcess.ServiceBase>  
 Présente les principales fonctionnalités de la classe <xref:System.ServiceProcess.ServiceBase>, utilisée pour créer des services.  
  
 <xref:System.ServiceProcess.ServiceProcessInstaller>  
 Décrit les fonctionnalités de la classe <xref:System.ServiceProcess.ServiceProcessInstaller>, qui est utilisée parallèlement à la classe <xref:System.ServiceProcess.ServiceInstaller> pour installer et désinstaller vos services.  
  
 <xref:System.ServiceProcess.ServiceInstaller>  
 Décrit les fonctionnalités de la classe <xref:System.ServiceProcess.ServiceInstaller>, qui est utilisée parallèlement à la classe <xref:System.ServiceProcess.ServiceProcessInstaller> pour installer et désinstaller votre service.  
  
 [Création de projets à partir de modèles](http://msdn.microsoft.com/fr-fr/7c36d86a-6b79-4480-8228-0f925f1204b2)  
 Décrit les différents types de projet utilisés dans ce chapitre et explique comment effectuer un choix parmi eux.