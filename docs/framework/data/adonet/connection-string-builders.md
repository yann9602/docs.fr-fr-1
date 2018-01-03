---
title: "Builders de chaînes de connexion"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: 8434b608-c4d3-43d3-8ae3-6d8c6b726759
caps.latest.revision: "3"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: a782969502509cb766e3a1d38222118a352dc3db
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="connection-string-builders"></a><span data-ttu-id="11cb2-102">Builders de chaînes de connexion</span><span class="sxs-lookup"><span data-stu-id="11cb2-102">Connection String Builders</span></span>
<span data-ttu-id="11cb2-103">Dans les versions antérieures de [!INCLUDE[vstecado](../../../../includes/vstecado-md.md)], vérification des chaînes de connexion avec la chaîne concaténée ne prenaient pas de valeurs, afin qu’au moment de l’exécution, un mot clé incorrect est généré lors de la compilation un <xref:System.ArgumentException>.</span><span class="sxs-lookup"><span data-stu-id="11cb2-103">In earlier versions of [!INCLUDE[vstecado](../../../../includes/vstecado-md.md)], compile-time checking of connection strings with concatenated string values did not occur, so that at run time, an incorrect keyword generated an <xref:System.ArgumentException>.</span></span> <span data-ttu-id="11cb2-104">Chacun des fournisseurs de données [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] utilisait une syntaxe différente pour les mots clés de chaîne de connexion, ce qui rendait difficile la génération de chaînes de connexion valides si l'opération était effectuée manuellement.</span><span class="sxs-lookup"><span data-stu-id="11cb2-104">Each of the [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] data providers supported different syntax for connection string keywords, which made constructing valid connection strings difficult if done manually.</span></span> <span data-ttu-id="11cb2-105">Pour résoudre ce problème, [!INCLUDE[vstecado](../../../../includes/vstecado-md.md)] 2.0 a introduit de nouveaux générateurs de chaînes de connexion pour chaque fournisseur de données [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)].</span><span class="sxs-lookup"><span data-stu-id="11cb2-105">To address this problem, [!INCLUDE[vstecado](../../../../includes/vstecado-md.md)] 2.0 introduced new connection string builders for each [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] data provider.</span></span> <span data-ttu-id="11cb2-106">Chaque fournisseur de données inclut une classe de générateur de chaînes de connexion fortement typée qui hérite de <xref:System.Data.Common.DbConnectionStringBuilder>.</span><span class="sxs-lookup"><span data-stu-id="11cb2-106">Each data provider includes a strongly typed connection string builder class that inherits from <xref:System.Data.Common.DbConnectionStringBuilder>.</span></span> <span data-ttu-id="11cb2-107">Le tableau suivant répertorie les fournisseurs de données [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] et leurs classes de générateur de chaînes de connexion associées.</span><span class="sxs-lookup"><span data-stu-id="11cb2-107">The following table lists the [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] data providers and their associated connection string builder classes.</span></span>  
  
|<span data-ttu-id="11cb2-108">Fournisseur</span><span class="sxs-lookup"><span data-stu-id="11cb2-108">Provider</span></span>|<span data-ttu-id="11cb2-109">Classe ConnectionStringBuilder</span><span class="sxs-lookup"><span data-stu-id="11cb2-109">ConnectionStringBuilder class</span></span>|  
|--------------|-----------------------------------|  
|<xref:System.Data.SqlClient>|<xref:System.Data.SqlClient.SqlConnectionStringBuilder?displayProperty=nameWithType>|  
|<xref:System.Data.OleDb>|<xref:System.Data.OleDb.OleDbConnectionStringBuilder?displayProperty=nameWithType>|  
|<xref:System.Data.Odbc>|<xref:System.Data.Odbc.OdbcConnectionStringBuilder?displayProperty=nameWithType>|  
|<xref:System.Data.OracleClient>|<xref:System.Data.OracleClient.OracleConnectionStringBuilder?displayProperty=nameWithType>|  
  
