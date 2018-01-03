---
title: Connexion de contexte
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e443ca86-9243-4234-a822-ed10a53a9de0
caps.latest.revision: "4"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: f3bb732644bf9373d847eb14b63e69a756cb3ac6
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="the-context-connection"></a><span data-ttu-id="47020-102">Connexion de contexte</span><span class="sxs-lookup"><span data-stu-id="47020-102">The Context Connection</span></span>
<span data-ttu-id="47020-103">Le problème de l'accès aux données interne est un scénario assez courant.</span><span class="sxs-lookup"><span data-stu-id="47020-103">The problem of internal data access is a fairly common scenario.</span></span> <span data-ttu-id="47020-104">Vous souhaitez accéder au même serveur, celui sur lequel s'exécute votre procédure stockée Common Language Runtime (CLR) ou fonction.</span><span class="sxs-lookup"><span data-stu-id="47020-104">That is, you wish to access the same server on which your common language runtime (CLR) stored procedure or function is executing.</span></span> <span data-ttu-id="47020-105">Une option consiste à créer une connexion à l'aide de <xref:System.Data.SqlClient.SqlConnection>, à spécifier une chaîne de connexion pointant vers le serveur local, puis à ouvrir la connexion.</span><span class="sxs-lookup"><span data-stu-id="47020-105">One option is to create a connection using <xref:System.Data.SqlClient.SqlConnection>, specify a connection string that points to the local server, and open the connection.</span></span> <span data-ttu-id="47020-106">Cela nécessite la spécification d'informations d'identification pour la connexion.</span><span class="sxs-lookup"><span data-stu-id="47020-106">This requires specifying credentials for logging in.</span></span> <span data-ttu-id="47020-107">La connexion s'opère dans une session de base de données différente de la procédure stockée ou de la fonction, elle peut avoir des options `SET` différentes, elle est dans une transaction séparée, elle ne voit pas vos tables temporaires, etc.</span><span class="sxs-lookup"><span data-stu-id="47020-107">The connection is in a different database session than the stored procedure or function, it may have different `SET` options, it is in a separate transaction, it does not see your temporary tables, and so on.</span></span> <span data-ttu-id="47020-108">Si votre code de fonction ou de procédure stockée managée s'exécute dans le processus SQL Server, c'est parce que quelqu'un s'est connecté à ce serveur et a exécuté une instruction SQL pour l'invoquer.</span><span class="sxs-lookup"><span data-stu-id="47020-108">If your managed stored procedure or function code is executing in the SQL Server process, it is because someone connected to that server and executed a SQL statement to invoke it.</span></span> <span data-ttu-id="47020-109">Vous souhaitez probablement que la fonction ou la procédure stockée s'exécute dans le contexte de cette connexion, ainsi qu'avec sa transaction, les options `SET`, etc.</span><span class="sxs-lookup"><span data-stu-id="47020-109">You probably want the stored procedure or function to execute in the context of that connection, along with its transaction, `SET` options, and so on.</span></span> <span data-ttu-id="47020-110">C'est ce que l'on appelle une connexion de contexte.</span><span class="sxs-lookup"><span data-stu-id="47020-110">This is called the context connection.</span></span>  
  
 <span data-ttu-id="47020-111">La connexion de contexte vous permet d'exécuter des instructions Transact-SQL dans le même contexte que celui dans lequel votre code a été invoqué en premier lieu.</span><span class="sxs-lookup"><span data-stu-id="47020-111">The context connection lets you execute Transact-SQL statements in the same context that your code was invoked in the first place.</span></span> <span data-ttu-id="47020-112">Pour obtenir des informations plus détaillées, voir la documentation en ligne de SQL Server pour la version de SQL Server que vous utilisez.</span><span class="sxs-lookup"><span data-stu-id="47020-112">For more detailed information, see the version of SQL Server Books Online for the version of SQL Server you are using.</span></span>  
  
 <span data-ttu-id="47020-113">**Documentation en ligne de SQL Server**</span><span class="sxs-lookup"><span data-stu-id="47020-113">**SQL Server Books Online**</span></span>  
  
1.  [<span data-ttu-id="47020-114">Connexion de contexte</span><span class="sxs-lookup"><span data-stu-id="47020-114">The Context Connection</span></span>](http://go.microsoft.com/fwlink/?LinkId=115395)  
  
## <a name="see-also"></a><span data-ttu-id="47020-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="47020-115">See Also</span></span>  
 [<span data-ttu-id="47020-116">Création d’objets SQL Server 2005 dans le Code managé</span><span class="sxs-lookup"><span data-stu-id="47020-116">Creating SQL Server 2005 Objects In Managed Code</span></span>](http://msdn.microsoft.com/en-us/5358a825-e19b-49aa-8214-674ce5fed1da)  
 [<span data-ttu-id="47020-117">Fournisseurs managés ADO.NET et centre de développement DataSet</span><span class="sxs-lookup"><span data-stu-id="47020-117">ADO.NET Managed Providers and DataSet Developer Center</span></span>](http://go.microsoft.com/fwlink/?LinkId=217917)
