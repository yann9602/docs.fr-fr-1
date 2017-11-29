---
title: Attribution d'autorisations de niveau ligne dans SQL Server
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a55aaa12-34ab-41cd-9dec-fd255b29258c
caps.latest.revision: "5"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: f6e71511286ce7451b2967e9c66ea2209549a356
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="granting-row-level-permissions-in-sql-server"></a><span data-ttu-id="ed32a-102">Attribution d'autorisations de niveau ligne dans SQL Server</span><span class="sxs-lookup"><span data-stu-id="ed32a-102">Granting Row-Level Permissions in SQL Server</span></span>
<span data-ttu-id="ed32a-103">Dans certains scénarios, il est nécessaire de contrôler l’accès aux données plus précisément qu’en se contentant d’accorder, de révoquer ou de refuser des autorisations.</span><span class="sxs-lookup"><span data-stu-id="ed32a-103">In some scenarios, there is a requirement to control access to data at a more granular level than what simply granting, revoking, or denying permissions provides.</span></span> <span data-ttu-id="ed32a-104">Par exemple, l’application de base de données d’un hôpital peut nécessiter que chaque médecin ne puisse accéder qu’aux informations de ses propres patients.</span><span class="sxs-lookup"><span data-stu-id="ed32a-104">For example, a hospital database application may require individual Doctors to be restricted to accessing information related to only their patients.</span></span> <span data-ttu-id="ed32a-105">Des scénarios similaires existent dans de nombreux environnements, notamment dans les applications financières, juridiques, publiques et militaires.</span><span class="sxs-lookup"><span data-stu-id="ed32a-105">Similar requirements exist in many environments, including finance, law, government, and military applications.</span></span> <span data-ttu-id="ed32a-106">Pour gérer ces scénarios, SQL Server 2016 propose une fonctionnalité [Sécurité au niveau des lignes](https://msdn.microsoft.com/library/dn765131.aspx) qui simplifie et centralise la logique d’accès au niveau des lignes dans une stratégie de sécurité.</span><span class="sxs-lookup"><span data-stu-id="ed32a-106">To help address these scenarios, SQL Server 2016 provides a [Row-Level Security](https://msdn.microsoft.com/library/dn765131.aspx) feature that simplifies and centralizes row-level access logic in a security policy.</span></span> <span data-ttu-id="ed32a-107">Pour les versions antérieures de SQL Server, une fonctionnalité similaire peut être obtenue à l’aide de vues permettant de mettre en œuvre un filtrage au niveau des lignes.</span><span class="sxs-lookup"><span data-stu-id="ed32a-107">For earlier versions of SQL Server, similar functionality can be achieved by using views to enact row-level filtering.</span></span>  
  
## <a name="implementing-row-level-filtering"></a><span data-ttu-id="ed32a-108">Implémentation du filtrage au niveau des lignes</span><span class="sxs-lookup"><span data-stu-id="ed32a-108">Implementing Row-level Filtering</span></span>  
 <span data-ttu-id="ed32a-109">Le filtrage au niveau des lignes est utilisé pour les applications qui stockent des informations dans une seule table, comme dans l’exemple de l’hôpital ci-dessus.</span><span class="sxs-lookup"><span data-stu-id="ed32a-109">Row-level filtering is used for applications storing information in a single table like in the hospital example above.</span></span> <span data-ttu-id="ed32a-110">Pour implémenter le filtrage au niveau des lignes, chaque ligne est associée à une colonne qui définit un paramètre de différenciation, comme un nom d’utilisateur, une étiquette ou tout autre identificateur.</span><span class="sxs-lookup"><span data-stu-id="ed32a-110">To implement row-level filtering each row has a column that defines a differentiating parameter, such as a user name, label or other identifier.</span></span> <span data-ttu-id="ed32a-111">Vous créez une stratégie de sécurité ou une vue sur la table, qui filtre les lignes auxquelles l’utilisateur a accès.</span><span class="sxs-lookup"><span data-stu-id="ed32a-111">You create either a security policy or a view on the table, which filters the rows that the user can access.</span></span> <span data-ttu-id="ed32a-112">Vous créez ensuite des procédures stockées paramétrées qui contrôlent les types de requêtes que l’utilisateur peut exécuter.</span><span class="sxs-lookup"><span data-stu-id="ed32a-112">You then create parameterized stored procedures, which control the types of queries the user can execute.</span></span>  
  
 <span data-ttu-id="ed32a-113">L’exemple suivant décrit comment configurer le filtrage au niveau des lignes à partir d’un nom d’utilisateur ou d’un nom de connexion.</span><span class="sxs-lookup"><span data-stu-id="ed32a-113">The following example describes how to configure row-level filtering based on a user or login name:</span></span>  
  
-   <span data-ttu-id="ed32a-114">Créez la table en ajoutant une colonne pour stocker le nom.</span><span class="sxs-lookup"><span data-stu-id="ed32a-114">Create the table, adding a column to store the name.</span></span>  
  
-   <span data-ttu-id="ed32a-115">Activez le filtrage au niveau des lignes :</span><span class="sxs-lookup"><span data-stu-id="ed32a-115">Enable row-level filtering:</span></span>  
  
    -   <span data-ttu-id="ed32a-116">Si vous utilisez SQL Server 2016 ou version ultérieure, ou [base de données SQL Azure](https://docs.microsoft.com/azure/sql-database/), créer une stratégie de sécurité qui ajoute un prédicat sur la table de restreindre les lignes retournés à ceux qui correspond à l’utilisateur de base de données actuel (à l’aide de la CURRENT_USER() la fonction intégrée) ou le nom de connexion actuel (à l’aide de la fonction intégrée SUSER_SNAME()) :</span><span class="sxs-lookup"><span data-stu-id="ed32a-116">If you are using SQL Server 2016 or higher, or [Azure SQL Database](https://docs.microsoft.com/azure/sql-database/), create a security policy that adds a predicate on the table restricting the rows returned to those that match either the current database user (using the CURRENT_USER() built-in function) or the current login name (using the SUSER_SNAME() built-in function):</span></span>  
  
        ```tsql  
        CREATE SCHEMA Security  
        GO  
  
        CREATE FUNCTION Security.userAccessPredicate(@UserName sysname)  
            RETURNS TABLE  
            WITH SCHEMABINDING  
        AS  
            RETURN SELECT 1 AS accessResult  
            WHERE @UserName = SUSER_SNAME()  
        GO  
  
        CREATE SECURITY POLICY Security.userAccessPolicy  
            ADD FILTER PREDICATE Security.userAccessPredicate(UserName) ON dbo.MyTable,  
            ADD BLOCK PREDICATE Security.userAccessPredicate(UserName) ON dbo.MyTable  
        GO  
        ```  
  
    -   <span data-ttu-id="ed32a-117">Si vous utilisez une version de SQL Server antérieure à 2016, vous pouvez obtenir des fonctionnalités similaires à l’aide d’une vue :</span><span class="sxs-lookup"><span data-stu-id="ed32a-117">If you are using a version of SQL Server prior to 2016, you can achieve similar functionality using a view:</span></span>  
  
        ```tsql  
        CREATE VIEW vw_MyTable  
        AS  
            RETURN SELECT * FROM MyTable  
            WHERE UserName = SUSER_SNAME()  
        GO  
        ```  
  
-   <span data-ttu-id="ed32a-118">Créez des procédures stockées pour sélectionner, insérer, mettre à jour et supprimer des données.</span><span class="sxs-lookup"><span data-stu-id="ed32a-118">Create stored procedures to select, insert, update, and delete data.</span></span> <span data-ttu-id="ed32a-119">Si le filtrage est imposé par une stratégie de sécurité, les procédures stockées doivent effectuer ces opérations directement sur la table de base. Dans le cas contraire, si le filtrage est imposé par une vue, les procédures stockées doivent plutôt fonctionner sur la vue.</span><span class="sxs-lookup"><span data-stu-id="ed32a-119">If the filtering is enacted by a security policy, the stored procedures should perform these operations on the base table directly; otherwise, if the filtering is enacted by a view, the stored procedures should instead operate against the view.</span></span> <span data-ttu-id="ed32a-120">La stratégie de sécurité ou la vue filtre automatiquement les lignes retournées ou modifiées par les requêtes utilisateur, et la procédure stockée fournit une limite de sécurité plus élevée pour empêcher les utilisateurs bénéficiant d’un accès direct aux requêtes d’exécuter des requêtes capables de déduire l’existence des données filtrées.</span><span class="sxs-lookup"><span data-stu-id="ed32a-120">The security policy or view will automatically filter the rows returned or modified by user queries, and the stored procedure will provide a harder security boundary to prevent users with direct query access from successfully running queries that can infer the existence of filtered data.</span></span>  
  
-   <span data-ttu-id="ed32a-121">Pour les procédures stockées qui insèrent des données, capturez le nom d’utilisateur à l’aide de la même fonction que celle spécifiée dans la stratégie de sécurité ou la vue et insérez cette valeur dans la colonne UserName.</span><span class="sxs-lookup"><span data-stu-id="ed32a-121">For stored procedures that insert data, capture the user name using the same function specified in the security policy or view, and insert that value into the UserName column.</span></span>  
  
-   <span data-ttu-id="ed32a-122">Refusez au rôle `public` toutes les autorisations sur les tables (et les vues, le cas échéant).</span><span class="sxs-lookup"><span data-stu-id="ed32a-122">Deny all permissions on the tables (and views, if applicable) to the `public` role.</span></span> <span data-ttu-id="ed32a-123">Les utilisateurs ne peuvent pas hériter des autorisations d’autres rôles de base de données, car le prédicat de filtre repose sur des noms d’utilisateurs ou de connexion, et non sur des rôles.</span><span class="sxs-lookup"><span data-stu-id="ed32a-123">Users will not be able to inherit permissions from other database roles, because the filter predicate is based on user or login names, not on roles.</span></span>  
  
-   <span data-ttu-id="ed32a-124">Accordez aux rôles de base de données l'autorisation EXECUTE sur les procédures stockées.</span><span class="sxs-lookup"><span data-stu-id="ed32a-124">Grant EXECUTE on the stored procedures to database roles.</span></span> <span data-ttu-id="ed32a-125">Les utilisateurs ne peuvent accéder aux données que par le biais des procédures stockées fournies.</span><span class="sxs-lookup"><span data-stu-id="ed32a-125">Users can only access data through the stored procedures provided.</span></span>  
  
## <a name="external-resources"></a><span data-ttu-id="ed32a-126">Ressources externes</span><span class="sxs-lookup"><span data-stu-id="ed32a-126">External Resources</span></span>  
 <span data-ttu-id="ed32a-127">Pour plus d'informations, voir la ressource suivante :</span><span class="sxs-lookup"><span data-stu-id="ed32a-127">For more information, see the following resource.</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="ed32a-128">[Implementing Row- and Cell-Level Security in Classified Databases Using SQL Server 2005](http://go.microsoft.com/fwlink/?LinkId=98227) sur le site SQL Server TechCenter.</span><span class="sxs-lookup"><span data-stu-id="ed32a-128">[Implementing Row- and Cell-Level Security in Classified Databases Using SQL Server 2005](http://go.microsoft.com/fwlink/?LinkId=98227) on the SQL Server TechCenter site.</span></span>|<span data-ttu-id="ed32a-129">Décrit comment utiliser la sécurité de niveau ligne et de niveau cellule pour répondre aux spécifications de sécurité des bases de données confidentielles.</span><span class="sxs-lookup"><span data-stu-id="ed32a-129">Describes how to use row- and cell-level security to meet classified database security requirements.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="ed32a-130">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ed32a-130">See Also</span></span>  
 [<span data-ttu-id="ed32a-131">Sécurité de niveau ligne</span><span class="sxs-lookup"><span data-stu-id="ed32a-131">Row-Level Security</span></span>](https://msdn.microsoft.com/library/dn765131.aspx)  
 [<span data-ttu-id="ed32a-132">Sécurisation des applications ADO.NET</span><span class="sxs-lookup"><span data-stu-id="ed32a-132">Securing ADO.NET Applications</span></span>](../../../../../docs/framework/data/adonet/securing-ado-net-applications.md)  
 [<span data-ttu-id="ed32a-133">Vue d’ensemble de la sécurité SQL Server</span><span class="sxs-lookup"><span data-stu-id="ed32a-133">Overview of SQL Server Security</span></span>](../../../../../docs/framework/data/adonet/sql/overview-of-sql-server-security.md)  
 [<span data-ttu-id="ed32a-134">Scénarios de sécurité dans SQL Server</span><span class="sxs-lookup"><span data-stu-id="ed32a-134">Application Security Scenarios in SQL Server</span></span>](../../../../../docs/framework/data/adonet/sql/application-security-scenarios-in-sql-server.md)  
 [<span data-ttu-id="ed32a-135">La gestion des autorisations avec des procédures stockées dans SQL Server</span><span class="sxs-lookup"><span data-stu-id="ed32a-135">Managing Permissions with Stored Procedures in SQL Server</span></span>](../../../../../docs/framework/data/adonet/sql/managing-permissions-with-stored-procedures-in-sql-server.md)  
 [<span data-ttu-id="ed32a-136">L’écriture SQL dynamique sécurisé dans SQL Server</span><span class="sxs-lookup"><span data-stu-id="ed32a-136">Writing Secure Dynamic SQL in SQL Server</span></span>](../../../../../docs/framework/data/adonet/sql/writing-secure-dynamic-sql-in-sql-server.md)  
 [<span data-ttu-id="ed32a-137">Fournisseurs managés ADO.NET et centre de développement DataSet</span><span class="sxs-lookup"><span data-stu-id="ed32a-137">ADO.NET Managed Providers and DataSet Developer Center</span></span>](http://go.microsoft.com/fwlink/?LinkId=217917)
