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
# <a name="developing-windows-service-applications"></a><span data-ttu-id="fac85-102">Développement des applications de service Windows</span><span class="sxs-lookup"><span data-stu-id="fac85-102">Developing Windows Service Applications</span></span>
<span data-ttu-id="fac85-103">À l’aide de Microsoft [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] ou Microsoft [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] SDK, vous pouvez facilement créer services en créant une application qui est installée en tant que service.</span><span class="sxs-lookup"><span data-stu-id="fac85-103">Using Microsoft [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] or the Microsoft [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] SDK, you can easily create services by creating an application that is installed as a service.</span></span> <span data-ttu-id="fac85-104">Ce type d’application est appelé un service Windows.</span><span class="sxs-lookup"><span data-stu-id="fac85-104">This type of application is called a Windows service.</span></span> <span data-ttu-id="fac85-105">Avec les fonctionnalités de framework, vous pouvez créer des services, les installer, Démarrer, arrêter et contrôler leur comportement.</span><span class="sxs-lookup"><span data-stu-id="fac85-105">With framework features, you can create services, install them, and start, stop, and otherwise control their behavior.</span></span>  
  
> [!WARNING]
>  <span data-ttu-id="fac85-106">Le modèle de service Windows pour C++ n’était pas inclus dans Visual Studio 2010.</span><span class="sxs-lookup"><span data-stu-id="fac85-106">The Windows service template for C++ was not included in Visual Studio 2010.</span></span> <span data-ttu-id="fac85-107">Pour créer un service Windows, vous pouvez créer un service dans le code managé en Visual c# ou Visual Basic, qui peut interagir avec le code C++ existant si nécessaire, ou vous pouvez créer un service Windows en C++ natif à l’aide de le [Assistant de projet ATL](/cpp/atl/reference/atl-project-wizard).</span><span class="sxs-lookup"><span data-stu-id="fac85-107">To create a Windows service, you can either create a service in managed code in Visual C# or Visual Basic, which could interoperate with existing C++ code if required, or you can create a Windows service in native C++ by using the [ATL Project Wizard](/cpp/atl/reference/atl-project-wizard).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="fac85-108">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="fac85-108">In This Section</span></span>  
 [<span data-ttu-id="fac85-109">Introduction aux applications de service Windows</span><span class="sxs-lookup"><span data-stu-id="fac85-109">Introduction to Windows Service Applications</span></span>](../../../docs/framework/windows-services/introduction-to-windows-service-applications.md)  
 <span data-ttu-id="fac85-110">Fournit une vue d’ensemble des applications de service Windows, la durée de vie d’un service, et comment les applications de service diffèrent des autres types de projets courants.</span><span class="sxs-lookup"><span data-stu-id="fac85-110">Provides an overview of Windows service applications, the lifetime of a service, and how service applications differ from other common project types.</span></span>  
  
 [<span data-ttu-id="fac85-111">Procédure pas à pas : création d’une application de service Windows dans le Concepteur de composants</span><span class="sxs-lookup"><span data-stu-id="fac85-111">Walkthrough: Creating a Windows Service Application in the Component Designer</span></span>](../../../docs/framework/windows-services/walkthrough-creating-a-windows-service-application-in-the-component-designer.md)  
 <span data-ttu-id="fac85-112">Fournit un exemple de création d’un service dans [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)] et Visual c#.</span><span class="sxs-lookup"><span data-stu-id="fac85-112">Provides an example of creating a service in [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)] and Visual C#.</span></span>  
  
 [<span data-ttu-id="fac85-113">Architecture de programmation d’une application de service</span><span class="sxs-lookup"><span data-stu-id="fac85-113">Service Application Programming Architecture</span></span>](../../../docs/framework/windows-services/service-application-programming-architecture.md)  
 <span data-ttu-id="fac85-114">Explique les éléments de langage utilisées dans la programmation de service.</span><span class="sxs-lookup"><span data-stu-id="fac85-114">Explains the language elements used in service programming.</span></span>  
  
 [<span data-ttu-id="fac85-115">Guide pratique pour créer des services Windows</span><span class="sxs-lookup"><span data-stu-id="fac85-115">How to: Create Windows Services</span></span>](../../../docs/framework/windows-services/how-to-create-windows-services.md)  
 <span data-ttu-id="fac85-116">Décrit le processus de création et la configuration des services Windows en utilisant le modèle de projet de service Windows.</span><span class="sxs-lookup"><span data-stu-id="fac85-116">Describes the process of creating and configuring Windows services using the Windows service project template.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="fac85-117">Rubriques connexes</span><span class="sxs-lookup"><span data-stu-id="fac85-117">Related Sections</span></span>  
 <xref:System.ServiceProcess.ServiceBase>  
 <span data-ttu-id="fac85-118">Décrit les principales fonctionnalités de la <xref:System.ServiceProcess.ServiceBase> (classe), qui est utilisé pour créer des services.</span><span class="sxs-lookup"><span data-stu-id="fac85-118">Describes the major features of the <xref:System.ServiceProcess.ServiceBase> class, which is used to create services.</span></span>  
  
 <xref:System.ServiceProcess.ServiceProcessInstaller>  
 <span data-ttu-id="fac85-119">Décrit les fonctionnalités de la <xref:System.ServiceProcess.ServiceProcessInstaller> (classe), qui est utilisée avec la <xref:System.ServiceProcess.ServiceInstaller> classe pour installer et désinstaller vos services.</span><span class="sxs-lookup"><span data-stu-id="fac85-119">Describes the features of the <xref:System.ServiceProcess.ServiceProcessInstaller> class, which is used along with the <xref:System.ServiceProcess.ServiceInstaller> class to install and uninstall your services.</span></span>  
  
 <xref:System.ServiceProcess.ServiceInstaller>  
 <span data-ttu-id="fac85-120">Décrit les fonctionnalités de la <xref:System.ServiceProcess.ServiceInstaller> (classe), qui est utilisée avec la <xref:System.ServiceProcess.ServiceProcessInstaller> classe pour installer et désinstaller votre service.</span><span class="sxs-lookup"><span data-stu-id="fac85-120">Describes the features of the <xref:System.ServiceProcess.ServiceInstaller> class, which is used along with the <xref:System.ServiceProcess.ServiceProcessInstaller> class to install and uninstall your service.</span></span>  
  
 [<span data-ttu-id="fac85-121">NIB création de projets à partir de modèles</span><span class="sxs-lookup"><span data-stu-id="fac85-121">NIB Creating Projects from Templates</span></span>](http://msdn.microsoft.com/library/7c36d86a-6b79-4480-8228-0f925f1204b2)  
 <span data-ttu-id="fac85-122">Décrit les projets de types utilisés dans ce chapitre et comment choisir entre eux.</span><span class="sxs-lookup"><span data-stu-id="fac85-122">Describes the projects types used in this chapter and how to choose between them.</span></span>
