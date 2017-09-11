---
title: "SqlMetal.exe (outil de génération de code)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- SQLMetal [LINQ to SQL]
- code generation tool
- SQLMetal.exe
- LINQ to SQL, serialization
- LINQ to SQL, DBML files
- LINQ to SQL, SQLMetal
ms.assetid: 819e5a96-7646-4fdb-b14b-fe31221b0614
caps.latest.revision: 43
author: Erikre
ms.author: erikre
manager: erikre
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 6d0ac9c682c60db8eb9e5188a71916dc5d97de60
ms.contentlocale: fr-fr
ms.lasthandoff: 07/28/2017

---
# <a name="sqlmetalexe-code-generation-tool"></a><span data-ttu-id="34524-102">SqlMetal.exe (outil de génération de code)</span><span class="sxs-lookup"><span data-stu-id="34524-102">SqlMetal.exe (Code Generation Tool)</span></span>
<span data-ttu-id="34524-103">L'outil en ligne de commande SqlMetal génère le code et le mappage du composant [!INCLUDE[vbtecdlinq](../../../includes/vbtecdlinq-md.md)] du [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)].</span><span class="sxs-lookup"><span data-stu-id="34524-103">The SqlMetal command-line tool generates code and mapping for the [!INCLUDE[vbtecdlinq](../../../includes/vbtecdlinq-md.md)] component of the [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)].</span></span> <span data-ttu-id="34524-104">En appliquant les options qui apparaissent ultérieurement dans cette rubrique, vous pouvez ordonner à SqlMetal d'exécuter plusieurs actions différentes, dont les suivantes :</span><span class="sxs-lookup"><span data-stu-id="34524-104">By applying options that appear later in this topic, you can instruct SqlMetal to perform several different actions that include the following:</span></span>  
  
-   <span data-ttu-id="34524-105">À partir d'une base de données, générez le code source et les attributs de mappage ou un fichier de mappage.</span><span class="sxs-lookup"><span data-stu-id="34524-105">From a database, generate source code and mapping attributes or a mapping file.</span></span>  
  
-   <span data-ttu-id="34524-106">À partir d'une base de données, générez un fichier .dbml (database markup language) intermédiaire à des fins de personnalisation.</span><span class="sxs-lookup"><span data-stu-id="34524-106">From a database, generate an intermediate database markup language (.dbml) file for customization.</span></span>  
  
