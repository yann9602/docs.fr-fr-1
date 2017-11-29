---
title: "Comment : migrer le code client des services Web ASP.NET vers Windows Communication Foundation"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 2e0a22a7-e1d5-4718-8997-4319a7cd9027
caps.latest.revision: "6"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: d77e07cca938b67f5b79416ac4d8fdef96739ed2
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="how-to-migrate-aspnet-web-service-client-code-to-the-windows-communication-foundation"></a><span data-ttu-id="7caa2-102">Comment : migrer le code client des services Web ASP.NET vers Windows Communication Foundation</span><span class="sxs-lookup"><span data-stu-id="7caa2-102">How to: Migrate ASP.NET Web Service Client Code to the Windows Communication Foundation</span></span>
<span data-ttu-id="7caa2-103">La procédure suivante décrit la procédure générale de migration du code client des services Web ASP.NET vers [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].</span><span class="sxs-lookup"><span data-stu-id="7caa2-103">The following procedure describes the broad steps that need to be followed to migrate ASP.NET Web Service client code to [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].</span></span>  
  
## <a name="procedure"></a><span data-ttu-id="7caa2-104">Procédure</span><span class="sxs-lookup"><span data-stu-id="7caa2-104">Procedure</span></span>  
  
#### <a name="to-migrate-aspnet-web-service-client-code-to-wcf"></a><span data-ttu-id="7caa2-105">Pour migrer le code client des services Web ASP.NET vers WCF</span><span class="sxs-lookup"><span data-stu-id="7caa2-105">To migrate ASP.NET Web Service client code to WCF</span></span>  
  
1.  <span data-ttu-id="7caa2-106">Assurez-vous qu'un jeu complet de tests existe pour le client.</span><span class="sxs-lookup"><span data-stu-id="7caa2-106">Ensure that a comprehensive set of tests exist for the client.</span></span>  
  
2.  <span data-ttu-id="7caa2-107">Utilisez Visual Studio 2005 pour mettre à niveau l'application cliente vers .NET 2.0.</span><span class="sxs-lookup"><span data-stu-id="7caa2-107">Use Visual Studio 2005 to upgrade the client application to .NET 2.0.</span></span> <span data-ttu-id="7caa2-108">Exécutez l'ensemble des tests.</span><span class="sxs-lookup"><span data-stu-id="7caa2-108">Run the set of tests.</span></span>  
  
3.  <span data-ttu-id="7caa2-109">Supprimez le code client ASP.NET du projet client.</span><span class="sxs-lookup"><span data-stu-id="7caa2-109">Remove ASP.NET client code from the client project.</span></span> <span data-ttu-id="7caa2-110">Ce code se trouve dans les modules générés à l'aide de l'outil WSDL.exe.</span><span class="sxs-lookup"><span data-stu-id="7caa2-110">That code is in modules generated using the WSDL.exe tool.</span></span>  
  
4.  <span data-ttu-id="7caa2-111">Générer [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] code client qui utilise le [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md).</span><span class="sxs-lookup"><span data-stu-id="7caa2-111">Generate [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] client code using the [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md).</span></span> <span data-ttu-id="7caa2-112">Ajoutez ce code au projet client et fusionnez la sortie de la configuration dans le fichier de configuration existant du client.</span><span class="sxs-lookup"><span data-stu-id="7caa2-112">Add that code to the client project and merge the configuration output into the client’s existing configuration file.</span></span>  
  
5.  <span data-ttu-id="7caa2-113">Compilez l'application.</span><span class="sxs-lookup"><span data-stu-id="7caa2-113">Compile the application.</span></span> <span data-ttu-id="7caa2-114">Réparez les erreurs de compilation en remplaçant les références aux types de clients ASP.NET précédents par les références aux nouveaux types de clients [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].</span><span class="sxs-lookup"><span data-stu-id="7caa2-114">Repair the compilation errors by replacing references to the former ASP.NET client types with references to the new [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] client types.</span></span>  
  
6.  <span data-ttu-id="7caa2-115">Exécutez l'ensemble des tests.</span><span class="sxs-lookup"><span data-stu-id="7caa2-115">Run the set of tests.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7caa2-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="7caa2-116">See Also</span></span>  
 [<span data-ttu-id="7caa2-117">Comment : migrer du Code de Service Web ASP.NET vers Windows Communication Foundation</span><span class="sxs-lookup"><span data-stu-id="7caa2-117">How to: Migrate ASP.NET Web Service Code to the Windows Communication Foundation</span></span>](../../../../docs/framework/wcf/feature-details/migrate-asp-net-web-service-to-wcf.md)
