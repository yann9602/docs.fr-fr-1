---
title: "Propriété et séparation des schémas utilisateur dans SQL Server"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 242830c1-31b5-4427-828c-cc22ff339f30
caps.latest.revision: "6"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 168eaf9bc0bbac80cbd1e2bb0538aab89d262a49
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="ownership-and-user-schema-separation-in-sql-server"></a><span data-ttu-id="78d8a-102">Propriété et séparation des schémas utilisateur dans SQL Server</span><span class="sxs-lookup"><span data-stu-id="78d8a-102">Ownership and User-Schema Separation in SQL Server</span></span>
<span data-ttu-id="78d8a-103">Il existe un concept essentiel relative à la sécurité de SQL Server, selon lequel les propriétaires d'objets disposent d'autorisations irrévocables pour les administrer.</span><span class="sxs-lookup"><span data-stu-id="78d8a-103">A core concept of SQL Server security is that owners of objects have irrevocable permissions to administer them.</span></span> <span data-ttu-id="78d8a-104">Vous ne pouvez pas supprimer les privilèges d'un propriétaire d'objets et vous ne pouvez pas supprimer des utilisateurs d'une base de données dans laquelle se trouvent des objets qui leur appartiennent.</span><span class="sxs-lookup"><span data-stu-id="78d8a-104">You cannot remove privileges from an object owner, and you cannot drop users from a database if they own objects in it.</span></span>  
  
## <a name="user-schema-separation"></a><span data-ttu-id="78d8a-105">Séparation utilisateur-schéma</span><span class="sxs-lookup"><span data-stu-id="78d8a-105">User-Schema Separation</span></span>  
 <span data-ttu-id="78d8a-106">La séparation utilisateur-schéma permet plus de souplesse dans la gestion des autorisations d'objet de base de données.</span><span class="sxs-lookup"><span data-stu-id="78d8a-106">User-schema separation allows for more flexibility in managing database object permissions.</span></span> <span data-ttu-id="78d8a-107">A *schéma* est un conteneur nommé pour les objets de base de données, qui vous permet de grouper des objets dans les espaces de noms distincts.</span><span class="sxs-lookup"><span data-stu-id="78d8a-107">A *schema* is a named container for database objects, which allows you to group objects into separate namespaces.</span></span> <span data-ttu-id="78d8a-108">Par exemple, l'exemple de base de données AdventureWorks contient des schémas pour Production, Sales et HumanResources.</span><span class="sxs-lookup"><span data-stu-id="78d8a-108">For example, the AdventureWorks sample database contains schemas for Production, Sales, and HumanResources.</span></span>  
  
 <span data-ttu-id="78d8a-109">La syntaxe de dénomination en quatre parties destinée à faire référence à des objets spécifie le nom de schéma.</span><span class="sxs-lookup"><span data-stu-id="78d8a-109">The four-part naming syntax for referring to objects specifies the schema name.</span></span>  
  
```  
Server.Database.DatabaseSchema.DatabaseObject  
```  
  
### <a name="schema-owners-and-permissions"></a><span data-ttu-id="78d8a-110">Propriétaires et autorisations de schéma</span><span class="sxs-lookup"><span data-stu-id="78d8a-110">Schema Owners and Permissions</span></span>  
 <span data-ttu-id="78d8a-111">Les schémas peuvent appartenir à n'importe quelle principal de sécurité de base de données, tandis qu'une principal de sécurité unique peut posséder plusieurs schémas.</span><span class="sxs-lookup"><span data-stu-id="78d8a-111">Schemas can be owned by any database principal, and a single principal can own multiple schemas.</span></span> <span data-ttu-id="78d8a-112">Vous pouvez appliquer des règles de sécurité à un schéma, dont hériteront tous les objets du schéma.</span><span class="sxs-lookup"><span data-stu-id="78d8a-112">You can apply security rules to a schema, which are inherited by all objects in the schema.</span></span> <span data-ttu-id="78d8a-113">Une fois que vous avez défini des autorisations d'accès pour un schéma, elles sont automatiquement appliquées lors de l'ajout de nouveaux objets au schéma.</span><span class="sxs-lookup"><span data-stu-id="78d8a-113">Once you set up access permissions for a schema, those permissions are automatically applied as new objects are added to the schema.</span></span> <span data-ttu-id="78d8a-114">Un schéma par défaut peut être affecté aux utilisateurs, et plusieurs utilisateurs de base de données peuvent partager le même schéma.</span><span class="sxs-lookup"><span data-stu-id="78d8a-114">Users can be assigned a default schema, and multiple database users can share the same schema.</span></span>  
  
 <span data-ttu-id="78d8a-115">Par défaut, lorsque des développeurs créent des objets dans un schéma, ces objets appartiennent à la principal de sécurité qui possède le schéma, et non aux développeurs.</span><span class="sxs-lookup"><span data-stu-id="78d8a-115">By default, when developers create objects in a schema, the objects are owned by the security principal that owns the schema, not the developer.</span></span> <span data-ttu-id="78d8a-116">La propriété d'objet peut être transférée avec l'instruction Transact-SQL ALTER AUTHORIZATION.</span><span class="sxs-lookup"><span data-stu-id="78d8a-116">Object ownership can be transferred with ALTER AUTHORIZATION Transact-SQL statement.</span></span> <span data-ttu-id="78d8a-117">Un schéma peut également contenir des objets qui appartiennent à différents utilisateurs et disposent d'autorisations plus précises que celles affectées au schéma, même si cela n'est pas recommandé car la gestion des autorisations devient alors plus complexe.</span><span class="sxs-lookup"><span data-stu-id="78d8a-117">A schema can also contain objects that are owned by different users and have more granular permissions than those assigned to the schema, although this is not recommended because it adds complexity to managing permissions.</span></span> <span data-ttu-id="78d8a-118">Les objets peuvent être déplacés entre plusieurs schémas et la propriété de schéma peut être transférée entre plusieurs entités.</span><span class="sxs-lookup"><span data-stu-id="78d8a-118">Objects can be moved between schemas, and schema ownership can be transferred between principals.</span></span> <span data-ttu-id="78d8a-119">Les utilisateurs de base de données peuvent être supprimés sans affecter les schémas.</span><span class="sxs-lookup"><span data-stu-id="78d8a-119">Database users can be dropped without affecting schemas.</span></span>  
  
