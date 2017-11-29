---
title: "Vue d'ensemble de la sécurité SQL Server"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ae66dd75-5c16-4cc0-9e12-774dd26d3fb9
caps.latest.revision: "5"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: d93d077153cd15534175c1e60e63a765ce893c71
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="overview-of-sql-server-security"></a><span data-ttu-id="05e1f-102">Vue d'ensemble de la sécurité SQL Server</span><span class="sxs-lookup"><span data-stu-id="05e1f-102">Overview of SQL Server Security</span></span>
<span data-ttu-id="05e1f-103">Une stratégie de défense en profondeur avec chevauchement des couches de sécurité est le meilleur moyen de contrer les menaces de sécurité.</span><span class="sxs-lookup"><span data-stu-id="05e1f-103">A defense-in-depth strategy, with overlapping layers of security, is the best way to counter security threats.</span></span> <span data-ttu-id="05e1f-104">SQL Server propose une architecture de sécurité conçue pour permettre aux administrateurs et aux développeurs de bases de données de créer des applications de base de données sécurisées et de contrer les menaces.</span><span class="sxs-lookup"><span data-stu-id="05e1f-104">SQL Server provides a security architecture that is designed to allow database administrators and developers to create secure database applications and counter threats.</span></span> <span data-ttu-id="05e1f-105">Chaque version de SQL Server offre des améliorations par rapport aux versions précédentes avec l'introduction de nouvelles fonctions et fonctionnalités.</span><span class="sxs-lookup"><span data-stu-id="05e1f-105">Each version of SQL Server has improved on previous versions of SQL Server with the introduction of new features and functionality.</span></span> <span data-ttu-id="05e1f-106">Pour autant, il ne peut exister de plan de sécurité prêt à l'emploi.</span><span class="sxs-lookup"><span data-stu-id="05e1f-106">However, security does not ship in the box.</span></span> <span data-ttu-id="05e1f-107">Chaque application a des spécifications de sécurité uniques.</span><span class="sxs-lookup"><span data-stu-id="05e1f-107">Each application is unique in its security requirements.</span></span> <span data-ttu-id="05e1f-108">Les développeurs doivent comprendre quelle combinaison de fonctions et fonctionnalités est la plus adéquate pour contrer les menaces identifiées et pour anticiper les menaces qui risquent de voir le jour dans l'avenir.</span><span class="sxs-lookup"><span data-stu-id="05e1f-108">Developers need to understand which combination of features and functionality are most appropriate to counter known threats, and to anticipate threats that may arise in the future.</span></span>  
  
 <span data-ttu-id="05e1f-109">Une instance SQL Server contient une collection hiérarchique d'entités, qui commence par le serveur.</span><span class="sxs-lookup"><span data-stu-id="05e1f-109">A SQL Server instance contains a hierarchical collection of entities, starting with the server.</span></span> <span data-ttu-id="05e1f-110">Chaque serveur contient plusieurs bases de données et chaque base de données contient une collection d’objets sécurisables.</span><span class="sxs-lookup"><span data-stu-id="05e1f-110">Each server contains multiple databases, and each database contains a collection of securable objects.</span></span> <span data-ttu-id="05e1f-111">Chaque élément sécurisable de SQL Server est associé à *autorisations* qui peuvent être accordées à un *principal*, qui est un groupe individuel, ou processus autorisé à accéder à SQL Server.</span><span class="sxs-lookup"><span data-stu-id="05e1f-111">Every SQL Server securable has associated *permissions* that can be granted to a *principal*, which is an individual, group or process granted access to SQL Server.</span></span> <span data-ttu-id="05e1f-112">L’infrastructure de sécurité de SQL Server gère l’accès aux entités sécurisables via *authentification* et *autorisation*.</span><span class="sxs-lookup"><span data-stu-id="05e1f-112">The SQL Server security framework manages access to securable entities through *authentication* and *authorization*.</span></span>  
  
-   <span data-ttu-id="05e1f-113">L'authentification est le processus de connexion à SQL Server dans lequel une principal de sécurité demande l'accès en soumettant des informations d'identification qui sont évaluées par le serveur.</span><span class="sxs-lookup"><span data-stu-id="05e1f-113">Authentication is the process of logging on to SQL Server by which a principal requests access by submitting credentials that the server evaluates.</span></span> <span data-ttu-id="05e1f-114">L'authentification établit l'identité de l'utilisateur ou du processus en cours d'authentification.</span><span class="sxs-lookup"><span data-stu-id="05e1f-114">Authentication establishes the identity of the user or process being authenticated.</span></span>  
  