-   <span data-ttu-id="34524-107">À partir d'un fichier .dbml, générez du code et des attributs de mappage ou un fichier de mappage.</span><span class="sxs-lookup"><span data-stu-id="34524-107">From a .dbml file, generate code and mapping attributes or a mapping file.</span></span>  
  
 <span data-ttu-id="34524-108">Cet outil est installé automatiquement avec Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="34524-108">This tool is automatically installed with Visual Studio.</span></span> <span data-ttu-id="34524-109">Par défaut, ce fichier se trouve à l'emplacement suivant : `drive`:\Program Files\Microsoft SDKs\Windows\v`n.nn`\bin.</span><span class="sxs-lookup"><span data-stu-id="34524-109">By default, the file is located at `drive`:\Program Files\Microsoft SDKs\Windows\v`n.nn`\bin.</span></span> <span data-ttu-id="34524-110">Si vous n’installez pas Visual Studio, vous pouvez également obtenir le fichier SQLMetal en téléchargeant le [SDK Windows](http://go.microsoft.com/fwlink/?LinkId=142225).</span><span class="sxs-lookup"><span data-stu-id="34524-110">If you do not install Visual Studio, you can also get the SQLMetal file by downloading the [Windows SDK](http://go.microsoft.com/fwlink/?LinkId=142225).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="34524-111">Les développeurs qui utilisent Visual Studio peuvent également utiliser [!INCLUDE[vs_ordesigner_long](../../../includes/vs-ordesigner-long-md.md)] pour générer des classes d'entité.</span><span class="sxs-lookup"><span data-stu-id="34524-111">Developers who use Visual Studio can also use the [!INCLUDE[vs_ordesigner_long](../../../includes/vs-ordesigner-long-md.md)] to generate entity classes.</span></span> <span data-ttu-id="34524-112">L'approche de ligne de commande est bien adaptée aux bases de données volumineuses.</span><span class="sxs-lookup"><span data-stu-id="34524-112">The command-line approach scales well for large databases.</span></span> <span data-ttu-id="34524-113">Puisque SqlMetal est un outil de ligne de commande, vous pouvez l'utiliser dans un processus de génération.</span><span class="sxs-lookup"><span data-stu-id="34524-113">Because SqlMetal is a command-line tool, you can use it in a build process.</span></span>  
  
 <span data-ttu-id="34524-114">Pour exécuter l'outil, utilisez l'invite de commandes développeur (ou l'invite de commandes Visual Studio dans Windows 7).</span><span class="sxs-lookup"><span data-stu-id="34524-114">To run the tool, use the Developer Command Prompt (or the Visual Studio Command Prompt in Windows 7).</span></span> <span data-ttu-id="34524-115">Pour plus d’informations, consultez [Invites de commandes](../../../docs/framework/tools/developer-command-prompt-for-vs.md). À l’invite de commandes, tapez ce qui suit :</span><span class="sxs-lookup"><span data-stu-id="34524-115">For more information, see [Command Prompts](../../../docs/framework/tools/developer-command-prompt-for-vs.md).At the command prompt, type the following:</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="34524-116">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="34524-116">Syntax</span></span>  
  
```  
sqlmetal [options] [<input file>]  
```  
  
## <a name="options"></a><span data-ttu-id="34524-117">Options</span><span class="sxs-lookup"><span data-stu-id="34524-117">Options</span></span>  
 <span data-ttu-id="34524-118">Pour afficher la liste des options la plus récente, tapez `sqlmetal /?` à partir d’une invite de commandes depuis l’emplacement d’installation.</span><span class="sxs-lookup"><span data-stu-id="34524-118">To view the most current option list, type `sqlmetal /?` at a command prompt from the installed location.</span></span>  
  
 <span data-ttu-id="34524-119">**Options de connexion**</span><span class="sxs-lookup"><span data-stu-id="34524-119">**Connection Options**</span></span>  
  
|<span data-ttu-id="34524-120">Option</span><span class="sxs-lookup"><span data-stu-id="34524-120">Option</span></span>|<span data-ttu-id="34524-121">Description</span><span class="sxs-lookup"><span data-stu-id="34524-121">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="34524-122">**/server:** *\<nom>*</span><span class="sxs-lookup"><span data-stu-id="34524-122">**/server:** *\<name>*</span></span>|<span data-ttu-id="34524-123">Spécifie le nom du serveur de base de données.</span><span class="sxs-lookup"><span data-stu-id="34524-123">Specifies database server name.</span></span>|  
|<span data-ttu-id="34524-124">**/database:** *\<nom>*</span><span class="sxs-lookup"><span data-stu-id="34524-124">**/database:** *\<name>*</span></span>|<span data-ttu-id="34524-125">Spécifie le catalogue de base de données sur le serveur.</span><span class="sxs-lookup"><span data-stu-id="34524-125">Specifies database catalog on server.</span></span>|  
|<span data-ttu-id="34524-126">**/user:** *\<nom>*</span><span class="sxs-lookup"><span data-stu-id="34524-126">**/user:** *\<name>*</span></span>|<span data-ttu-id="34524-127">Spécifie l'ID de connexion de l'utilisateur.</span><span class="sxs-lookup"><span data-stu-id="34524-127">Specifies logon user id.</span></span> <span data-ttu-id="34524-128">Valeur par défaut : utilisez l'authentification Windows.</span><span class="sxs-lookup"><span data-stu-id="34524-128">Default value: Use Windows authentication.</span></span>|  
|<span data-ttu-id="34524-129">**/password:** *\<mot_de_passe>*</span><span class="sxs-lookup"><span data-stu-id="34524-129">**/password:** *\<password>*</span></span>|<span data-ttu-id="34524-130">Spécifie le mot de passe d'ouverture de session.</span><span class="sxs-lookup"><span data-stu-id="34524-130">Specifies logon password.</span></span> <span data-ttu-id="34524-131">Valeur par défaut : utilisez l'authentification Windows.</span><span class="sxs-lookup"><span data-stu-id="34524-131">Default value: Use Windows authentication.</span></span>|  
|<span data-ttu-id="34524-132">**/conn:** *\<chaîne_connexion>*</span><span class="sxs-lookup"><span data-stu-id="34524-132">**/conn:** *\<connection string>*</span></span>|<span data-ttu-id="34524-133">Spécifie la chaîne de connexion de base de données.</span><span class="sxs-lookup"><span data-stu-id="34524-133">Specifies database connection string.</span></span> <span data-ttu-id="34524-134">Ne peut pas être utilisée avec les options **/server**, **/database**, **/user**ou **/password** .</span><span class="sxs-lookup"><span data-stu-id="34524-134">Cannot be used with **/server**, **/database**, **/user**, or **/password** options.</span></span><br /><br /> <span data-ttu-id="34524-135">N'inclut pas le nom de fichier dans la chaîne de connexion.</span><span class="sxs-lookup"><span data-stu-id="34524-135">Do not include the file name in the connection string.</span></span> <span data-ttu-id="34524-136">Ajoutez plutôt le nom de fichier à la ligne de commande comme fichier d'entrée.</span><span class="sxs-lookup"><span data-stu-id="34524-136">Instead, add the file name to the command line as the input file.</span></span> <span data-ttu-id="34524-137">Par exemple, la ligne suivante spécifie "c:\northwnd.mdf" comme fichier d’entrée : **sqlmetal /code:"c:\northwind.cs" /language:csharp "c:\northwnd.mdf"**.</span><span class="sxs-lookup"><span data-stu-id="34524-137">For example, the following line specifies "c:\northwnd.mdf" as the input file: **sqlmetal /code:"c:\northwind.cs" /language:csharp "c:\northwnd.mdf"**.</span></span>|  
|<span data-ttu-id="34524-138">**/timeout:** *\<secondes>*</span><span class="sxs-lookup"><span data-stu-id="34524-138">**/timeout:** *\<seconds>*</span></span>|<span data-ttu-id="34524-139">Spécifie la valeur du délai d'attente lorsque SqlMetal accède à la base de données.</span><span class="sxs-lookup"><span data-stu-id="34524-139">Specifies time-out value when SqlMetal accesses the database.</span></span> <span data-ttu-id="34524-140">Valeur par défaut : 0 (à savoir, aucune limite de temps).</span><span class="sxs-lookup"><span data-stu-id="34524-140">Default value: 0 (that is, no time limit).</span></span>|  
  
 <span data-ttu-id="34524-141">**Options d'extraction**</span><span class="sxs-lookup"><span data-stu-id="34524-141">**Extraction options**</span></span>  
  
|<span data-ttu-id="34524-142">Option</span><span class="sxs-lookup"><span data-stu-id="34524-142">Option</span></span>|<span data-ttu-id="34524-143">Description</span><span class="sxs-lookup"><span data-stu-id="34524-143">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="34524-144">**/views**</span><span class="sxs-lookup"><span data-stu-id="34524-144">**/views**</span></span>|<span data-ttu-id="34524-145">Extrait des vues de base de données.</span><span class="sxs-lookup"><span data-stu-id="34524-145">Extracts database views.</span></span>|  
|<span data-ttu-id="34524-146">**/functions**</span><span class="sxs-lookup"><span data-stu-id="34524-146">**/functions**</span></span>|<span data-ttu-id="34524-147">Extrait des fonctions de base de données.</span><span class="sxs-lookup"><span data-stu-id="34524-147">Extracts database functions.</span></span>|  
|<span data-ttu-id="34524-148">**/sprocs**</span><span class="sxs-lookup"><span data-stu-id="34524-148">**/sprocs**</span></span>|<span data-ttu-id="34524-149">Extrait des procédures stockées.</span><span class="sxs-lookup"><span data-stu-id="34524-149">Extracts stored procedures.</span></span>|  
  
 <span data-ttu-id="34524-150">**Options de sortie**</span><span class="sxs-lookup"><span data-stu-id="34524-150">**Output options**</span></span>  
  
|<span data-ttu-id="34524-151">Option</span><span class="sxs-lookup"><span data-stu-id="34524-151">Option</span></span>|<span data-ttu-id="34524-152">Description</span><span class="sxs-lookup"><span data-stu-id="34524-152">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="34524-153">**/dbml** *[:file]*</span><span class="sxs-lookup"><span data-stu-id="34524-153">**/dbml** *[:file]*</span></span>|<span data-ttu-id="34524-154">Envoie la sortie au format .dbml.</span><span class="sxs-lookup"><span data-stu-id="34524-154">Sends output as .dbml.</span></span> <span data-ttu-id="34524-155">Ne peut pas être utilisée avec l’option **/map** .</span><span class="sxs-lookup"><span data-stu-id="34524-155">Cannot be used with **/map** option.</span></span>|  
|<span data-ttu-id="34524-156">**/code** *[:file]*</span><span class="sxs-lookup"><span data-stu-id="34524-156">**/code** *[:file]*</span></span>|<span data-ttu-id="34524-157">Envoie la sortie sous la forme de code source.</span><span class="sxs-lookup"><span data-stu-id="34524-157">Sends output as source code.</span></span> <span data-ttu-id="34524-158">Ne peut pas être utilisée avec l’option **/dbml** .</span><span class="sxs-lookup"><span data-stu-id="34524-158">Cannot be used with **/dbml** option.</span></span>|  
|<span data-ttu-id="34524-159">**/map** *[:file]*</span><span class="sxs-lookup"><span data-stu-id="34524-159">**/map** *[:file]*</span></span>|<span data-ttu-id="34524-160">Génère un fichier de mappage XML plutôt que des attributs.</span><span class="sxs-lookup"><span data-stu-id="34524-160">Generates an XML mapping file instead of attributes.</span></span> <span data-ttu-id="34524-161">Ne peut pas être utilisée avec l’option **/dbml** .</span><span class="sxs-lookup"><span data-stu-id="34524-161">Cannot be used with **/dbml** option.</span></span>|  
  
 <span data-ttu-id="34524-162">**Divers**</span><span class="sxs-lookup"><span data-stu-id="34524-162">**Miscellaneous**</span></span>  
  
|<span data-ttu-id="34524-163">Option</span><span class="sxs-lookup"><span data-stu-id="34524-163">Option</span></span>|<span data-ttu-id="34524-164">Description</span><span class="sxs-lookup"><span data-stu-id="34524-164">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="34524-165">**/language:** *\<langage>*</span><span class="sxs-lookup"><span data-stu-id="34524-165">**/language:** *\<language>*</span></span>|<span data-ttu-id="34524-166">Spécifie le langage du code source.</span><span class="sxs-lookup"><span data-stu-id="34524-166">Specifies source code language.</span></span><br /><br /> <span data-ttu-id="34524-167">*\<langage>* valide : vb, csharp.</span><span class="sxs-lookup"><span data-stu-id="34524-167">Valid *\<language>*: vb, csharp.</span></span><br /><br /> <span data-ttu-id="34524-168">Valeur par défaut : Dérivé de l’extension du nom du fichier de code.</span><span class="sxs-lookup"><span data-stu-id="34524-168">Default value: Derived from extension on code file name.</span></span>|  
|<span data-ttu-id="34524-169">**/namespace:** *\<nom>*</span><span class="sxs-lookup"><span data-stu-id="34524-169">**/namespace:** *\<name>*</span></span>|<span data-ttu-id="34524-170">Spécifie l'espace de noms du code généré.</span><span class="sxs-lookup"><span data-stu-id="34524-170">Specifies namespace of the generated code.</span></span> <span data-ttu-id="34524-171">Valeur par défaut : Aucun espace de noms.</span><span class="sxs-lookup"><span data-stu-id="34524-171">Default value: no namespace.</span></span>|  
|<span data-ttu-id="34524-172">**/context:** *\<type>*</span><span class="sxs-lookup"><span data-stu-id="34524-172">**/context:** *\<type>*</span></span>|<span data-ttu-id="34524-173">Spécifie le nom de la classe du contexte de données.</span><span class="sxs-lookup"><span data-stu-id="34524-173">Specifies name of data context class.</span></span> <span data-ttu-id="34524-174">Valeur par défaut : Dérivé du nom de la base de données.</span><span class="sxs-lookup"><span data-stu-id="34524-174">Default value: Derived from database name.</span></span>|  
|<span data-ttu-id="34524-175">**/entitybase:** *\<type>*</span><span class="sxs-lookup"><span data-stu-id="34524-175">**/entitybase:** *\<type>*</span></span>|<span data-ttu-id="34524-176">Spécifie la classe de base des classes d'entité du code généré.</span><span class="sxs-lookup"><span data-stu-id="34524-176">Specifies the base class of the entity classes in the generated code.</span></span> <span data-ttu-id="34524-177">Valeur par défaut : Les entités n'ont pas de classe de base.</span><span class="sxs-lookup"><span data-stu-id="34524-177">Default value: Entities have no base class.</span></span>|  
|<span data-ttu-id="34524-178">**/pluralize**</span><span class="sxs-lookup"><span data-stu-id="34524-178">**/pluralize**</span></span>|<span data-ttu-id="34524-179">Pluralise ou singularise automatiquement des noms de membre et de classe.</span><span class="sxs-lookup"><span data-stu-id="34524-179">Automatically pluralizes or singularizes class and member names.</span></span><br /><br /> <span data-ttu-id="34524-180">Cette option est disponible uniquement dans la version Anglais américain.</span><span class="sxs-lookup"><span data-stu-id="34524-180">This option is available only in the U.S. English version.</span></span>|  
|<span data-ttu-id="34524-181">**/serialization:** *\<option>*</span><span class="sxs-lookup"><span data-stu-id="34524-181">**/serialization:** *\<option>*</span></span>|<span data-ttu-id="34524-182">Génère des classes sérialisables.</span><span class="sxs-lookup"><span data-stu-id="34524-182">Generates serializable classes.</span></span><br /><br /> <span data-ttu-id="34524-183">*\<option>*valide : None, Unidirectional.</span><span class="sxs-lookup"><span data-stu-id="34524-183">Valid *\<option>*: None, Unidirectional.</span></span> <span data-ttu-id="34524-184">Valeur par défaut : Aucun.</span><span class="sxs-lookup"><span data-stu-id="34524-184">Default value: None.</span></span><br /><br /> <span data-ttu-id="34524-185">Pour plus d’informations, consultez [Sérialisation](../../../docs/framework/data/adonet/sql/linq/serialization.md).</span><span class="sxs-lookup"><span data-stu-id="34524-185">For more information, see [Serialization](../../../docs/framework/data/adonet/sql/linq/serialization.md).</span></span>|  
  
 <span data-ttu-id="34524-186">**Fichier d'entrée**</span><span class="sxs-lookup"><span data-stu-id="34524-186">**Input File**</span></span>  
  
|<span data-ttu-id="34524-187">Option</span><span class="sxs-lookup"><span data-stu-id="34524-187">Option</span></span>|<span data-ttu-id="34524-188">Description</span><span class="sxs-lookup"><span data-stu-id="34524-188">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="34524-189">**\<fichier_entrée>**</span><span class="sxs-lookup"><span data-stu-id="34524-189">**\<input file>**</span></span>|<span data-ttu-id="34524-190">Spécifie un fichier SQL Server Express .mdf, un fichier [!INCLUDE[ssEW](../../../includes/ssew-md.md)] .sdf, ou un fichier intermédiaire .dbml.</span><span class="sxs-lookup"><span data-stu-id="34524-190">Specifies a SQL Server Express .mdf file, a [!INCLUDE[ssEW](../../../includes/ssew-md.md)] .sdf file, or a .dbml intermediate file.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="34524-191">Remarques</span><span class="sxs-lookup"><span data-stu-id="34524-191">Remarks</span></span>  
 <span data-ttu-id="34524-192">La fonctionnalité SqlMetal implique en fait deux étapes :</span><span class="sxs-lookup"><span data-stu-id="34524-192">SqlMetal functionality actually involves two steps:</span></span>  
  
-   <span data-ttu-id="34524-193">Extraction des métadonnées de la base de données dans un fichier .dbml.</span><span class="sxs-lookup"><span data-stu-id="34524-193">Extracting the metadata of the database into a .dbml file.</span></span>  
  
-   <span data-ttu-id="34524-194">Génération d'un fichier de sortie de code.</span><span class="sxs-lookup"><span data-stu-id="34524-194">Generating a code output file.</span></span>  
  
     <span data-ttu-id="34524-195">En utilisant les options de ligne de commande appropriées, vous pouvez produire [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)] ou du code source C#, ou encore un fichier de mappage XML.</span><span class="sxs-lookup"><span data-stu-id="34524-195">By using the appropriate command-line options, you can produce [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)] or C# source code, or you can produce an XML mapping file.</span></span>  
  
 <span data-ttu-id="34524-196">Pour extraire les métadonnées d'un fichier .mdf, vous devez spécifier le nom du fichier .mdf après toutes les autres options.</span><span class="sxs-lookup"><span data-stu-id="34524-196">To extract the metadata from an .mdf file, you must specify the name of the .mdf file after all other options.</span></span>  
  
 <span data-ttu-id="34524-197">Si **/server** n’est pas spécifié, **localhost/sqlexpress** est supposé.</span><span class="sxs-lookup"><span data-stu-id="34524-197">If no **/server** is specified, **localhost/sqlexpress** is assumed.</span></span>  
  
 [!INCLUDE[sqprsqext](../../../includes/sqprsqext-md.md)]<span data-ttu-id="34524-198"> lève une exception si une ou plusieurs conditions parmi les suivantes est vraie :</span><span class="sxs-lookup"><span data-stu-id="34524-198"> throws an exception if one or more of the following conditions are true:</span></span>  
  
