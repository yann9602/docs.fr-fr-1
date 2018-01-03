---
title: "Comment : générer le modèle objet en Visual Basic ou C#"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a0c73b33-5650-420c-b9dc-f49310c201ee
caps.latest.revision: "3"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: f4cf0999366a1a677fa729f2d409bea36821eb3a
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-generate-the-object-model-in-visual-basic-or-c"></a><span data-ttu-id="a07e4-102">Comment : générer le modèle objet en Visual Basic ou C#</span><span class="sxs-lookup"><span data-stu-id="a07e4-102">How to: Generate the Object Model in Visual Basic or C#</span></span> #
<span data-ttu-id="a07e4-103">Dans [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], un modèle objet dans votre propre langage de programmation est mappé à une base de données relationnelle.</span><span class="sxs-lookup"><span data-stu-id="a07e4-103">In [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], an object model in your own programming language is mapped to a relational database.</span></span> <span data-ttu-id="a07e4-104">Deux outils sont disponibles pour générer automatiquement un [!INCLUDE[vbprvb](../../../../../../includes/vbprvb-md.md)] ou le modèle c# à partir des métadonnées de base de données existante.</span><span class="sxs-lookup"><span data-stu-id="a07e4-104">Two tools are available for automatically generating a [!INCLUDE[vbprvb](../../../../../../includes/vbprvb-md.md)] or C# model from the metadata of an existing database.</span></span>  
  