## <a name="connection-string-injection-attacks"></a><span data-ttu-id="11cb2-110">Attaques par injection de chaîne de connexion</span><span class="sxs-lookup"><span data-stu-id="11cb2-110">Connection String Injection Attacks</span></span>  
 <span data-ttu-id="11cb2-111">Une attaque par injection de chaîne de connexion peut se produire lorsqu'une concaténation de chaîne dynamique est utilisée pour générer des chaînes de connexion se basant sur l'entrée d'utilisateur.</span><span class="sxs-lookup"><span data-stu-id="11cb2-111">A connection string injection attack can occur when dynamic string concatenation is used to build connection strings that are based on user input.</span></span> <span data-ttu-id="11cb2-112">Si la chaîne n'est pas validée et que du texte ou des caractères malveillants ne font pas l'objet d'un échappement, un attaquant peut éventuellement accéder à des données sensibles ou à d'autres ressources sur le serveur.</span><span class="sxs-lookup"><span data-stu-id="11cb2-112">If the string is not validated and malicious text or characters not escaped, an attacker can potentially access sensitive data or other resources on the server.</span></span> <span data-ttu-id="11cb2-113">Par exemple, un attaquant peut organiser une attaque en fournissant un point-virgule et en ajoutant une valeur supplémentaire.</span><span class="sxs-lookup"><span data-stu-id="11cb2-113">For example, an attacker could mount an attack by supplying a semicolon and appending an additional value.</span></span> <span data-ttu-id="11cb2-114">La chaîne de connexion est alors analysée à l'aide de l'algorithme « last one wins », de sorte que l'entrée hostile soit remplacée par une valeur légitime.</span><span class="sxs-lookup"><span data-stu-id="11cb2-114">The connection string is parsed by using a "last one wins" algorithm, and the hostile input is substituted for a legitimate value.</span></span>  
  
 <span data-ttu-id="11cb2-115">Les classes de générateur de chaînes de connexion sont conçues pour éliminer le travail de recherche et pour se protéger contre les erreurs de syntaxe et les failles en matière de sécurité.</span><span class="sxs-lookup"><span data-stu-id="11cb2-115">The connection string builder classes are designed to eliminate guesswork and protect against syntax errors and security vulnerabilities.</span></span> <span data-ttu-id="11cb2-116">Elles fournissent des méthodes et des propriétés qui correspondent aux paires clé/valeur connues autorisées par chaque fournisseur de données.</span><span class="sxs-lookup"><span data-stu-id="11cb2-116">They provide methods and properties corresponding to the known key/value pairs permitted by each data provider.</span></span> <span data-ttu-id="11cb2-117">La classe maintient une collection fixe de synonymes et peut traduire un synonyme vers le nom de la clé connue correspondante.</span><span class="sxs-lookup"><span data-stu-id="11cb2-117">Each class maintains a fixed collection of synonyms and can translate from a synonym to the corresponding well-known key name.</span></span> <span data-ttu-id="11cb2-118">Des vérifications sont effectuées pour contrôler la validité des paires clé/valeur et une paire non valide lève une exception.</span><span class="sxs-lookup"><span data-stu-id="11cb2-118">Checks are performed for valid key/value pairs and an invalid pair throws an exception.</span></span> <span data-ttu-id="11cb2-119">En outre, les valeurs injectées sont gérées de manière sécurisée.</span><span class="sxs-lookup"><span data-stu-id="11cb2-119">In addition, injected values are handled in a safe manner.</span></span>  
  
 <span data-ttu-id="11cb2-120">L'exemple suivant montre comment <xref:System.Data.SqlClient.SqlConnectionStringBuilder> gère une valeur supplémentaire insérée pour le paramètre `Initial Catalog`.</span><span class="sxs-lookup"><span data-stu-id="11cb2-120">The following example demonstrates how the <xref:System.Data.SqlClient.SqlConnectionStringBuilder> handles an inserted extra value for the `Initial Catalog` setting.</span></span>  
  