### <a name="built-in-schemas"></a><span data-ttu-id="78d8a-120">Schémas intégrés</span><span class="sxs-lookup"><span data-stu-id="78d8a-120">Built-In Schemas</span></span>  
 <span data-ttu-id="78d8a-121">SQL Server est livré avec six schémas prédéfinis qui possèdent les mêmes noms que les utilisateurs et les rôles de base de données intégrés.</span><span class="sxs-lookup"><span data-stu-id="78d8a-121">SQL Server ships with ten pre-defined schemas that have the same names as the built-in database users and roles.</span></span> <span data-ttu-id="78d8a-122">Ils sont principalement destinés à la compatibilité descendante.</span><span class="sxs-lookup"><span data-stu-id="78d8a-122">These exist mainly for backward compatibility.</span></span> <span data-ttu-id="78d8a-123">Vous pouvez supprimer les schémas qui possèdent les mêmes noms que ceux des rôles de base de données fixes si vous n'en avez pas besoin.</span><span class="sxs-lookup"><span data-stu-id="78d8a-123">You can drop the schemas that have the same names as the fixed database roles if you do not need them.</span></span> <span data-ttu-id="78d8a-124">Par contre, vous ne pouvez pas supprimer les schémas suivants :</span><span class="sxs-lookup"><span data-stu-id="78d8a-124">You cannot drop the following schemas:</span></span>  
  
-   `dbo`  
  
-   `guest`  
  
-   `sys`  
  
-   `INFORMATION_SCHEMA`  
  
 <span data-ttu-id="78d8a-125">Si vous les supprimez de la base de données model, ils n'apparaîtront pas dans les nouvelles bases de données.</span><span class="sxs-lookup"><span data-stu-id="78d8a-125">If you drop them from the model database, they will not appear in new databases.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="78d8a-126">Les schémas `sys` et `INFORMATION_SCHEMA` sont réservés pour les objets système.</span><span class="sxs-lookup"><span data-stu-id="78d8a-126">The `sys` and `INFORMATION_SCHEMA` schemas are reserved for system objects.</span></span> <span data-ttu-id="78d8a-127">Vous ne pouvez pas créer d'objets dans ces schémas et vous ne pouvez pas les supprimer.</span><span class="sxs-lookup"><span data-stu-id="78d8a-127">You cannot create objects in these schemas and you cannot drop them.</span></span>  
  
