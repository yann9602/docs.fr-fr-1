---
title: "Sécurité dans LINQ to SQL"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d49787f7-414e-4c71-aa33-80a5895536b1
caps.latest.revision: "2"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: 0ee361c27bd14f0266b2b86f315f9c091e049c12
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/17/2018
---
# <a name="security-in-linq-to-sql"></a><span data-ttu-id="723ed-102">Sécurité dans LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="723ed-102">Security in LINQ to SQL</span></span>
<span data-ttu-id="723ed-103">Les risques de sécurité sont toujours présents lorsque vous vous connectez à une base de données.</span><span class="sxs-lookup"><span data-stu-id="723ed-103">Security risks are always present when you connect to a database.</span></span> <span data-ttu-id="723ed-104">Même si LINQ to SQL inclut de nouvelles méthodes d'utilisation des données dans SQL Server, il ne fournit pas de mécanismes de sécurité supplémentaires.</span><span class="sxs-lookup"><span data-stu-id="723ed-104">Although LINQ to SQL may include some new ways to work with data in SQL Server, it does not provide any additional security mechanisms.</span></span>  
  
## <a name="access-control-and-authentication"></a><span data-ttu-id="723ed-105">Contrôle d'accès et authentification</span><span class="sxs-lookup"><span data-stu-id="723ed-105">Access Control and Authentication</span></span>  
 <span data-ttu-id="723ed-106">LINQ to SQL ne dispose pas de modèle utilisateur ou de mécanismes d'authentification qui lui sont propres.</span><span class="sxs-lookup"><span data-stu-id="723ed-106">LINQ to SQL does not have its own user model or authentication mechanisms.</span></span> <span data-ttu-id="723ed-107">SQL Server Security vous permet de contrôler l'accès à la base de données, aux tables de base de données, aux vues et aux procédures stockées qui sont mappées à votre modèle objet.</span><span class="sxs-lookup"><span data-stu-id="723ed-107">Use SQL Server Security to control access to the database, database tables, views, and stored procedures that are mapped to your object model.</span></span> <span data-ttu-id="723ed-108">Accordez l'accès requis minimal aux utilisateurs et exigez des mots de passe forts pour l'authentification des utilisateurs.</span><span class="sxs-lookup"><span data-stu-id="723ed-108">Grant the minimally required access to users and require strong passwords for user authentication.</span></span>  
  
## <a name="mapping-and-schema-information"></a><span data-ttu-id="723ed-109">Informations de mappage et de schéma</span><span class="sxs-lookup"><span data-stu-id="723ed-109">Mapping and Schema Information</span></span>  
 <span data-ttu-id="723ed-110">Les informations de schéma de base de données et de mappage de type SQL-CLR de votre modèle objet ou fichier de mappage externe sont consultables par tous ceux qui ont accès à ces fichiers via le système de fichiers.</span><span class="sxs-lookup"><span data-stu-id="723ed-110">SQL-CLR type mapping and database schema information in your object model or external mapping file is available for all with access to those files in the file system.</span></span> <span data-ttu-id="723ed-111">Supposons que les informations de schéma sont consultables par tous ceux qui peuvent accéder au modèle objet ou au fichier de mappage externe. Pour éviter un accès plus étendu aux informations de schéma, utilisez des mécanismes de sécurité des fichiers pour sécuriser les fichiers sources et de mappage.</span><span class="sxs-lookup"><span data-stu-id="723ed-111">Assume that schema information will be available to all who can access the object model or external mapping file.To prevent more widespread access to schema information, use file security mechanisms to secure source files and mapping files.</span></span>  
  
