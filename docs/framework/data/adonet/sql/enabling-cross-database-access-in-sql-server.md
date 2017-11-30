---
title: "Activation de l'accès entre bases de données dans SQL Server"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 10663fb6-434c-4c81-8178-ec894b9cf895
caps.latest.revision: "10"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 720c4c8eecc20b971eb9ecf1abb85da1e72e3c54
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="enabling-cross-database-access-in-sql-server"></a><span data-ttu-id="6a941-102">Activation de l'accès entre bases de données dans SQL Server</span><span class="sxs-lookup"><span data-stu-id="6a941-102">Enabling Cross-Database Access in SQL Server</span></span>
<span data-ttu-id="6a941-103">Le chaînage des propriétés des bases de données croisées se produit lorsqu'une procédure dans une base de données repose sur des objets appartenant à une autre base de données.</span><span class="sxs-lookup"><span data-stu-id="6a941-103">Cross-database ownership chaining occurs when a procedure in one database depends on objects in another database.</span></span> <span data-ttu-id="6a941-104">La chaîne des propriétés des bases de données croisées fonctionne de la même manière que le chaînage des propriétés dans une seule base de données, sauf qu'une chaîne de propriétés continue nécessite le mappage de tous les propriétaires d'objets au même compte de connexion.</span><span class="sxs-lookup"><span data-stu-id="6a941-104">A cross-database ownership chain works in the same way as ownership chaining within a single database, except that an unbroken ownership chain requires that all the object owners are mapped to the same login account.</span></span> <span data-ttu-id="6a941-105">Si l'objet source de la base de données source et les objets cibles des bases de données cibles appartiennent au même compte de connexion, SQL Server ne vérifie pas les autorisations sur les objets cibles.</span><span class="sxs-lookup"><span data-stu-id="6a941-105">If the source object in the source database and the target objects in the target databases are owned by the same login account, SQL Server does not check permissions on the target objects.</span></span>  
  
## <a name="off-by-default"></a><span data-ttu-id="6a941-106">Désactivé par défaut</span><span class="sxs-lookup"><span data-stu-id="6a941-106">Off By Default</span></span>  
 <span data-ttu-id="6a941-107">Le chaînage des propriétés des bases de données est désactivé par défaut.</span><span class="sxs-lookup"><span data-stu-id="6a941-107">Ownership chaining across databases is turned off by default.</span></span> <span data-ttu-id="6a941-108">Microsoft vous recommande de désactiver le chaînage des propriétés des bases de données croisées, car il vous expose aux risques de sécurité suivants :</span><span class="sxs-lookup"><span data-stu-id="6a941-108">Microsoft recommends that you disable cross-database ownership chaining because it exposes you to the following security risks:</span></span>  
  
-   <span data-ttu-id="6a941-109">Les propriétaires et les membres de base de données des rôles de base de données `db_ddladmin` ou `db_owners` peuvent créer des objets appartenant à d'autres utilisateurs.</span><span class="sxs-lookup"><span data-stu-id="6a941-109">Database owners and members of the `db_ddladmin` or the `db_owners` database roles can create objects that are owned by other users.</span></span> <span data-ttu-id="6a941-110">Ces objets peuvent potentiellement viser des objets dans d'autres bases de données.</span><span class="sxs-lookup"><span data-stu-id="6a941-110">These objects can potentially target objects in other databases.</span></span> <span data-ttu-id="6a941-111">Cela signifie que si vous activez le chaînage des propriétés des bases de données croisées, vous devez faire totalement confiance aux utilisateurs dans toutes les bases de données.</span><span class="sxs-lookup"><span data-stu-id="6a941-111">This means that if you enable cross-database ownership chaining, you must fully trust these users with data in all databases.</span></span>  
  
-   <span data-ttu-id="6a941-112">Les utilisateurs avec l'autorisation CREATE DATABASE peuvent créer de nouvelles bases de données et attacher les bases de données existantes.</span><span class="sxs-lookup"><span data-stu-id="6a941-112">Users with CREATE DATABASE permission can create new databases and attach existing databases.</span></span> <span data-ttu-id="6a941-113">Si le chaînage des propriétés des bases de données croisées est activé, ces utilisateurs peuvent accéder à des objets dans d'autres bases de données pour lesquels ils n'ont pas de privilèges à partir des bases de données qu'ils ont récemment créées ou attachées. </span><span class="sxs-lookup"><span data-stu-id="6a941-113">If cross-database ownership chaining is enabled, these users can access objects in other databases that they might not have privileges in from the newly created or attached databases that they create.</span></span>  
  
