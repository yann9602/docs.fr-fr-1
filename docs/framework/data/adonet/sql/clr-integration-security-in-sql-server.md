---
title: "Sécurité de l'intégration du CLR dans SQL Server"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 489fe096-fd1d-42de-8438-bf7aed46aea2
caps.latest.revision: "5"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: 37437d827fc0ff6583178f33f4cceaa86f5175dd
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/19/2018
---
# <a name="clr-integration-security-in-sql-server"></a><span data-ttu-id="16fad-102">Sécurité de l'intégration du CLR dans SQL Server</span><span class="sxs-lookup"><span data-stu-id="16fad-102">CLR Integration Security in SQL Server</span></span>
<span data-ttu-id="16fad-103">Microsoft SQL Server introduit le composant Common Language Runtime (CLR) du .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="16fad-103">Microsoft SQL Server provides the integration of the common language runtime (CLR) component of the .NET Framework.</span></span> <span data-ttu-id="16fad-104">L'intégration du CLR vous permet d'écrire des procédures stockées, des déclencheurs, des types définis par l'utilisateur, des fonctions définies par l'utilisateur, des agrégats définis par l'utilisateur et des fonctions de flux évaluées par une table, en utilisant tout langage .NET Framework, tel que Microsoft Visual Basic .NET ou Microsoft Visual C#.</span><span class="sxs-lookup"><span data-stu-id="16fad-104">CLR integration allows you to write stored procedures, triggers, user-defined types, user-defined functions, user-defined aggregates, and streaming table-valued functions, using any .NET Framework language, such as Microsoft Visual Basic .NET or Microsoft Visual C#.</span></span>  
  
 <span data-ttu-id="16fad-105">Le CLR prend en charge un modèle de sécurité appelé sécurité d'accès du code (CAS) pour le code managé.</span><span class="sxs-lookup"><span data-stu-id="16fad-105">The CLR supports a security model called code access security (CAS) for managed code.</span></span> <span data-ttu-id="16fad-106">Dans ce modèle, les autorisations sont accordées aux assemblys en fonction de la preuve fournie par le code dans les métadonnées.</span><span class="sxs-lookup"><span data-stu-id="16fad-106">In this model, permissions are granted to assemblies based on evidence supplied by the code in metadata.</span></span> <span data-ttu-id="16fad-107">SQL Server intègre le modèle de sécurité de SQL Server, basé sur l'utilisateur avec le modèle de sécurité du CLR, basé sur l'accès du code.</span><span class="sxs-lookup"><span data-stu-id="16fad-107">SQL Server integrates the user-based security model of SQL Server with the code access-based security model of the CLR.</span></span>  
  
## <a name="external-resources"></a><span data-ttu-id="16fad-108">Ressources externes</span><span class="sxs-lookup"><span data-stu-id="16fad-108">External Resources</span></span>  
 <span data-ttu-id="16fad-109">Pour plus d'informations sur l'intégration du CLR avec SQL Server, voir les ressources répertoriées ci-dessous.</span><span class="sxs-lookup"><span data-stu-id="16fad-109">For more information on CLR integration with SQL Server, see the following resources.</span></span>  
  
|<span data-ttu-id="16fad-110">Ressource</span><span class="sxs-lookup"><span data-stu-id="16fad-110">Resource</span></span>|<span data-ttu-id="16fad-111">Description</span><span class="sxs-lookup"><span data-stu-id="16fad-111">Description</span></span>|  
|--------------|-----------------|  
|[<span data-ttu-id="16fad-112">Sécurité d’accès du code</span><span class="sxs-lookup"><span data-stu-id="16fad-112">Code Access Security</span></span>](http://msdn.microsoft.com/library/23a20143-241d-4fe5-9d9f-3933fd594c03)|<span data-ttu-id="16fad-113">Contient des rubriques qui décrivent la sécurité d'accès du code dans le .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="16fad-113">Contains topics describing CAS in the .NET Framework.</span></span>|  
|[<span data-ttu-id="16fad-114">Sécurité d’intégration du CLR</span><span class="sxs-lookup"><span data-stu-id="16fad-114">CLR Integration Security</span></span>](http://go.microsoft.com/fwlink/?LinkId=59998)|<span data-ttu-id="16fad-115">Présente le modèle de sécurité pour le code managé qui s'exécute au sein de SQL Server.</span><span class="sxs-lookup"><span data-stu-id="16fad-115">Discusses the security model for managed code executing inside of SQL Server.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="16fad-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="16fad-116">See Also</span></span>  
 [<span data-ttu-id="16fad-117">Sécurisation des applications ADO.NET</span><span class="sxs-lookup"><span data-stu-id="16fad-117">Securing ADO.NET Applications</span></span>](../../../../../docs/framework/data/adonet/securing-ado-net-applications.md)  
 [<span data-ttu-id="16fad-118">Scénarios de sécurité des applications dans SQL Server</span><span class="sxs-lookup"><span data-stu-id="16fad-118">Application Security Scenarios in SQL Server</span></span>](../../../../../docs/framework/data/adonet/sql/application-security-scenarios-in-sql-server.md)  
 [<span data-ttu-id="16fad-119">Intégration CLR SQL Server</span><span class="sxs-lookup"><span data-stu-id="16fad-119">SQL Server Common Language Runtime Integration</span></span>](../../../../../docs/framework/data/adonet/sql/sql-server-common-language-runtime-integration.md)  
 [<span data-ttu-id="16fad-120">Fournisseurs managés ADO.NET et centre de développement DataSet</span><span class="sxs-lookup"><span data-stu-id="16fad-120">ADO.NET Managed Providers and DataSet Developer Center</span></span>](http://go.microsoft.com/fwlink/?LinkId=217917)
