---
title: "Chaînes de connexion dans ADO.NET"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 745c5f95-2f02-4674-b378-6d51a7ec2490
caps.latest.revision: "4"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: a20061c551f5cb1a19c64a2f92b8180465f58eb2
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="connection-strings-in-adonet"></a><span data-ttu-id="57608-102">Chaînes de connexion dans ADO.NET</span><span class="sxs-lookup"><span data-stu-id="57608-102">Connection Strings in ADO.NET</span></span>
<span data-ttu-id="57608-103">Le .NET Framework 2.0 a introduit de nouvelles fonctionnalités permettant d'utiliser des chaînes de connexion, y compris l'intégration de nouveaux mots clés aux classes de générateur de chaînes de connexion, qui facilitent la création de chaînes de connexion valides au moment de l'exécution.</span><span class="sxs-lookup"><span data-stu-id="57608-103">The .NET Framework 2.0 introduced new capabilities for working with connection strings, including the introduction of new keywords to the connection string builder classes, which facilitate creating valid connection strings at run time.</span></span>  
  
 <span data-ttu-id="57608-104">Une chaîne de connexion contient des informations d'initialisation qui sont passées en tant que paramètre d'un fournisseur de données à une source de données.</span><span class="sxs-lookup"><span data-stu-id="57608-104">A connection string contains initialization information that is passed as a parameter from a data provider to a data source.</span></span> <span data-ttu-id="57608-105">La syntaxe dépend du fournisseur de données et la chaîne de connexion est analysée lors de la tentative d'ouverture d'une connexion.</span><span class="sxs-lookup"><span data-stu-id="57608-105">The syntax depends on the data provider, and the connection string is parsed during the attempt to open a connection.</span></span> <span data-ttu-id="57608-106">Des erreurs de syntaxe génèrent une exception runtime mais d'autres erreurs ne se produisent qu'après que la source de données a reçu des informations de connexion.</span><span class="sxs-lookup"><span data-stu-id="57608-106">Syntax errors generate a run-time exception, but other errors occur only after the data source receives connection information.</span></span> <span data-ttu-id="57608-107">Une fois validée, la source de données applique les options spécifiées dans la chaîne de connexion et ouvre la connexion.</span><span class="sxs-lookup"><span data-stu-id="57608-107">Once validated, the data source applies the options specified in the connection string and opens the connection.</span></span>  
  
 <span data-ttu-id="57608-108">Le format d'une chaîne de connexion est une liste délimitée par des points-virgules de paires de paramètres clé/valeur :</span><span class="sxs-lookup"><span data-stu-id="57608-108">The format of a connection string is a semicolon-delimited list of key/value parameter pairs:</span></span>  
  
 `keyword1=value; keyword2=value;`  
  
 <span data-ttu-id="57608-109">Les mots clés ne respectent pas la casse et les espaces entre les paires clé/valeur sont ignorés.</span><span class="sxs-lookup"><span data-stu-id="57608-109">Keywords are not case sensitive, and spaces between key/value pairs are ignored.</span></span> <span data-ttu-id="57608-110">Toutefois, des valeurs peuvent respecter la casse, en fonction de la source de données.</span><span class="sxs-lookup"><span data-stu-id="57608-110">However, values may be case sensitive, depending on the data source.</span></span> <span data-ttu-id="57608-111">Toute valeur contenant un point-virgule ou des guillemets simples ou doubles doit être placée entre des guillemets doubles.</span><span class="sxs-lookup"><span data-stu-id="57608-111">Any values containing a semicolon, single quotation marks, or double quotation marks must be enclosed in double quotation marks.</span></span>  
  
 <span data-ttu-id="57608-112">La syntaxe de chaîne de connexion valide dépend du fournisseur et a évolué au fil des ans, par rapport aux premières API, telles qu'ODBC.</span><span class="sxs-lookup"><span data-stu-id="57608-112">Valid connection string syntax depends on the provider, and has evolved over the years from earlier APIs like ODBC.</span></span> <span data-ttu-id="57608-113">Le fournisseur de données .NET Framework pour SQL Server (SqlClient) incorpore de nombreux éléments d'une syntaxe plus ancienne et se montre généralement plus souple avec une syntaxe de chaîne de connexion ordinaire.</span><span class="sxs-lookup"><span data-stu-id="57608-113">The .NET Framework Data Provider for SQL Server (SqlClient) incorporates many elements from older syntax and is generally more flexible with common connection string syntax.</span></span> <span data-ttu-id="57608-114">Des synonymes tout aussi valides d'éléments de syntaxe de chaîne de connexion se rencontrent fréquemment, mais certaines erreurs de syntaxe et d'orthographe peuvent poser des problèmes.</span><span class="sxs-lookup"><span data-stu-id="57608-114">There are frequently equally valid synonyms for connection string syntax elements, but some syntax and spelling errors can cause problems.</span></span> <span data-ttu-id="57608-115">Par exemple, "`Integrated Security=true`" est valide, tandis que "`IntegratedSecurity=true`" provoque une erreur.</span><span class="sxs-lookup"><span data-stu-id="57608-115">For example, "`Integrated Security=true`" is valid, whereas "`IntegratedSecurity=true`" causes an error.</span></span> <span data-ttu-id="57608-116">Par ailleurs, les chaînes de connexion générées au moment de l'exécution à partir d'une entrée utilisateur non validée peuvent entraîner des attaques par injection de chaîne, ce qui compromet la sécurité au niveau de la source de données.</span><span class="sxs-lookup"><span data-stu-id="57608-116">In addition, connection strings constructed at run time from unvalidated user input can lead to string injection attacks, jeopardizing security at the data source.</span></span>  
  
 <span data-ttu-id="57608-117">Pour résoudre ces problèmes, ADO.NET 2.0 a introduit de nouveaux générateurs de chaînes de connexion pour chaque fournisseur de données .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="57608-117">To address these problems, ADO.NET 2.0 introduced new connection string builders for each .NET Framework data provider.</span></span> <span data-ttu-id="57608-118">Les mots clés son exposés en tant que propriétés, ce qui permet de valider la syntaxe de chaîne de connexion avant de la soumettre à la source de données.</span><span class="sxs-lookup"><span data-stu-id="57608-118">Keywords are exposed as properties, enabling connection string syntax to be validated before submission to the data source.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="57608-119">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="57608-119">In This Section</span></span>  
 [<span data-ttu-id="57608-120">Générateurs de chaînes de connexion</span><span class="sxs-lookup"><span data-stu-id="57608-120">Connection String Builders</span></span>](../../../../docs/framework/data/adonet/connection-string-builders.md)  
 <span data-ttu-id="57608-121">Montre comment utiliser les classes `ConnectionStringBuilder` pour générer des chaînes de connexion valides au moment de l'exécution.</span><span class="sxs-lookup"><span data-stu-id="57608-121">Demonstrates how to use the `ConnectionStringBuilder` classes to construct valid connection strings at run time.</span></span>  
  
 [<span data-ttu-id="57608-122">Chaînes de connexion et fichiers de configuration</span><span class="sxs-lookup"><span data-stu-id="57608-122">Connection Strings and Configuration Files</span></span>](../../../../docs/framework/data/adonet/connection-strings-and-configuration-files.md)  
 <span data-ttu-id="57608-123">Montre comment stocker et extraire des chaînes de connexion dans des fichiers de configuration.</span><span class="sxs-lookup"><span data-stu-id="57608-123">Demonstrates how to store and retrieve connection strings in configuration files.</span></span>  
  
 [<span data-ttu-id="57608-124">Syntaxe des chaînes de connexion</span><span class="sxs-lookup"><span data-stu-id="57608-124">Connection String Syntax</span></span>](../../../../docs/framework/data/adonet/connection-string-syntax.md)  
 <span data-ttu-id="57608-125">Décrit comment configurer des chaînes de connexion spécifiques au fournisseur pour `SqlClient`, `OracleClient`, `OleDb` et `Odbc`.</span><span class="sxs-lookup"><span data-stu-id="57608-125">Describes how to configure provider-specific connection strings for `SqlClient`, `OracleClient`, `OleDb`, and `Odbc`.</span></span>  
  
 [<span data-ttu-id="57608-126">Protection des informations de connexion</span><span class="sxs-lookup"><span data-stu-id="57608-126">Protecting Connection Information</span></span>](../../../../docs/framework/data/adonet/protecting-connection-information.md)  
 <span data-ttu-id="57608-127">Montre des techniques pour la protection des informations utilisées pour la connexion à une source de données.</span><span class="sxs-lookup"><span data-stu-id="57608-127">Demonstrates techniques for protecting information used to connect to a data source.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="57608-128">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="57608-128">See Also</span></span>  
 [<span data-ttu-id="57608-129">Connexion à une source de données</span><span class="sxs-lookup"><span data-stu-id="57608-129">Connecting to a Data Source</span></span>](/cpp/data/odbc/connecting-to-a-data-source)  
 [<span data-ttu-id="57608-130">Fournisseurs managés ADO.NET et centre de développement DataSet</span><span class="sxs-lookup"><span data-stu-id="57608-130">ADO.NET Managed Providers and DataSet Developer Center</span></span>](http://go.microsoft.com/fwlink/?LinkId=217917)