## <a name="enabling-cross-database-ownership-chaining"></a><span data-ttu-id="6a941-114">Activation du chaînage des propriétés des bases de données croisées</span><span class="sxs-lookup"><span data-stu-id="6a941-114">Enabling Cross-database Ownership Chaining</span></span>  
 <span data-ttu-id="6a941-115">L'activation du chaînage des propriétés des bases de données croisées doit être réservée aux environnements dans lesquels vous pouvez faire totalement confiance aux utilisateurs disposant de privilèges élevés.</span><span class="sxs-lookup"><span data-stu-id="6a941-115">Cross-database ownership chaining should only be enabled in environments where you can fully trust highly-privileged users.</span></span> <span data-ttu-id="6a941-116">Vous pouvez configurer l'activation au cours de l'installation pour l'ensemble des bases de données, ou de manière sélective pour des bases de données spécifiques à l'aide des commandes [!INCLUDE[tsql](../../../../../includes/tsql-md.md)] `sp_configure` et `ALTER DATABASE`.</span><span class="sxs-lookup"><span data-stu-id="6a941-116">It can be configured during setup for all databases, or selectively for specific databases using the [!INCLUDE[tsql](../../../../../includes/tsql-md.md)] commands `sp_configure` and `ALTER DATABASE`.</span></span>  
  
 <span data-ttu-id="6a941-117">Pour configurer de manière sélective le chaînage des propriétés des bases de données croisées, utilisez `sp_configure` afin de désactiver cette option pour le serveur.</span><span class="sxs-lookup"><span data-stu-id="6a941-117">To selectively configure cross-database ownership chaining, use `sp_configure` to turn it off for the server.</span></span> <span data-ttu-id="6a941-118">Puis, utilisez la commande ALTER DATABASE avec SET DB_CHAINING ON afin de configurer le chaînage des propriétés des bases de données croisées uniquement pour les bases de données qui le nécessitent.</span><span class="sxs-lookup"><span data-stu-id="6a941-118">Then use the ALTER DATABASE command with SET DB_CHAINING ON to configure cross-database ownership chaining for only the databases that require it.</span></span>  
  
 <span data-ttu-id="6a941-119">L'exemple suivant active le chaînage des propriétés des bases de données pour toutes les bases de données :</span><span class="sxs-lookup"><span data-stu-id="6a941-119">The following sample turns on cross-database ownership chaining for all databases:</span></span>  
  
```  
EXECUTE sp_configure 'show advanced', 1;  
RECONFIGURE;  
EXECUTE sp_configure 'cross db ownership chaining', 1;  
RECONFIGURE;  
```  
  
 <span data-ttu-id="6a941-120">L'exemple suivant active le chaînage des propriétés des bases de données de bases de données spécifiques :</span><span class="sxs-lookup"><span data-stu-id="6a941-120">The following sample turns on cross-database ownership chaining for specific databases:</span></span>  
  
```  
ALTER DATABASE Database1 SET DB_CHAINING ON;  
ALTER DATABASE Database2 SET DB_CHAINING ON;  
```  
  
### <a name="dynamic-sql"></a><span data-ttu-id="6a941-121">Code SQL dynamique</span><span class="sxs-lookup"><span data-stu-id="6a941-121">Dynamic SQL</span></span>  
 <span data-ttu-id="6a941-122">Le chaînage des propriétés des bases de données croisées ne fonctionne pas dans les cas où des instructions SQL créées dynamiquement sont exécutées sauf si le même utilisateur existe dans les deux bases de données.</span><span class="sxs-lookup"><span data-stu-id="6a941-122">Cross-database ownership chaining does not work in cases where dynamically created SQL statements are executed unless the same user exists in both databases.</span></span> <span data-ttu-id="6a941-123">Il est possible de contourner cette restriction dans [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)] en créant une procédure stockée qui accède aux données dans une autre base de données et en signant la procédure avec un certificat qui existe dans les deux bases de données.</span><span class="sxs-lookup"><span data-stu-id="6a941-123">You can work around this in [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)] by creating a stored procedure that accesses data in another database and signing the procedure with a certificate that exists in both databases.</span></span> <span data-ttu-id="6a941-124">De cette manière, les utilisateurs ont accès aux ressources de base de données utilisées par la procédure sans que l'accès ou les autorisations de base de données leur soient octroyés.</span><span class="sxs-lookup"><span data-stu-id="6a941-124">This gives users access to the database resources used by the procedure without granting them database access or permissions.</span></span>  
  