-   <span data-ttu-id="34524-199">SqlMetal essaie d'extraire une procédure stockée qui s'appelle elle-même.</span><span class="sxs-lookup"><span data-stu-id="34524-199">SqlMetal tries to extract a stored procedure that calls itself.</span></span>  
  
-   <span data-ttu-id="34524-200">Le niveau d'imbrication d'une procédure stockée, d'une fonction, ou d'une vue dépasse 32.</span><span class="sxs-lookup"><span data-stu-id="34524-200">The nesting level of a stored procedure, function, or view exceeds 32.</span></span>  
  
     <span data-ttu-id="34524-201">SqlMetal intercepte cette exception et la signale comme un avertissement.</span><span class="sxs-lookup"><span data-stu-id="34524-201">SqlMetal catches this exception and reports it as a warning.</span></span>  
  
 <span data-ttu-id="34524-202">Pour spécifier un nom de fichier d'entrée, ajoutez son nom à la ligne de commande comme fichier d'entrée.</span><span class="sxs-lookup"><span data-stu-id="34524-202">To specify an input file name, add the name to the command line as the input file.</span></span> <span data-ttu-id="34524-203">L’inclusion du nom de fichier dans la chaîne de connexion (avec l’option **/conn** ) n’est pas prise en charge.</span><span class="sxs-lookup"><span data-stu-id="34524-203">Including the file name in the connection string (using the **/conn** option) is not supported.</span></span>  
  