## <a name="connection-strings"></a><span data-ttu-id="723ed-112">Chaînes de connexion</span><span class="sxs-lookup"><span data-stu-id="723ed-112">Connection Strings</span></span>  
 <span data-ttu-id="723ed-113">Dans la mesure du possible, vous devez éviter d'utiliser des mots de passe dans les chaînes de connexion.</span><span class="sxs-lookup"><span data-stu-id="723ed-113">Using passwords in connection strings should be avoided whenever possible.</span></span> <span data-ttu-id="723ed-114">Non seulement une chaîne de connexion constitue un risque de sécurité en tant que telle, mais elle peut également être ajoutée en texte clair au modèle objet ou au fichier de mappage externe lors de l'utilisation du Concepteur Objet/Relationnel ou de l'outil de ligne de commande SQLMetal.</span><span class="sxs-lookup"><span data-stu-id="723ed-114">Not only is a connection string a security risk in its own right, but the connection string may also be added in clear text to the object model or external mapping file when using the Object Relational Designer or SQLMetal command-line tool.</span></span> <span data-ttu-id="723ed-115">Toute personne pouvant accéder au modèle objet ou au fichier de mappage externe via le système de fichiers peut visualiser le mot de passe de connexion (s'il est inclus dans la chaîne de connexion).</span><span class="sxs-lookup"><span data-stu-id="723ed-115">Anyone with access to the object model or external mapping file via the file system could see the connection password (if it is included in the connection string).</span></span>  
  
 <span data-ttu-id="723ed-116">Pour réduire de tels risques, utilisez la sécurité intégrée pour effectuer une connexion approuvée avec [!INCLUDE[ssNoVersion](../../../../../../includes/ssnoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="723ed-116">To minimize such risks, use integrated security to make a trusted connection with [!INCLUDE[ssNoVersion](../../../../../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="723ed-117">En utilisant cette approche, vous ne devez pas stocker de mot de passe dans la chaîne de connexion.</span><span class="sxs-lookup"><span data-stu-id="723ed-117">By using this approach, you do not have to store a password in the connection string.</span></span> <span data-ttu-id="723ed-118">Pour plus d’informations, consultez [sécurité SQL Server](../../../../../../docs/framework/data/adonet/sql/sql-server-security.md).</span><span class="sxs-lookup"><span data-stu-id="723ed-118">For more information, see [SQL Server Security](../../../../../../docs/framework/data/adonet/sql/sql-server-security.md).</span></span>  
  
 <span data-ttu-id="723ed-119">En l'absence de sécurité intégrée, un mot de passe en texte clair est nécessaire dans la chaîne de connexion.</span><span class="sxs-lookup"><span data-stu-id="723ed-119">In the absence of integrated security, a clear-text password will be needed in the connection string.</span></span> <span data-ttu-id="723ed-120">La méthode la plus appropriée pour sécuriser votre chaîne de connexion, dans l'ordre croissant de risque, est la suivante :</span><span class="sxs-lookup"><span data-stu-id="723ed-120">The best way to help secure your connection string, in increasing order of risk, is as follows:</span></span>  
  
-   <span data-ttu-id="723ed-121">Utilisez la sécurité intégrée.</span><span class="sxs-lookup"><span data-stu-id="723ed-121">Use integrated security.</span></span>  
  
-   <span data-ttu-id="723ed-122">Sécurisez les chaînes de connexion à l'aide de mots de passe et minimisez l'accès à celles-ci.</span><span class="sxs-lookup"><span data-stu-id="723ed-122">Secure connection strings with passwords and minimize passing around connection strings.</span></span>  
  
-   <span data-ttu-id="723ed-123">Utilisez une classe <xref:System.Data.SqlClient.SqlConnection?displayProperty=nameWithType> au lieu d'une chaîne de connexion car elle limite la durée d'exposition.</span><span class="sxs-lookup"><span data-stu-id="723ed-123">Use a <xref:System.Data.SqlClient.SqlConnection?displayProperty=nameWithType> class instead of a connection string since it limits the duration of exposure.</span></span> <span data-ttu-id="723ed-124">La classe <xref:System.Data.Linq.DataContext?displayProperty=nameWithType> LINQ to SQL peut être instanciée à l'aide d'un objet <xref:System.Data.SqlClient.SqlConnection>.</span><span class="sxs-lookup"><span data-stu-id="723ed-124">The LINQ to SQL <xref:System.Data.Linq.DataContext?displayProperty=nameWithType> class can be instantiated using a <xref:System.Data.SqlClient.SqlConnection>.</span></span>  
  
-   <span data-ttu-id="723ed-125">Minimisez les durées de vie et les points d'accès pour toutes les chaînes de connexion.</span><span class="sxs-lookup"><span data-stu-id="723ed-125">Minimize lifetimes and touch points for all connection strings.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="723ed-126">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="723ed-126">See Also</span></span>  
 [<span data-ttu-id="723ed-127">Informations générales</span><span class="sxs-lookup"><span data-stu-id="723ed-127">Background Information</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/background-information.md)  
 [<span data-ttu-id="723ed-128">Forum Aux Questions</span><span class="sxs-lookup"><span data-stu-id="723ed-128">Frequently Asked Questions</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/frequently-asked-questions.md)