```vb  
Dim builder As New System.Data.SqlClient.SqlConnectionStringBuilder  
builder("Data Source") = "(local)"  
builder("Integrated Security") = True  
builder("Initial Catalog") = "AdventureWorks;NewValue=Bad"  
Console.WriteLine(builder.ConnectionString)  
```  
  
```csharp  
System.Data.SqlClient.SqlConnectionStringBuilder builder =  
  new System.Data.SqlClient.SqlConnectionStringBuilder();  
builder["Data Source"] = "(local)";  
builder["integrated Security"] = true;  
builder["Initial Catalog"] = "AdventureWorks;NewValue=Bad";  
Console.WriteLine(builder.ConnectionString);  
```  
  
 <span data-ttu-id="11cb2-121">La sortie montre que <xref:System.Data.SqlClient.SqlConnectionStringBuilder> a agi correctement en plaçant dans une séquence d'échappement, entre des guillemets doubles, la valeur supplémentaire au lieu de l'ajouter à la chaîne de connexion en tant que nouvelle paire clé/valeur.</span><span class="sxs-lookup"><span data-stu-id="11cb2-121">The output shows that the <xref:System.Data.SqlClient.SqlConnectionStringBuilder> handled this correctly by escaping the extra value in double quotation marks instead of appending it to the connection string as a new key/value pair.</span></span>  
  
```  
data source=(local);Integrated Security=True;  
initial catalog="AdventureWorks;NewValue=Bad"  
```  
  
## <a name="building-connection-strings-from-configuration-files"></a><span data-ttu-id="11cb2-122">Génération de chaînes de connexion à partir de fichiers de configuration</span><span class="sxs-lookup"><span data-stu-id="11cb2-122">Building Connection Strings from Configuration Files</span></span>  
 <span data-ttu-id="11cb2-123">Si certains éléments d'une chaîne de connexion sont connus à l'avance, ils peuvent être stockés dans un fichier de configuration et récupérés au moment de l'exécution pour générer une chaîne de connexion complète.</span><span class="sxs-lookup"><span data-stu-id="11cb2-123">If certain elements of a connection string are known beforehand, they can be stored in a configuration file and retrieved at run time to construct a complete connection string.</span></span> <span data-ttu-id="11cb2-124">Par exemple, le nom de la base de données peut être connue à l'avance, mais pas celui du serveur.</span><span class="sxs-lookup"><span data-stu-id="11cb2-124">For example, the name of the database might be known in advance, but not the name of the server.</span></span> <span data-ttu-id="11cb2-125">Ou bien, vous pouvez souhaiter qu'un utilisateur fournisse un nom et un mot de passe au moment de l'exécution mais sans pouvoir injecter d'autres valeurs dans la chaîne de connexion.</span><span class="sxs-lookup"><span data-stu-id="11cb2-125">Or you might want a user to supply a name and password at run time without being able to inject other values into the connection string.</span></span>  
  
 <span data-ttu-id="11cb2-126">L'un des constructeurs surchargés d'un générateur de chaînes de connexion prend <xref:System.String> en tant qu'argument, ce qui vous permet de fournir une chaîne de connexion partielle qui pourra ensuite être complétée à partir de l'entrée d'utilisateur.</span><span class="sxs-lookup"><span data-stu-id="11cb2-126">One of the overloaded constructors for a connection string builder takes a <xref:System.String> as an argument, which enables you to supply a partial connection string that can then be completed from user input.</span></span> <span data-ttu-id="11cb2-127">La chaîne de connexion partielle peut être stockée dans un fichier de configuration et récupérée au moment de l'exécution.</span><span class="sxs-lookup"><span data-stu-id="11cb2-127">The partial connection string can be stored in a configuration file and retrieved at run time.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="11cb2-128">L'espace de noms <xref:System.Configuration> autorise l'accès par programme aux fichiers de configuration qui utilisent <xref:System.Web.Configuration.WebConfigurationManager> pour les applications Web et <xref:System.Configuration.ConfigurationManager> pour les applications Windows.</span><span class="sxs-lookup"><span data-stu-id="11cb2-128">The <xref:System.Configuration> namespace allows programmatic access to configuration files that use the <xref:System.Web.Configuration.WebConfigurationManager> for Web applications and the <xref:System.Configuration.ConfigurationManager> for Windows applications.</span></span> <span data-ttu-id="11cb2-129">Pour plus d’informations sur l’utilisation des chaînes de connexion et les fichiers de configuration, consultez [les chaînes de connexion et les fichiers de Configuration](../../../../docs/framework/data/adonet/connection-strings-and-configuration-files.md).</span><span class="sxs-lookup"><span data-stu-id="11cb2-129">For more information about working with connection strings and configuration files, see [Connection Strings and Configuration Files](../../../../docs/framework/data/adonet/connection-strings-and-configuration-files.md).</span></span>  
  
