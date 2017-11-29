---
title: "Types CLR définis par l'utilisateur"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 9f70e0b0-3a0d-4eb1-b914-07a5d0c167c2
caps.latest.revision: "6"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 0e81cf54ed9dc516d88b8c7a97c8a5b33b8943d0
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="clr-user-defined-types"></a><span data-ttu-id="899c7-102">Types CLR définis par l'utilisateur</span><span class="sxs-lookup"><span data-stu-id="899c7-102">CLR User-Defined Types</span></span>
<span data-ttu-id="899c7-103">Microsoft SQL Server fournit la prise en charge des types définis par l'utilisateur (UDT) implémentée avec le Common Language Runtime (CLR) Microsoft .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="899c7-103">Microsoft SQL Server provides support for user-defined types (UDTs) implemented with the Microsoft .NET Framework common language runtime (CLR).</span></span> <span data-ttu-id="899c7-104">Le CLR est intégré dans SQL Server et son mécanisme vous permet d'étendre le système de type de la base de données.</span><span class="sxs-lookup"><span data-stu-id="899c7-104">The CLR is integrated into SQL Server, and this mechanism enables you to extend the type system of the database.</span></span> <span data-ttu-id="899c7-105">Les UDT offrent à l'utilisateur l'extensibilité du système de type de données SQL Server, ainsi que la possibilité de définir des types structurés complexes.</span><span class="sxs-lookup"><span data-stu-id="899c7-105">UDTs provide user extensibility of the SQL Server data type system, and also the ability to define complex structured types.</span></span>  
  
 <span data-ttu-id="899c7-106">Les UDT peuvent offrir deux avantages clés dans la perspective d'une architecture d'application :</span><span class="sxs-lookup"><span data-stu-id="899c7-106">UDTs can provide two key benefits from an application architecture perspective:</span></span>  
  
-   <span data-ttu-id="899c7-107">Puissante encapsulation (tant au niveau du client que du serveur) entre l'état interne et les comportements externes.</span><span class="sxs-lookup"><span data-stu-id="899c7-107">Strong encapsulation (both in the client and the server) between the internal state and the external behaviors.</span></span>  
  
-   <span data-ttu-id="899c7-108">Profonde intégration avec d'autres fonctionnalités serveur liées.</span><span class="sxs-lookup"><span data-stu-id="899c7-108">Deep integration with other related server features.</span></span> <span data-ttu-id="899c7-109">Après que vous avez défini votre propre UDT, vous pouvez l'utiliser dans tous les contextes où vous pouvez utiliser un type système dans SQL Server, notamment des définitions de colonne, variables, paramètres, résultats de fonction, curseurs, déclencheurs et réplication.</span><span class="sxs-lookup"><span data-stu-id="899c7-109">Once you define your own UDT, you can use it in all contexts where you can use a system type in SQL Server, including column definitions, and as variables, parameters, function results, cursors, triggers, and replication.</span></span>  
  
 <span data-ttu-id="899c7-110">Pour obtenir des informations plus détaillées, voir la documentation en ligne de SQL Server pour la version de SQL Server que vous utilisez.</span><span class="sxs-lookup"><span data-stu-id="899c7-110">For more detailed information, see the version of SQL Server Books Online for the version of SQL Server you are using.</span></span>  
  
 <span data-ttu-id="899c7-111">**Documentation en ligne de SQL Server**</span><span class="sxs-lookup"><span data-stu-id="899c7-111">**SQL Server Books Online**</span></span>  
  
1.  [<span data-ttu-id="899c7-112">Types CLR définis par l’utilisateur</span><span class="sxs-lookup"><span data-stu-id="899c7-112">CLR User-Defined Types</span></span>](http://go.microsoft.com/fwlink/?LinkId=98366)  
  
## <a name="see-also"></a><span data-ttu-id="899c7-113">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="899c7-113">See Also</span></span>  
 [<span data-ttu-id="899c7-114">Création d’objets SQL Server 2005 dans le Code managé</span><span class="sxs-lookup"><span data-stu-id="899c7-114">Creating SQL Server 2005 Objects In Managed Code</span></span>](http://msdn.microsoft.com/en-us/5358a825-e19b-49aa-8214-674ce5fed1da)  
 [<span data-ttu-id="899c7-115">Fournisseurs managés ADO.NET et centre de développement DataSet</span><span class="sxs-lookup"><span data-stu-id="899c7-115">ADO.NET Managed Providers and DataSet Developer Center</span></span>](http://go.microsoft.com/fwlink/?LinkId=217917)
