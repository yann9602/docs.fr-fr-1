---
title: SQL Server Compact et LINQ to SQL
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 59022359-a5a2-4c42-9a6a-5c0259c3ad17
caps.latest.revision: "5"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: 9409c17065b0421ec32a61352f9c0b975095ab44
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/17/2018
---
# <a name="sql-server-compact-and-linq-to-sql"></a><span data-ttu-id="54424-102">SQL Server Compact et LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="54424-102">SQL Server Compact and LINQ to SQL</span></span>
<span data-ttu-id="54424-103">SQL Server Compact est la base de données par défaut installé avec Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="54424-103">SQL Server Compact is the default database installed with Visual Studio.</span></span> <span data-ttu-id="54424-104">Pour plus d’informations, consultez [PAVE sur à l’aide de SQL Server Compact (Visual Studio)](http://msdn.microsoft.com/en-us/13320dd1-94e5-4077-bf76-8df253695ccc).</span><span class="sxs-lookup"><span data-stu-id="54424-104">For more information, see [PAVE OVER Using SQL Server Compact (Visual Studio)](http://msdn.microsoft.com/en-us/13320dd1-94e5-4077-bf76-8df253695ccc).</span></span>  
  
 <span data-ttu-id="54424-105">Cette rubrique décrit les principales différences dans l’utilisation, la configuration, ensembles de fonctionnalités et étendue de [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] prend en charge.</span><span class="sxs-lookup"><span data-stu-id="54424-105">This topic outlines the key differences in usage, configuration, feature sets, and scope of [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] support.</span></span>  
  
## <a name="characteristics-of-sql-server-compact-in-relation-to-linq-to-sql"></a><span data-ttu-id="54424-106">Caractéristiques de SQL Server Compact par rapport à LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="54424-106">Characteristics of SQL Server Compact in Relation to LINQ to SQL</span></span>  
 <span data-ttu-id="54424-107">Par défaut, SQL Server Compact est installé pour tous les [!INCLUDE[vs_current_short](../../../../../../includes/vs-current-short-md.md)] éditions et est par conséquent disponible sur l’ordinateur de développement pour une utilisation avec [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].</span><span class="sxs-lookup"><span data-stu-id="54424-107">By default, SQL Server Compact is installed for all [!INCLUDE[vs_current_short](../../../../../../includes/vs-current-short-md.md)] editions, and is therefore available on the development computer for use with [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].</span></span> <span data-ttu-id="54424-108">Mais le déploiement d’une application qui utilise SQL Server Compact et [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] diffère de celle pour une [!INCLUDE[ssNoVersion](../../../../../../includes/ssnoversion-md.md)] application.</span><span class="sxs-lookup"><span data-stu-id="54424-108">But deployment of an application that uses SQL Server Compact and [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] differs from that for a [!INCLUDE[ssNoVersion](../../../../../../includes/ssnoversion-md.md)] application.</span></span> <span data-ttu-id="54424-109">SQL Server Compact ne fait pas partie du .NET Framework et doit par conséquent être fourni avec l'application ou téléchargé séparément depuis le site Microsoft.</span><span class="sxs-lookup"><span data-stu-id="54424-109">SQL Server Compact is not a part of the .NET Framework, and therefore must be packaged with the application or downloaded separately from the Microsoft site.</span></span>  
  
 <span data-ttu-id="54424-110">Notez les caractéristiques suivantes :</span><span class="sxs-lookup"><span data-stu-id="54424-110">Note the following characteristics:</span></span>  
  
-   <span data-ttu-id="54424-111">SQL Server Compact est fourni comme une DLL qui peut être utilisée directement sur les fichiers de base de données (extension .sdf).</span><span class="sxs-lookup"><span data-stu-id="54424-111">SQL Server Compact is packaged as a DLL that can be used against database files (.sdf extension) directly.</span></span>  
  
-   <span data-ttu-id="54424-112">SQL Server Compact s’exécute dans le même processus que l’application cliente.</span><span class="sxs-lookup"><span data-stu-id="54424-112">SQL Server Compact runs in the same process as the client application.</span></span> <span data-ttu-id="54424-113">L’efficacité de la communication avec SQL Server Compact peut par conséquent être beaucoup plus importante que la communication avec [!INCLUDE[ssNoVersion](../../../../../../includes/ssnoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="54424-113">The efficiency of communication with SQL Server Compact can therefore be significantly higher than communicating with [!INCLUDE[ssNoVersion](../../../../../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="54424-114">En revanche, SQL Server Compact requiert l’interopérabilité entre le code managé et avec ses coûts connexes.</span><span class="sxs-lookup"><span data-stu-id="54424-114">On the other hand, SQL Server Compact does require interoperability between managed and unmanaged code with its attendant costs.</span></span>  
  
-   <span data-ttu-id="54424-115">La taille de la DLL SQL Server Compact est faible.</span><span class="sxs-lookup"><span data-stu-id="54424-115">The size of the SQL Server Compact DLL is small.</span></span> <span data-ttu-id="54424-116">Cette fonctionnalité réduit la taille globale de l’application.</span><span class="sxs-lookup"><span data-stu-id="54424-116">This feature reduces the overall application size.</span></span>  
  
-   <span data-ttu-id="54424-117">Le runtime de [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] et l'outil en ligne de commande SQLMetal prennent en charge SQL Server Compact.</span><span class="sxs-lookup"><span data-stu-id="54424-117">The [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] runtime and the SQLMetal command-line tool support SQL Server Compact.</span></span>  
  
-   <span data-ttu-id="54424-118">[!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)] ne prend pas en charge SQL Server Compact.</span><span class="sxs-lookup"><span data-stu-id="54424-118">The [!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)] does not support SQL Server Compact.</span></span>  
  
## <a name="feature-set"></a><span data-ttu-id="54424-119">Jeu de fonctionnalités</span><span class="sxs-lookup"><span data-stu-id="54424-119">Feature Set</span></span>  
 <span data-ttu-id="54424-120">L’ensemble de fonctionnalités SQL Server Compact est beaucoup plus simple que l’ensemble des fonctionnalités de [!INCLUDE[ssNoVersion](../../../../../../includes/ssnoversion-md.md)] manières suivantes peuvent affecter [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] applications :</span><span class="sxs-lookup"><span data-stu-id="54424-120">The SQL Server Compact feature set is much simpler than the feature set of [!INCLUDE[ssNoVersion](../../../../../../includes/ssnoversion-md.md)] in the following ways that can affect [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] applications :</span></span>  
  
-   <span data-ttu-id="54424-121">SQL Server Compact ne prend pas en charge de procédures stockées ou de vues.</span><span class="sxs-lookup"><span data-stu-id="54424-121">SQL Server Compact does not support stored procedures or views.</span></span>  
  
-   <span data-ttu-id="54424-122">SQL Server Compact prend en charge uniquement un sous-ensemble de types de données et de fonctions SQL.</span><span class="sxs-lookup"><span data-stu-id="54424-122">SQL Server Compact supports only a subset of data types and SQL functions.</span></span>  
  
-   <span data-ttu-id="54424-123">SQL Server Compact prend en charge uniquement un sous-ensemble de constructions SQL.</span><span class="sxs-lookup"><span data-stu-id="54424-123">SQL Server Compact supports only a subset of SQL constructs.</span></span>  
  
-   <span data-ttu-id="54424-124">SQL Server Compact fournit uniquement un optimiseur minimal.</span><span class="sxs-lookup"><span data-stu-id="54424-124">SQL Server Compact provides only a minimal optimizer.</span></span> <span data-ttu-id="54424-125">Il est possible que certaines requêtes peuvent expirer.</span><span class="sxs-lookup"><span data-stu-id="54424-125">It is possible that some queries might time out.</span></span>  
  
-   <span data-ttu-id="54424-126">SQL Server Compact ne prend pas en charge la confiance partielle.</span><span class="sxs-lookup"><span data-stu-id="54424-126">SQL Server Compact does not support partial trust.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="54424-127">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="54424-127">See Also</span></span>  
 [<span data-ttu-id="54424-128">Référence</span><span class="sxs-lookup"><span data-stu-id="54424-128">Reference</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/reference.md)
