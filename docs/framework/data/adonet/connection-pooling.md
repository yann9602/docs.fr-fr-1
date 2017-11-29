---
title: Regroupement de connexions
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 955c057f-aea8-4ba8-aa6d-e3dfa18ba8d5
caps.latest.revision: "3"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: c7398fbea3b59cafed6f9a7f2f4f0440ef29b80a
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="connection-pooling"></a><span data-ttu-id="bcc14-102">Regroupement de connexions</span><span class="sxs-lookup"><span data-stu-id="bcc14-102">Connection Pooling</span></span>
<span data-ttu-id="bcc14-103">Se connecter à une source de données peut prendre beaucoup de temps.</span><span class="sxs-lookup"><span data-stu-id="bcc14-103">Connecting to a data source can be time consuming.</span></span> <span data-ttu-id="bcc14-104">Pour réduire le coût de l’ouverture de connexions, ADO.NET utilise une technique d’optimisation nommée *le regroupement de connexions*, ce qui réduit le coût de l’ouverture et la fermeture des connexions.</span><span class="sxs-lookup"><span data-stu-id="bcc14-104">To minimize the cost of opening connections, ADO.NET uses an optimization technique called *connection pooling*, which minimizes the cost of repeatedly opening and closing connections.</span></span> <span data-ttu-id="bcc14-105">Le regroupement de connexions est géré différemment pour les fournisseurs de données .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="bcc14-105">Connection pooling is handled differently for the .NET Framework data providers.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="bcc14-106">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="bcc14-106">In This Section</span></span>  
 [<span data-ttu-id="bcc14-107">SQL Server regroupement de connexions (ADO.NET)</span><span class="sxs-lookup"><span data-stu-id="bcc14-107">SQL Server Connection Pooling (ADO.NET)</span></span>](../../../../docs/framework/data/adonet/sql-server-connection-pooling.md)  
 <span data-ttu-id="bcc14-108">Fournit une vue d'ensemble du regroupement de connexions et décrit son fonctionnement dans [!INCLUDE[ssNoVersion](../../../../includes/ssnoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="bcc14-108">Provides an overview of connection pooling and describes how connection pooling works in [!INCLUDE[ssNoVersion](../../../../includes/ssnoversion-md.md)].</span></span>  
  
 [<span data-ttu-id="bcc14-109">OLE DB, ODBC et Oracle Connection le regroupement</span><span class="sxs-lookup"><span data-stu-id="bcc14-109">OLE DB, ODBC, and Oracle Connection Pooling</span></span>](../../../../docs/framework/data/adonet/ole-db-odbc-and-oracle-connection-pooling.md)  
 <span data-ttu-id="bcc14-110">Décrit le regroupement de connexions pour les fournisseurs de données .NET Framework pour OLE DB, ODBC et Oracle.</span><span class="sxs-lookup"><span data-stu-id="bcc14-110">Describes connection pooling for the .NET Framework Data Provider for OLE DB, the .NET Framework Data Provider for ODBC, and the .NET Framework Data Provider for Oracle.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bcc14-111">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="bcc14-111">See Also</span></span>  
 [<span data-ttu-id="bcc14-112">Extraction et modification de données dans ADO.NET</span><span class="sxs-lookup"><span data-stu-id="bcc14-112">Retrieving and Modifying Data in ADO.NET</span></span>](../../../../docs/framework/data/adonet/retrieving-and-modifying-data.md)  
 [<span data-ttu-id="bcc14-113">Fournisseurs managés ADO.NET et centre de développement DataSet</span><span class="sxs-lookup"><span data-stu-id="bcc14-113">ADO.NET Managed Providers and DataSet Developer Center</span></span>](http://go.microsoft.com/fwlink/?LinkId=217917)