-   <span data-ttu-id="a07e4-105">Si vous utilisez [!INCLUDE[vs_current_short](../../../../../../includes/vs-current-short-md.md)], vous pouvez générer un modèle objet à l'aide d'[!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)].</span><span class="sxs-lookup"><span data-stu-id="a07e4-105">If you are using [!INCLUDE[vs_current_short](../../../../../../includes/vs-current-short-md.md)], you can use the [!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)] to generate an object model.</span></span> <span data-ttu-id="a07e4-106">Le [!INCLUDE[vs_ordesigner_short](../../../../../../includes/vs-ordesigner-short-md.md)] fournit une interface utilisateur élaborée pour vous aider à générer un [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] modèle objet.</span><span class="sxs-lookup"><span data-stu-id="a07e4-106">The [!INCLUDE[vs_ordesigner_short](../../../../../../includes/vs-ordesigner-short-md.md)] provides a rich user interface to help you generate a [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] object model.</span></span> <span data-ttu-id="a07e4-107">Pour plus d’informations, consultez [Linq to SQL Tools dans Visual Studio](https://docs.microsoft.com/en-us/visualstudio/data-tools/linq-to-sql-tools-in-visual-studio2).</span><span class="sxs-lookup"><span data-stu-id="a07e4-107">For more information see, [Linq to SQL Tools in Visual Studio](https://docs.microsoft.com/en-us/visualstudio/data-tools/linq-to-sql-tools-in-visual-studio2).</span></span>
  
-   <span data-ttu-id="a07e4-108">Outil en ligne de commande SQLMetal</span><span class="sxs-lookup"><span data-stu-id="a07e4-108">The SQLMetal command-line tool.</span></span> <span data-ttu-id="a07e4-109">Pour plus d’informations, consultez [SqlMetal.exe (outil de génération de code)](../../../../../../docs/framework/tools/sqlmetal-exe-code-generation-tool.md).</span><span class="sxs-lookup"><span data-stu-id="a07e4-109">For more information, see [SqlMetal.exe (Code Generation Tool)](../../../../../../docs/framework/tools/sqlmetal-exe-code-generation-tool.md).</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="a07e4-110">Si vous ne possédez pas de base de données existante et que vous souhaitez en créer une à partir d'un modèle objet, vous pouvez utiliser votre éditeur de code et <xref:System.Data.Linq.DataContext.CreateDatabase%2A>.</span><span class="sxs-lookup"><span data-stu-id="a07e4-110">If you do not have an existing database and want to create one from an object model, you can create your object model by using your code editor and <xref:System.Data.Linq.DataContext.CreateDatabase%2A>.</span></span> <span data-ttu-id="a07e4-111">Pour plus d’informations, consultez [Comment : créer dynamiquement une base de données](../../../../../../docs/framework/data/adonet/sql/linq/how-to-dynamically-create-a-database.md).</span><span class="sxs-lookup"><span data-stu-id="a07e4-111">For more information, see [How to: Dynamically Create a Database](../../../../../../docs/framework/data/adonet/sql/linq/how-to-dynamically-create-a-database.md).</span></span>  
  
 <span data-ttu-id="a07e4-112">Documentation pour le [!INCLUDE[vs_ordesigner_short](../../../../../../includes/vs-ordesigner-short-md.md)] fournit des exemples montrant comment générer un [!INCLUDE[vbprvb](../../../../../../includes/vbprvb-md.md)] ou le modèle objet c# à l’aide de la [!INCLUDE[vs_ordesigner_short](../../../../../../includes/vs-ordesigner-short-md.md)].</span><span class="sxs-lookup"><span data-stu-id="a07e4-112">Documentation for the [!INCLUDE[vs_ordesigner_short](../../../../../../includes/vs-ordesigner-short-md.md)] provides examples of how to generate a [!INCLUDE[vbprvb](../../../../../../includes/vbprvb-md.md)] or C# object model by using the [!INCLUDE[vs_ordesigner_short](../../../../../../includes/vs-ordesigner-short-md.md)].</span></span> <span data-ttu-id="a07e4-113">Les informations suivantes fournissent des exemples d'utilisation de l'outil en ligne de commande SQLMetal.</span><span class="sxs-lookup"><span data-stu-id="a07e4-113">The following information provide examples of how to use the SQLMetal command-line tool.</span></span> <span data-ttu-id="a07e4-114">Pour plus d’informations, consultez [SqlMetal.exe (outil de génération de code)](../../../../../../docs/framework/tools/sqlmetal-exe-code-generation-tool.md).</span><span class="sxs-lookup"><span data-stu-id="a07e4-114">For more information, see [SqlMetal.exe (Code Generation Tool)](../../../../../../docs/framework/tools/sqlmetal-exe-code-generation-tool.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="a07e4-115">Exemple</span><span class="sxs-lookup"><span data-stu-id="a07e4-115">Example</span></span>  
 <span data-ttu-id="a07e4-116">La ligne de commande SQLMetal présentée dans l'exemple suivant produit du code [!INCLUDE[vbprvb](../../../../../../includes/vbprvb-md.md)] comme modèle objet basé sur les attributs de l'exemple de base de données Northwind.</span><span class="sxs-lookup"><span data-stu-id="a07e4-116">The SQLMetal command line shown in the following example produces [!INCLUDE[vbprvb](../../../../../../includes/vbprvb-md.md)] code as the attribute-based object model of the Northwind sample database.</span></span> <span data-ttu-id="a07e4-117">Des procédures stockées et des fonctions sont également restituées.</span><span class="sxs-lookup"><span data-stu-id="a07e4-117">Stored procedures and functions are also rendered.</span></span>  
  
```  
sqlmetal /code:northwind.vb /language:vb "c:\northwnd.mdf" /sprocs /functions  
```  
  
## <a name="example"></a><span data-ttu-id="a07e4-118">Exemple</span><span class="sxs-lookup"><span data-stu-id="a07e4-118">Example</span></span>  
 <span data-ttu-id="a07e4-119">La ligne de commande SQLMetal présentée dans l'exemple suivant produit du code C# comme modèle objet basé sur les attributs de l'exemple de base de données Northwind.</span><span class="sxs-lookup"><span data-stu-id="a07e4-119">The SQLMetal command line shown in the following example produces C# code as the attribute-based object model of the Northwind sample database.</span></span> <span data-ttu-id="a07e4-120">Des procédures stockées et des fonctions sont également restituées, et les noms de table sont automatiquement pluralisés.</span><span class="sxs-lookup"><span data-stu-id="a07e4-120">Stored procedures and functions are also rendered, and table names are automatically pluralized.</span></span>  
  
```  
sqlmetal /code:northwind.cs /language:csharp "c:\northwnd.mdf" /sprocs /functions /pluralize  
```  
  
## <a name="see-also"></a><span data-ttu-id="a07e4-121">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="a07e4-121">See Also</span></span>  
 [<span data-ttu-id="a07e4-122">Guide de programmation</span><span class="sxs-lookup"><span data-stu-id="a07e4-122">Programming Guide</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/programming-guide.md)  
 [<span data-ttu-id="a07e4-123">Modèle objet LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="a07e4-123">The LINQ to SQL Object Model</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/the-linq-to-sql-object-model.md)  
 [<span data-ttu-id="a07e4-124">Apprentissage par les procédures pas à pas</span><span class="sxs-lookup"><span data-stu-id="a07e4-124">Learning by Walkthroughs</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/learning-by-walkthroughs.md)  
 [<span data-ttu-id="a07e4-125">Guide pratique pour personnaliser des classes d’entité à l’aide de l’éditeur de code</span><span class="sxs-lookup"><span data-stu-id="a07e4-125">How to: Customize Entity Classes by Using the Code Editor</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-customize-entity-classes-by-using-the-code-editor.md)  
 [<span data-ttu-id="a07e4-126">Mappage basé sur les attributs</span><span class="sxs-lookup"><span data-stu-id="a07e4-126">Attribute-Based Mapping</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/attribute-based-mapping.md)  
 [<span data-ttu-id="a07e4-127">SqlMetal.exe (outil de génération de code)</span><span class="sxs-lookup"><span data-stu-id="a07e4-127">SqlMetal.exe (Code Generation Tool)</span></span>](../../../../../../docs/framework/tools/sqlmetal-exe-code-generation-tool.md)  
 [<span data-ttu-id="a07e4-128">Mappage externe</span><span class="sxs-lookup"><span data-stu-id="a07e4-128">External Mapping</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/external-mapping.md)  
 [<span data-ttu-id="a07e4-129">Téléchargement d’exemples de base de données</span><span class="sxs-lookup"><span data-stu-id="a07e4-129">Downloading Sample Databases</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/downloading-sample-databases.md)  
 [<span data-ttu-id="a07e4-130">Création du modèle objet</span><span class="sxs-lookup"><span data-stu-id="a07e4-130">Creating the Object Model</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/creating-the-object-model.md)