#### <a name="the-dbo-schema"></a><span data-ttu-id="78d8a-128">Schéma dbo</span><span class="sxs-lookup"><span data-stu-id="78d8a-128">The dbo Schema</span></span>  
 <span data-ttu-id="78d8a-129">Le schéma `dbo` constitue le schéma par défaut d'une base de données qui vient d'être créée.</span><span class="sxs-lookup"><span data-stu-id="78d8a-129">The `dbo` schema is the default schema for a newly created database.</span></span> <span data-ttu-id="78d8a-130">Le schéma `dbo` appartient au compte d'utilisateur `dbo`.</span><span class="sxs-lookup"><span data-stu-id="78d8a-130">The `dbo` schema is owned by the `dbo` user account.</span></span> <span data-ttu-id="78d8a-131">Par défaut, les utilisateurs créés avec la commande Transact-SQL CREATE USER ont `dbo` en tant que schéma par défaut.</span><span class="sxs-lookup"><span data-stu-id="78d8a-131">By default, users created with the CREATE USER Transact-SQL command have `dbo` as their default schema.</span></span>  
  
 <span data-ttu-id="78d8a-132">Les utilisateurs à qui est affecté le schéma `dbo` n'héritent pas des autorisations du compte d'utilisateur `dbo`.</span><span class="sxs-lookup"><span data-stu-id="78d8a-132">Users who are assigned the `dbo` schema do not inherit the permissions of the `dbo` user account.</span></span> <span data-ttu-id="78d8a-133">Les utilisateurs n'héritent d'aucune autorisation provenant d'un schéma. En effet, ce sont les objets de base de données contenus dans le schéma qui héritent des autorisations du schéma.</span><span class="sxs-lookup"><span data-stu-id="78d8a-133">No permissions are inherited from a schema by users; schema permissions are inherited by the database objects contained in the schema.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="78d8a-134">Lorsque des objets de base de données sont référencés à l'aide d'un nom en une partie dans SQL Server consulte d'abord le schéma par défaut de l'utilisateur.</span><span class="sxs-lookup"><span data-stu-id="78d8a-134">When database objects are referenced by using a one-part name, SQL Server first looks in the user's default schema.</span></span> <span data-ttu-id="78d8a-135">Si l'objet y est introuvable, SQL Server recherche ensuite dans le schéma `dbo`.</span><span class="sxs-lookup"><span data-stu-id="78d8a-135">If the object is not found there, SQL Server looks next in the `dbo` schema.</span></span> <span data-ttu-id="78d8a-136">Si l'objet ne se trouve pas non plus dans le schéma `dbo`, une erreur est retournée.</span><span class="sxs-lookup"><span data-stu-id="78d8a-136">If the object is not in the `dbo` schema, an error is returned.</span></span>  
  
## <a name="external-resources"></a><span data-ttu-id="78d8a-137">Ressources externes</span><span class="sxs-lookup"><span data-stu-id="78d8a-137">External Resources</span></span>  
 <span data-ttu-id="78d8a-138">Pour plus d'informations sur la propriété d'objet et les schémas, voir les ressources suivantes.</span><span class="sxs-lookup"><span data-stu-id="78d8a-138">For more information on object ownership and schemas, see the following resources.</span></span>  
  
|<span data-ttu-id="78d8a-139">Ressource</span><span class="sxs-lookup"><span data-stu-id="78d8a-139">Resource</span></span>|<span data-ttu-id="78d8a-140">Description</span><span class="sxs-lookup"><span data-stu-id="78d8a-140">Description</span></span>|  
|--------------|-----------------|  
|<span data-ttu-id="78d8a-141">[Séparation utilisateur-schéma](http://msdn.microsoft.com/library/ms190387.aspx) dans la documentation en ligne de SQL Server</span><span class="sxs-lookup"><span data-stu-id="78d8a-141">[User-Schema Separation](http://msdn.microsoft.com/library/ms190387.aspx) in SQL Server Books Online</span></span>|<span data-ttu-id="78d8a-142">Décrit les modifications introduites par la séparation utilisateur-schéma.</span><span class="sxs-lookup"><span data-stu-id="78d8a-142">Describes the changes introduced by user-schema separation.</span></span> <span data-ttu-id="78d8a-143">Inclut un nouveau comportement, son impact sur la propriété, des affichages catalogue et des autorisations.</span><span class="sxs-lookup"><span data-stu-id="78d8a-143">Includes new behavior, its impact on ownership, catalog views, and permissions.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="78d8a-144">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="78d8a-144">See Also</span></span>  
 [<span data-ttu-id="78d8a-145">Sécurisation des applications ADO.NET</span><span class="sxs-lookup"><span data-stu-id="78d8a-145">Securing ADO.NET Applications</span></span>](../../../../../docs/framework/data/adonet/securing-ado-net-applications.md)  
 [<span data-ttu-id="78d8a-146">Scénarios de sécurité dans SQL Server</span><span class="sxs-lookup"><span data-stu-id="78d8a-146">Application Security Scenarios in SQL Server</span></span>](../../../../../docs/framework/data/adonet/sql/application-security-scenarios-in-sql-server.md)  
 [<span data-ttu-id="78d8a-147">Authentification dans SQL Server</span><span class="sxs-lookup"><span data-stu-id="78d8a-147">Authentication in SQL Server</span></span>](../../../../../docs/framework/data/adonet/sql/authentication-in-sql-server.md)  
 [<span data-ttu-id="78d8a-148">Rôles de serveur et base de données dans SQL Server</span><span class="sxs-lookup"><span data-stu-id="78d8a-148">Server and Database Roles in SQL Server</span></span>](../../../../../docs/framework/data/adonet/sql/server-and-database-roles-in-sql-server.md)  
 [<span data-ttu-id="78d8a-149">Autorisations dans SQL Server</span><span class="sxs-lookup"><span data-stu-id="78d8a-149">Authorization and Permissions in SQL Server</span></span>](../../../../../docs/framework/data/adonet/sql/authorization-and-permissions-in-sql-server.md)  
 [<span data-ttu-id="78d8a-150">Fournisseurs managés ADO.NET et centre de développement DataSet</span><span class="sxs-lookup"><span data-stu-id="78d8a-150">ADO.NET Managed Providers and DataSet Developer Center</span></span>](http://go.microsoft.com/fwlink/?LinkId=217917)
