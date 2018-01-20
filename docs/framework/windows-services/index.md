---
title: "Développement des applications de service Windows"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- ServiceInstaller class, Windows Service applications
- Service class, Windows Service applications
- Windows Service applications
- Windows NT services
- ServiceProcessInstaller class, Windows Service applications
- services
- .NET applications, Windows applications
ms.assetid: ba72d648-9553-4849-b829-069ad5ea014b
caps.latest.revision: "18"
author: ghogen
ms.author: ghogen
manager: douge
ms.workload: dotnet
ms.openlocfilehash: 325e43f4b1734bc6ab8753285e5069f36b0fda51
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/19/2018
---
# <a name="developing-windows-service-applications"></a>Développement des applications de service Windows
À l’aide de Microsoft [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] ou Microsoft [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] SDK, vous pouvez facilement créer services en créant une application qui est installée en tant que service. Ce type d’application est appelé un service Windows. Avec les fonctionnalités de framework, vous pouvez créer des services, les installer, Démarrer, arrêter et contrôler leur comportement.  
  
> [!WARNING]
>  Le modèle de service Windows pour C++ n’était pas inclus dans Visual Studio 2010. Pour créer un service Windows, vous pouvez créer un service dans le code managé en Visual c# ou Visual Basic, qui peut interagir avec le code C++ existant si nécessaire, ou vous pouvez créer un service Windows en C++ natif à l’aide de le [Assistant de projet ATL](/cpp/atl/reference/atl-project-wizard).  
  
## <a name="in-this-section"></a>Dans cette section  
 [Introduction aux applications de service Windows](../../../docs/framework/windows-services/introduction-to-windows-service-applications.md)  
 Fournit une vue d’ensemble des applications de service Windows, la durée de vie d’un service, et comment les applications de service diffèrent des autres types de projets courants.  
  
 [Procédure pas à pas : création d’une application de service Windows dans le Concepteur de composants](../../../docs/framework/windows-services/walkthrough-creating-a-windows-service-application-in-the-component-designer.md)  
 Fournit un exemple de création d’un service dans [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)] et Visual c#.  
  
 [Architecture de programmation d’une application de service](../../../docs/framework/windows-services/service-application-programming-architecture.md)  
 Explique les éléments de langage utilisées dans la programmation de service.  
  
 [Guide pratique pour créer des services Windows](../../../docs/framework/windows-services/how-to-create-windows-services.md)  
 Décrit le processus de création et la configuration des services Windows en utilisant le modèle de projet de service Windows.  
  
## <a name="related-sections"></a>Rubriques connexes  
 <xref:System.ServiceProcess.ServiceBase>  
 Décrit les principales fonctionnalités de la <xref:System.ServiceProcess.ServiceBase> (classe), qui est utilisé pour créer des services.  
  
 <xref:System.ServiceProcess.ServiceProcessInstaller>  
 Décrit les fonctionnalités de la <xref:System.ServiceProcess.ServiceProcessInstaller> (classe), qui est utilisée avec la <xref:System.ServiceProcess.ServiceInstaller> classe pour installer et désinstaller vos services.  
  
 <xref:System.ServiceProcess.ServiceInstaller>  
 Décrit les fonctionnalités de la <xref:System.ServiceProcess.ServiceInstaller> (classe), qui est utilisée avec la <xref:System.ServiceProcess.ServiceProcessInstaller> classe pour installer et désinstaller votre service.  
  
 [NIB création de projets à partir de modèles](http://msdn.microsoft.com/library/7c36d86a-6b79-4480-8228-0f925f1204b2)  
 Décrit les projets de types utilisés dans ce chapitre et comment choisir entre eux.