### <a name="example"></a><span data-ttu-id="11cb2-130">Exemple</span><span class="sxs-lookup"><span data-stu-id="11cb2-130">Example</span></span>  
 <span data-ttu-id="11cb2-131">Cet exemple montre comment récupérer une chaîne de connexion partielle d'un fichier de configuration et comment la compléter en définissant les propriétés <xref:System.Data.SqlClient.SqlConnectionStringBuilder.DataSource%2A>, <xref:System.Data.SqlClient.SqlConnectionStringBuilder.UserID%2A> et <xref:System.Data.SqlClient.SqlConnectionStringBuilder.Password%2A> de <xref:System.Data.SqlClient.SqlConnectionStringBuilder>.</span><span class="sxs-lookup"><span data-stu-id="11cb2-131">This example demonstrates retrieving a partial connection string from a configuration file and completing it by setting the <xref:System.Data.SqlClient.SqlConnectionStringBuilder.DataSource%2A>, <xref:System.Data.SqlClient.SqlConnectionStringBuilder.UserID%2A>, and <xref:System.Data.SqlClient.SqlConnectionStringBuilder.Password%2A> properties of the <xref:System.Data.SqlClient.SqlConnectionStringBuilder>.</span></span> <span data-ttu-id="11cb2-132">Le fichier de configuration est défini comme suit.</span><span class="sxs-lookup"><span data-stu-id="11cb2-132">The configuration file is defined as follows.</span></span>  
  
```xml  
<connectionStrings>  
  <clear/>  
  <add name="partialConnectString"   
    connectionString="Initial Catalog=Northwind;"  
    providerName="System.Data.SqlClient" />  
</connectionStrings>  
```  
  
> [!NOTE]
>  <span data-ttu-id="11cb2-133">Vous devez définir une référence à `System.Configuration.dll` dans votre projet pour le code à exécuter.</span><span class="sxs-lookup"><span data-stu-id="11cb2-133">You must set a reference to the `System.Configuration.dll` in your project for the code to run.</span></span>  
  
 [!code-csharp[DataWorks SqlConnectionStringBuilder.UserNamePwd#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlConnectionStringBuilder.UserNamePwd/CS/source.cs#1)]
 [!code-vb[DataWorks SqlConnectionStringBuilder.UserNamePwd#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlConnectionStringBuilder.UserNamePwd/VB/source.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="11cb2-134">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="11cb2-134">See Also</span></span>  
 [<span data-ttu-id="11cb2-135">Chaînes de connexion</span><span class="sxs-lookup"><span data-stu-id="11cb2-135">Connection Strings</span></span>](../../../../docs/framework/data/adonet/connection-strings.md)  
 [<span data-ttu-id="11cb2-136">Confidentialité et sécurité des données</span><span class="sxs-lookup"><span data-stu-id="11cb2-136">Privacy and Data Security</span></span>](../../../../docs/framework/data/adonet/privacy-and-data-security.md)  
 [<span data-ttu-id="11cb2-137">Fournisseurs managés ADO.NET et centre de développement DataSet</span><span class="sxs-lookup"><span data-stu-id="11cb2-137">ADO.NET Managed Providers and DataSet Developer Center</span></span>](http://go.microsoft.com/fwlink/?LinkId=217917)