## <a name="external-resources"></a><span data-ttu-id="6a941-125">Ressources externes</span><span class="sxs-lookup"><span data-stu-id="6a941-125">External Resources</span></span>  
 <span data-ttu-id="6a941-126">Pour plus d'informations, voir les ressources ci-dessous.</span><span class="sxs-lookup"><span data-stu-id="6a941-126">For more information, see the following resources.</span></span>  
  
|<span data-ttu-id="6a941-127">Ressource</span><span class="sxs-lookup"><span data-stu-id="6a941-127">Resource</span></span>|<span data-ttu-id="6a941-128">Description</span><span class="sxs-lookup"><span data-stu-id="6a941-128">Description</span></span>|  
|--------------|-----------------|  
|<span data-ttu-id="6a941-129">[Extension de l’emprunt d’identité de base de données à l’aide de EXECUTE AS](http://msdn.microsoft.com/library/ms188304\(SQL.105\).aspx) et [Cross DB Ownership Chaining (Option)](http://msdn.microsoft.com/library/ms188694.aspx) [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)] la documentation en ligne.</span><span class="sxs-lookup"><span data-stu-id="6a941-129">[Extending Database Impersonation by Using EXECUTE AS](http://msdn.microsoft.com/library/ms188304\(SQL.105\).aspx) and [Cross DB Ownership Chaining Option](http://msdn.microsoft.com/library/ms188694.aspx)[!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)] Books Online.</span></span>|<span data-ttu-id="6a941-130">Les rubriques décrivent comment configurer le chaînage des propriétés des bases de données croisées pour une instance de [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="6a941-130">Topics describe how to configure cross-database ownership chaining for an instance of [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)].</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="6a941-131">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="6a941-131">See Also</span></span>  
 [<span data-ttu-id="6a941-132">Sécurisation des applications ADO.NET</span><span class="sxs-lookup"><span data-stu-id="6a941-132">Securing ADO.NET Applications</span></span>](../../../../../docs/framework/data/adonet/securing-ado-net-applications.md)  
 [<span data-ttu-id="6a941-133">Vue d’ensemble de la sécurité SQL Server</span><span class="sxs-lookup"><span data-stu-id="6a941-133">Overview of SQL Server Security</span></span>](../../../../../docs/framework/data/adonet/sql/overview-of-sql-server-security.md)  
 [<span data-ttu-id="6a941-134">La gestion des autorisations avec des procédures stockées dans SQL Server</span><span class="sxs-lookup"><span data-stu-id="6a941-134">Managing Permissions with Stored Procedures in SQL Server</span></span>](../../../../../docs/framework/data/adonet/sql/managing-permissions-with-stored-procedures-in-sql-server.md)  
 [<span data-ttu-id="6a941-135">L’écriture SQL dynamique sécurisé dans SQL Server</span><span class="sxs-lookup"><span data-stu-id="6a941-135">Writing Secure Dynamic SQL in SQL Server</span></span>](../../../../../docs/framework/data/adonet/sql/writing-secure-dynamic-sql-in-sql-server.md)  
 [<span data-ttu-id="6a941-136">Signature de procédures stockées dans SQL Server</span><span class="sxs-lookup"><span data-stu-id="6a941-136">Signing Stored Procedures in SQL Server</span></span>](../../../../../docs/framework/data/adonet/sql/signing-stored-procedures-in-sql-server.md)  
 [<span data-ttu-id="6a941-137">Fournisseurs managés ADO.NET et centre de développement DataSet</span><span class="sxs-lookup"><span data-stu-id="6a941-137">ADO.NET Managed Providers and DataSet Developer Center</span></span>](http://go.microsoft.com/fwlink/?LinkId=217917)
