---
title: "Comment : générer du code personnalisé en modifiant un fichier DBML"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 50ad597a-8598-42d3-82dd-fc7d702ebc37
caps.latest.revision: "2"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: c9a2b382c84548d3226fe68531961e0f53033e7d
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/17/2018
---
# <a name="how-to-generate-customized-code-by-modifying-a-dbml-file"></a><span data-ttu-id="daced-102">Comment : générer du code personnalisé en modifiant un fichier DBML</span><span class="sxs-lookup"><span data-stu-id="daced-102">How to: Generate Customized Code by Modifying a DBML File</span></span>
<span data-ttu-id="daced-103">Vous pouvez générer [!INCLUDE[vbprvb](../../../../../../includes/vbprvb-md.md)] ou du code source c# à partir d’un fichier de métadonnées de base de données markup language (.dbml).</span><span class="sxs-lookup"><span data-stu-id="daced-103">You can generate [!INCLUDE[vbprvb](../../../../../../includes/vbprvb-md.md)] or C# source code from a database markup language (.dbml) metadata file.</span></span> <span data-ttu-id="daced-104">Cette approche permet de personnaliser le fichier .dbml par défaut avant de générer le code de mappage de l’application.</span><span class="sxs-lookup"><span data-stu-id="daced-104">This approach provides an opportunity to customize the default .dbml file before you generate the application mapping code.</span></span> <span data-ttu-id="daced-105">Il s'agit d'une fonctionnalité avancée.</span><span class="sxs-lookup"><span data-stu-id="daced-105">This is an advanced feature.</span></span>  
  
 <span data-ttu-id="daced-106">Les étapes de ce processus sont les suivantes :</span><span class="sxs-lookup"><span data-stu-id="daced-106">The steps in this process are as follows:</span></span>  
  
1.  <span data-ttu-id="daced-107">Générez un fichier .dbml.</span><span class="sxs-lookup"><span data-stu-id="daced-107">Generate a .dbml file.</span></span>  
  
2.  <span data-ttu-id="daced-108">Utilisez un éditeur pour modifier le fichier .dbml.</span><span class="sxs-lookup"><span data-stu-id="daced-108">Use an editor to modify the .dbml file.</span></span> <span data-ttu-id="daced-109">Notez que le fichier .dbml doit valider le fichier de définition (.xsd) schéma pour [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] fichiers .dbml.</span><span class="sxs-lookup"><span data-stu-id="daced-109">Note that the .dbml file must validate against the schema definition (.xsd) file for [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] .dbml files.</span></span> <span data-ttu-id="daced-110">Pour plus d’informations, consultez [la génération de Code dans LINQ to SQL](../../../../../../docs/framework/data/adonet/sql/linq/code-generation-in-linq-to-sql.md).</span><span class="sxs-lookup"><span data-stu-id="daced-110">For more information, see [Code Generation in LINQ to SQL](../../../../../../docs/framework/data/adonet/sql/linq/code-generation-in-linq-to-sql.md).</span></span>  
  
3.  <span data-ttu-id="daced-111">Générez le code source [!INCLUDE[vbprvb](../../../../../../includes/vbprvb-md.md)] ou C#.</span><span class="sxs-lookup"><span data-stu-id="daced-111">Generate the [!INCLUDE[vbprvb](../../../../../../includes/vbprvb-md.md)] or C# source code.</span></span>  
  
 <span data-ttu-id="daced-112">Les exemples suivants utilisent l'outil en ligne de commande SQLMetal.</span><span class="sxs-lookup"><span data-stu-id="daced-112">The following examples use the SQLMetal command-line tool.</span></span> <span data-ttu-id="daced-113">Pour plus d’informations, consultez [SqlMetal.exe (outil de génération de code)](../../../../../../docs/framework/tools/sqlmetal-exe-code-generation-tool.md).</span><span class="sxs-lookup"><span data-stu-id="daced-113">For more information, see [SqlMetal.exe (Code Generation Tool)](../../../../../../docs/framework/tools/sqlmetal-exe-code-generation-tool.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="daced-114">Exemple</span><span class="sxs-lookup"><span data-stu-id="daced-114">Example</span></span>  
 <span data-ttu-id="daced-115">Le code suivant génère un fichier .dbml à partir de l'exemple de base de données Northwind.</span><span class="sxs-lookup"><span data-stu-id="daced-115">The following code generates a .dbml file from the Northwind sample database.</span></span> <span data-ttu-id="daced-116">Vous pouvez utiliser le nom de la base de données ou le nom du fichier .mdf comme source pour les métadonnées de base de données.</span><span class="sxs-lookup"><span data-stu-id="daced-116">As source for the database metadata, you can use either the name of the database or the name of the .mdf file.</span></span>  
  
```  
sqlmetal /server:myserver /database:northwind /dbml:mymeta.dbml  
sqlmetal /dbml:mymeta.dbml mydbfile.mdf  
```  
  
## <a name="example"></a><span data-ttu-id="daced-117">Exemple</span><span class="sxs-lookup"><span data-stu-id="daced-117">Example</span></span>  
 <span data-ttu-id="daced-118">Le code suivant génère le fichier de code source [!INCLUDE[vbprvb](../../../../../../includes/vbprvb-md.md)] ou C# à partir d'un fichier .dbml.</span><span class="sxs-lookup"><span data-stu-id="daced-118">The following code generates [!INCLUDE[vbprvb](../../../../../../includes/vbprvb-md.md)] or C# source code file from a .dbml file.</span></span>  
  
```  
sqlmetal /namespace:nwind /code:nwind.vb /language:vb DBMLFile.dbml  
sqlmetal /namespace:nwind /code:nwind.cs /language:csharp DBMLFile.dbml  
```  
  
## <a name="see-also"></a><span data-ttu-id="daced-119">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="daced-119">See Also</span></span>  
 [<span data-ttu-id="daced-120">Génération de code dans LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="daced-120">Code Generation in LINQ to SQL</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/code-generation-in-linq-to-sql.md)  
 [<span data-ttu-id="daced-121">SqlMetal.exe (outil de génération de code)</span><span class="sxs-lookup"><span data-stu-id="daced-121">SqlMetal.exe (Code Generation Tool)</span></span>](../../../../../../docs/framework/tools/sqlmetal-exe-code-generation-tool.md)  
 [<span data-ttu-id="daced-122">Création du modèle objet</span><span class="sxs-lookup"><span data-stu-id="daced-122">Creating the Object Model</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/creating-the-object-model.md)
