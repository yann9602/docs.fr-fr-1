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
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: 6737b451a0ccb42dfb83dda487e351a9fafde398
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/17/2018
---
# <a name="connection-strings-in-adonet"></a><span data-ttu-id="71c21-102">Chaînes de connexion dans ADO.NET</span><span class="sxs-lookup"><span data-stu-id="71c21-102">Connection Strings in ADO.NET</span></span>
<span data-ttu-id="71c21-103">Le .NET Framework 2.0 a introduit de nouvelles fonctionnalités permettant d'utiliser des chaînes de connexion, y compris l'intégration de nouveaux mots clés aux classes de générateur de chaînes de connexion, qui facilitent la création de chaînes de connexion valides au moment de l'exécution.</span><span class="sxs-lookup"><span data-stu-id="71c21-103">The .NET Framework 2.0 introduced new capabilities for working with connection strings, including the introduction of new keywords to the connection string builder classes, which facilitate creating valid connection strings at run time.</span></span>  
  
 <span data-ttu-id="71c21-104">Une chaîne de connexion contient des informations d'initialisation qui sont passées en tant que paramètre d'un fournisseur de données à une source de données.</span><span class="sxs-lookup"><span data-stu-id="71c21-104">A connection string contains initialization information that is passed as a parameter from a data provider to a data source.</span></span> <span data-ttu-id="71c21-105">La syntaxe dépend du fournisseur de données et la chaîne de connexion est analysée lors de la tentative d'ouverture d'une connexion.</span><span class="sxs-lookup"><span data-stu-id="71c21-105">The syntax depends on the data provider, and the connection string is parsed during the attempt to open a connection.</span></span> <span data-ttu-id="71c21-106">Des erreurs de syntaxe génèrent une exception runtime mais d'autres erreurs ne se produisent qu'après que la source de données a reçu des informations de connexion.</span><span class="sxs-lookup"><span data-stu-id="71c21-106">Syntax errors generate a run-time exception, but other errors occur only after the data source receives connection information.</span></span> <span data-ttu-id="71c21-107">Une fois validée, la source de données applique les options spécifiées dans la chaîne de connexion et ouvre la connexion.</span><span class="sxs-lookup"><span data-stu-id="71c21-107">Once validated, the data source applies the options specified in the connection string and opens the connection.</span></span>  
  
 <span data-ttu-id="71c21-108">Le format d'une chaîne de connexion est une liste délimitée par des points-virgules de paires de paramètres clé/valeur :</span><span class="sxs-lookup"><span data-stu-id="71c21-108">The format of a connection string is a semicolon-delimited list of key/value parameter pairs:</span></span>  
  
 `keyword1=value; keyword2=value;`  
  
 <span data-ttu-id="71c21-109">Les mots clés ne respectent pas la casse et les espaces entre les paires clé/valeur sont ignorés.</span><span class="sxs-lookup"><span data-stu-id="71c21-109">Keywords are not case sensitive, and spaces between key/value pairs are ignored.</span></span> <span data-ttu-id="71c21-110">Toutefois, des valeurs peuvent respecter la casse, en fonction de la source de données.</span><span class="sxs-lookup"><span data-stu-id="71c21-110">However, values may be case sensitive, depending on the data source.</span></span> <span data-ttu-id="71c21-111">Toute valeur contenant un point-virgule ou des guillemets simples ou doubles doit être placée entre des guillemets doubles.</span><span class="sxs-lookup"><span data-stu-id="71c21-111">Any values containing a semicolon, single quotation marks, or double quotation marks must be enclosed in double quotation marks.</span></span>  
  
 <span data-ttu-id="71c21-112">La syntaxe de chaîne de connexion valide dépend du fournisseur et a évolué au fil des ans, par rapport aux premières API, telles qu'ODBC.</span><span class="sxs-lookup"><span data-stu-id="71c21-112">Valid connection string syntax depends on the provider, and has evolved over the years from earlier APIs like ODBC.</span></span> <span data-ttu-id="71c21-113">Le fournisseur de données .NET Framework pour SQL Server (SqlClient) incorpore de nombreux éléments d'une syntaxe plus ancienne et se montre généralement plus souple avec une syntaxe de chaîne de connexion ordinaire.</span><span class="sxs-lookup"><span data-stu-id="71c21-113">The .NET Framework Data Provider for SQL Server (SqlClient) incorporates many elements from older syntax and is generally more flexible with common connection string syntax.</span></span> <span data-ttu-id="71c21-114">Des synonymes tout aussi valides d'éléments de syntaxe de chaîne de connexion se rencontrent fréquemment, mais certaines erreurs de syntaxe et d'orthographe peuvent poser des problèmes.</span><span class="sxs-lookup"><span data-stu-id="71c21-114">There are frequently equally valid synonyms for connection string syntax elements, but some syntax and spelling errors can cause problems.</span></span> <span data-ttu-id="71c21-115">Par exemple, "`Integrated Security=true`" est valide, tandis que "`IntegratedSecurity=true`" provoque une erreur.</span><span class="sxs-lookup"><span data-stu-id="71c21-115">For example, "`Integrated Security=true`" is valid, whereas "`IntegratedSecurity=true`" causes an error.</span></span> <span data-ttu-id="71c21-116">Par ailleurs, les chaînes de connexion générées au moment de l'exécution à partir d'une entrée utilisateur non validée peuvent entraîner des attaques par injection de chaîne, ce qui compromet la sécurité au niveau de la source de données.</span><span class="sxs-lookup"><span data-stu-id="71c21-116">In addition, connection strings constructed at run time from unvalidated user input can lead to string injection attacks, jeopardizing security at the data source.</span></span>  
  
 <span data-ttu-id="71c21-117">Pour résoudre ces problèmes, ADO.NET 2.0 a introduit de nouveaux générateurs de chaînes de connexion pour chaque fournisseur de données .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="71c21-117">To address these problems, ADO.NET 2.0 introduced new connection string builders for each .NET Framework data provider.</span></span> <span data-ttu-id="71c21-118">Les mots clés son exposés en tant que propriétés, ce qui permet de valider la syntaxe de chaîne de connexion avant de la soumettre à la source de données.</span><span class="sxs-lookup"><span data-stu-id="71c21-118">Keywords are exposed as properties, enabling connection string syntax to be validated before submission to the data source.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="71c21-119">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="71c21-119">In This Section</span></span>  
 [<span data-ttu-id="71c21-120">Générateurs de chaînes de connexion</span><span class="sxs-lookup"><span data-stu-id="71c21-120">Connection String Builders</span></span>](../../../../docs/framework/data/adonet/connection-string-builders.md)  
 <span data-ttu-id="71c21-121">Montre comment utiliser les classes `ConnectionStringBuilder` pour générer des chaînes de connexion valides au moment de l'exécution.</span><span class="sxs-lookup"><span data-stu-id="71c21-121">Demonstrates how to use the `ConnectionStringBuilder` classes to construct valid connection strings at run time.</span></span>  
  
 [<span data-ttu-id="71c21-122">Chaînes de connexion et fichiers de configuration</span><span class="sxs-lookup"><span data-stu-id="71c21-122">Connection Strings and Configuration Files</span></span>](../../../../docs/framework/data/adonet/connection-strings-and-configuration-files.md)  
 <span data-ttu-id="71c21-123">Montre comment stocker et extraire des chaînes de connexion dans des fichiers de configuration.</span><span class="sxs-lookup"><span data-stu-id="71c21-123">Demonstrates how to store and retrieve connection strings in configuration files.</span></span>  
  
 [<span data-ttu-id="71c21-124">Syntaxe des chaînes de connexion</span><span class="sxs-lookup"><span data-stu-id="71c21-124">Connection String Syntax</span></span>](../../../../docs/framework/data/adonet/connection-string-syntax.md)  
 <span data-ttu-id="71c21-125">Décrit comment configurer des chaînes de connexion spécifiques au fournisseur pour `SqlClient`, `OracleClient`, `OleDb` et `Odbc`.</span><span class="sxs-lookup"><span data-stu-id="71c21-125">Describes how to configure provider-specific connection strings for `SqlClient`, `OracleClient`, `OleDb`, and `Odbc`.</span></span>  
  
 [<span data-ttu-id="71c21-126">Protection des informations de connexion</span><span class="sxs-lookup"><span data-stu-id="71c21-126">Protecting Connection Information</span></span>](../../../../docs/framework/data/adonet/protecting-connection-information.md)  
 <span data-ttu-id="71c21-127">Montre des techniques pour la protection des informations utilisées pour la connexion à une source de données.</span><span class="sxs-lookup"><span data-stu-id="71c21-127">Demonstrates techniques for protecting information used to connect to a data source.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="71c21-128">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="71c21-128">See Also</span></span>  
 [<span data-ttu-id="71c21-129">Connexion à une source de données</span><span class="sxs-lookup"><span data-stu-id="71c21-129">Connecting to a Data Source</span></span>](/cpp/data/odbc/connecting-to-a-data-source)  
 [<span data-ttu-id="71c21-130">Fournisseurs managés ADO.NET et centre de développement DataSet</span><span class="sxs-lookup"><span data-stu-id="71c21-130">ADO.NET Managed Providers and DataSet Developer Center</span></span>](http://go.microsoft.com/fwlink/?LinkId=217917)