## <a name="examples"></a><span data-ttu-id="34524-204">Exemples</span><span class="sxs-lookup"><span data-stu-id="34524-204">Examples</span></span>  
 <span data-ttu-id="34524-205">Générez un fichier .dbml qui inclut des métadonnées SQL extraites :</span><span class="sxs-lookup"><span data-stu-id="34524-205">Generate a .dbml file that includes extracted SQL metadata:</span></span>  
  
 <span data-ttu-id="34524-206">**sqlmetal /server:myserver /database:northwind /dbml:mymeta.dbml**</span><span class="sxs-lookup"><span data-stu-id="34524-206">**sqlmetal /server:myserver /database:northwind /dbml:mymeta.dbml**</span></span>  
  
 <span data-ttu-id="34524-207">Générez un fichier .dbml qui inclut des métadonnées SQL extraites d'un fichier .mdf à l'aide de SQL Server Express :</span><span class="sxs-lookup"><span data-stu-id="34524-207">Generate a .dbml file that includes extracted SQL metadata from an .mdf file by using SQL Server Express:</span></span>  
  
 <span data-ttu-id="34524-208">**sqlmetal /dbml:mymeta.dbml mydbfile.mdf**</span><span class="sxs-lookup"><span data-stu-id="34524-208">**sqlmetal /dbml:mymeta.dbml mydbfile.mdf**</span></span>  
  
 <span data-ttu-id="34524-209">Générez un fichier .dbml qui inclut des métadonnées SQL extraites de SQL Server Express :</span><span class="sxs-lookup"><span data-stu-id="34524-209">Generate a .dbml file that includes extracted SQL metadata from SQL Server Express:</span></span>  
  
 <span data-ttu-id="34524-210">**sqlmetal /server:.\sqlexpress /dbml:mymeta.dbml /database:northwind**</span><span class="sxs-lookup"><span data-stu-id="34524-210">**sqlmetal /server:.\sqlexpress /dbml:mymeta.dbml /database:northwind**</span></span>  
  
 <span data-ttu-id="34524-211">Générez du code source à partir d'un fichier de métadonnées .dbml :</span><span class="sxs-lookup"><span data-stu-id="34524-211">Generate source code from a .dbml metadata file:</span></span>  
  
 <span data-ttu-id="34524-212">**sqlmetal /namespace:nwind /code:nwind.cs /language:csharp mymetal.dbml**</span><span class="sxs-lookup"><span data-stu-id="34524-212">**sqlmetal /namespace:nwind /code:nwind.cs /language:csharp mymetal.dbml**</span></span>  
  
 <span data-ttu-id="34524-213">Générez le code source directement à partir de métadonnées SQL :</span><span class="sxs-lookup"><span data-stu-id="34524-213">Generate source code from SQL metadata directly:</span></span>  
  
 <span data-ttu-id="34524-214">**sqlmetal /server:myserver /database:northwind /namespace:nwind /code:nwind.cs /language:csharp**</span><span class="sxs-lookup"><span data-stu-id="34524-214">**sqlmetal /server:myserver /database:northwind /namespace:nwind /code:nwind.cs /language:csharp**</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="34524-215">Quand vous utilisez l’option **/pluralize** avec l’exemple de base de données Northwind, notez le comportement suivant.</span><span class="sxs-lookup"><span data-stu-id="34524-215">When you use the **/pluralize** option with the Northwind sample database, note the following behavior.</span></span> <span data-ttu-id="34524-216">Lorsque SqlMetal génère des noms de types de lignes pour des tables, les noms de table sont au singulier.</span><span class="sxs-lookup"><span data-stu-id="34524-216">When SqlMetal makes row-type names for tables, the table names are singular.</span></span> <span data-ttu-id="34524-217">Lorsqu'il génère des propriétés <xref:System.Data.Linq.DataContext> pour des tables, les noms de table sont au pluriel.</span><span class="sxs-lookup"><span data-stu-id="34524-217">When it makes <xref:System.Data.Linq.DataContext> properties for tables, the table names are plural.</span></span> <span data-ttu-id="34524-218">Par coïncidence, les tables de l'exemple de base de données Northwind sont déjà au pluriel.</span><span class="sxs-lookup"><span data-stu-id="34524-218">Coincidentally, the tables in the Northwind sample database are already plural.</span></span> <span data-ttu-id="34524-219">Par conséquent, vous ne pourrez pas voir cette partie active.</span><span class="sxs-lookup"><span data-stu-id="34524-219">Therefore, you do not see that part working.</span></span> <span data-ttu-id="34524-220">Bien qu’il soit courant de nommer des tables de base de données au pluriel, il est également courant dans .NET de nommer des collections au pluriel.</span><span class="sxs-lookup"><span data-stu-id="34524-220">Although it is common practice to name database tables singular, it is also a common practice in .NET to name collections plural.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="34524-221">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="34524-221">See Also</span></span>  
 <span data-ttu-id="34524-222">[Guide pratique pour générer le modèle objet en Visual Basic ou C#](../../../docs/framework/data/adonet/sql/linq/how-to-generate-the-object-model-in-visual-basic-or-csharp.md) </span><span class="sxs-lookup"><span data-stu-id="34524-222">[How to: Generate the Object Model in Visual Basic or C#](../../../docs/framework/data/adonet/sql/linq/how-to-generate-the-object-model-in-visual-basic-or-csharp.md) </span></span>  
 <span data-ttu-id="34524-223">[Génération de code dans LINQ to SQL](../../../docs/framework/data/adonet/sql/linq/code-generation-in-linq-to-sql.md) </span><span class="sxs-lookup"><span data-stu-id="34524-223">[Code Generation in LINQ to SQL](../../../docs/framework/data/adonet/sql/linq/code-generation-in-linq-to-sql.md) </span></span>  
 [<span data-ttu-id="34524-224">Mappage externe</span><span class="sxs-lookup"><span data-stu-id="34524-224">External Mapping</span></span>](../../../docs/framework/data/adonet/sql/linq/external-mapping.md)