-   <span data-ttu-id="05e1f-115">L'autorisation est le processus consistant à déterminer les ressources sécurisables auxquelles une principal de sécurité peut accéder et les opérations qui sont autorisées pour ces ressources.</span><span class="sxs-lookup"><span data-stu-id="05e1f-115">Authorization is the process of determining which securable resources a principal can access, and which operations are allowed for those resources.</span></span>  
  
 <span data-ttu-id="05e1f-116">Les rubriques de cette section présentent les concepts fondamentaux de la sécurité SQL Server et fournissent des liens vers la version appropriée de la documentation complète en ligne de SQL Server.</span><span class="sxs-lookup"><span data-stu-id="05e1f-116">The topics in this section cover SQL Server security fundamentals, providing links to the complete documentation in the relevant version of SQL Server Books Online.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="05e1f-117">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="05e1f-117">In This Section</span></span>  
 [<span data-ttu-id="05e1f-118">Authentification dans SQL Server</span><span class="sxs-lookup"><span data-stu-id="05e1f-118">Authentication in SQL Server</span></span>](../../../../../docs/framework/data/adonet/sql/authentication-in-sql-server.md)  
 <span data-ttu-id="05e1f-119">Décrit les connexions et l'authentification dans SQL Server et fournit des liens vers des ressources supplémentaires.</span><span class="sxs-lookup"><span data-stu-id="05e1f-119">Describes logins and authentication in SQL Server and provides links to additional resources.</span></span>  
  
 [<span data-ttu-id="05e1f-120">Rôles de serveur et base de données dans SQL Server</span><span class="sxs-lookup"><span data-stu-id="05e1f-120">Server and Database Roles in SQL Server</span></span>](../../../../../docs/framework/data/adonet/sql/server-and-database-roles-in-sql-server.md)  
 <span data-ttu-id="05e1f-121">Décrit le rôle serveur fixe et le rôle de base de données fixe, les rôles de base de données personnalisés et les comptes intégrés, et fournit des liens vers des ressources supplémentaires.</span><span class="sxs-lookup"><span data-stu-id="05e1f-121">Describes fixed server and database roles, custom database roles, and built-in accounts and provides links to additional resources.</span></span>  
  
 [<span data-ttu-id="05e1f-122">La propriété et séparation utilisateur-schéma dans SQL Server</span><span class="sxs-lookup"><span data-stu-id="05e1f-122">Ownership and User-Schema Separation in SQL Server</span></span>](../../../../../docs/framework/data/adonet/sql/ownership-and-user-schema-separation-in-sql-server.md)  
 <span data-ttu-id="05e1f-123">Décrit la propriété d'objet et la séparation utilisateur-schéma, et fournit des liens vers des ressources supplémentaires.</span><span class="sxs-lookup"><span data-stu-id="05e1f-123">Describes object ownership and  user-schema separation and provides links to additional resources.</span></span>  
  
 [<span data-ttu-id="05e1f-124">Autorisations dans SQL Server</span><span class="sxs-lookup"><span data-stu-id="05e1f-124">Authorization and Permissions in SQL Server</span></span>](../../../../../docs/framework/data/adonet/sql/authorization-and-permissions-in-sql-server.md)  
 <span data-ttu-id="05e1f-125">Décrit l'octroi d'autorisations selon le principe des privilèges minimum et fournit des liens vers des ressources supplémentaires.</span><span class="sxs-lookup"><span data-stu-id="05e1f-125">Describes granting permissions using the principle of least privilege and provides links to additional resources.</span></span>  
  
 [<span data-ttu-id="05e1f-126">Chiffrement des données dans SQL Server</span><span class="sxs-lookup"><span data-stu-id="05e1f-126">Data Encryption in SQL Server</span></span>](../../../../../docs/framework/data/adonet/sql/data-encryption-in-sql-server.md)  
 <span data-ttu-id="05e1f-127">Décrit les options de chiffrement de données dans SQL Server et fournit des liens vers des ressources supplémentaires.</span><span class="sxs-lookup"><span data-stu-id="05e1f-127">Describes data encryption options in SQL Server and provides links to additional resources.</span></span>  
  
 [<span data-ttu-id="05e1f-128">Sécurité de l’intégration CLR dans SQL Server</span><span class="sxs-lookup"><span data-stu-id="05e1f-128">CLR Integration Security in SQL Server</span></span>](../../../../../docs/framework/data/adonet/sql/clr-integration-security-in-sql-server.md)  
 <span data-ttu-id="05e1f-129">Fournit des liens vers les ressources de sécurité d'intégration de CLR.</span><span class="sxs-lookup"><span data-stu-id="05e1f-129">Provides links to CLR integration security resources.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="05e1f-130">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="05e1f-130">See Also</span></span>  
 [<span data-ttu-id="05e1f-131">Sécurisation des applications ADO.NET</span><span class="sxs-lookup"><span data-stu-id="05e1f-131">Securing ADO.NET Applications</span></span>](../../../../../docs/framework/data/adonet/securing-ado-net-applications.md)  
 [<span data-ttu-id="05e1f-132">Sécurité SQL Server</span><span class="sxs-lookup"><span data-stu-id="05e1f-132">SQL Server Security</span></span>](../../../../../docs/framework/data/adonet/sql/sql-server-security.md)  
 [<span data-ttu-id="05e1f-133">Scénarios de sécurité dans SQL Server</span><span class="sxs-lookup"><span data-stu-id="05e1f-133">Application Security Scenarios in SQL Server</span></span>](../../../../../docs/framework/data/adonet/sql/application-security-scenarios-in-sql-server.md)  
 [<span data-ttu-id="05e1f-134">Fournisseurs managés ADO.NET et centre de développement DataSet</span><span class="sxs-lookup"><span data-stu-id="05e1f-134">ADO.NET Managed Providers and DataSet Developer Center</span></span>](http://go.microsoft.com/fwlink/?LinkId=217917)
