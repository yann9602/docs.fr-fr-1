---
title: "Comment : valider des fichiers de mappage externes et DBML"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d9ea37f5-0a9e-4401-8fc3-1e6fd44c49f9
caps.latest.revision: "2"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: 7724586c33c19654c3657a5a4604a3c74f2c8756
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/17/2018
---
# <a name="how-to-validate-dbml-and-external-mapping-files"></a><span data-ttu-id="bf353-102">Comment : valider des fichiers de mappage externes et DBML</span><span class="sxs-lookup"><span data-stu-id="bf353-102">How to: Validate DBML and External Mapping Files</span></span>
<span data-ttu-id="bf353-103">Les fichiers de mappage externes et les fichiers .dbml que vous modifiez doivent être validés par rapport à leurs définitions de schéma respectives.</span><span class="sxs-lookup"><span data-stu-id="bf353-103">External mapping files and .dbml files that you modify must be validated against their respective schema definitions.</span></span> <span data-ttu-id="bf353-104">Cette rubrique fournit aux utilisateurs [!INCLUDE[vs_current_short](../../../../../../includes/vs-current-short-md.md)] les étapes d'implémentation du processus de validation.</span><span class="sxs-lookup"><span data-stu-id="bf353-104">This topic provides [!INCLUDE[vs_current_short](../../../../../../includes/vs-current-short-md.md)] users with the steps to implement the validation process.</span></span>  
  
 [!INCLUDE[note_settings_general](../../../../../../includes/note-settings-general-md.md)]  
  
### <a name="to-validate-a-dbml-or-xml-file"></a><span data-ttu-id="bf353-105">Pour valider un fichier .dbml ou XML</span><span class="sxs-lookup"><span data-stu-id="bf353-105">To validate a .dbml or XML file</span></span>  
  
1.  <span data-ttu-id="bf353-106">Dans Visual Studio **fichier** menu, pointez sur **ouvrir**, puis cliquez sur **fichier**.</span><span class="sxs-lookup"><span data-stu-id="bf353-106">On the Visual Studio **File** menu, point to **Open**, and then click **File**.</span></span>  
  
2.  <span data-ttu-id="bf353-107">Dans le **ouvrir le fichier** boîte de dialogue, cliquez sur le fichier .dbml ou le fichier de mappage XML que vous souhaitez valider.</span><span class="sxs-lookup"><span data-stu-id="bf353-107">In the **Open File** dialog box, click the .dbml or XML mapping file that you want to validate.</span></span>  
  
     <span data-ttu-id="bf353-108">Le fichier s’ouvre dans le **éditeur XML**.</span><span class="sxs-lookup"><span data-stu-id="bf353-108">The file opens in the **XML Editor**.</span></span>  
  
3.  <span data-ttu-id="bf353-109">Avec le bouton droit de la fenêtre, puis cliquez sur **propriétés**.</span><span class="sxs-lookup"><span data-stu-id="bf353-109">Right-click the window, and then click **Properties**.</span></span>  
  
4.  <span data-ttu-id="bf353-110">Dans le **propriétés** fenêtre, cliquez sur le bouton de sélection pour la **schémas** propriété.</span><span class="sxs-lookup"><span data-stu-id="bf353-110">In the **Properties** window, click the ellipsis for the **Schemas** property.</span></span>  
  
     <span data-ttu-id="bf353-111">Le **schémas XML** boîte de dialogue s’ouvre.</span><span class="sxs-lookup"><span data-stu-id="bf353-111">The **XML Schemas** dialog box opens.</span></span>  
  
5.  <span data-ttu-id="bf353-112">Notez la définition de schéma en fonction de vos besoins.</span><span class="sxs-lookup"><span data-stu-id="bf353-112">Note the appropriate schema definition for your purpose.</span></span>  
  
    -   <span data-ttu-id="bf353-113">DbmlSchema.xsd est la définition de schéma pour valider un fichier .dbml.</span><span class="sxs-lookup"><span data-stu-id="bf353-113">DbmlSchema.xsd is the schema definition for validating a .dbml file.</span></span> <span data-ttu-id="bf353-114">Pour plus d’informations, consultez [la génération de Code dans LINQ to SQL](../../../../../../docs/framework/data/adonet/sql/linq/code-generation-in-linq-to-sql.md).</span><span class="sxs-lookup"><span data-stu-id="bf353-114">For more information, see [Code Generation in LINQ to SQL](../../../../../../docs/framework/data/adonet/sql/linq/code-generation-in-linq-to-sql.md).</span></span>  
  
    -   <span data-ttu-id="bf353-115">LinqToSqlMapping.xsd est la définition de schéma pour valider un fichier mappage XML externe.</span><span class="sxs-lookup"><span data-stu-id="bf353-115">LinqToSqlMapping.xsd is the schema definition for validating an external XML mapping file.</span></span> <span data-ttu-id="bf353-116">Pour plus d’informations, consultez [mappage externe](../../../../../../docs/framework/data/adonet/sql/linq/external-mapping.md).</span><span class="sxs-lookup"><span data-stu-id="bf353-116">For more information, see [External Mapping](../../../../../../docs/framework/data/adonet/sql/linq/external-mapping.md).</span></span>  
  
6.  <span data-ttu-id="bf353-117">Dans le **utilisez** colonne de la ligne de définition de schéma de votre choix, cliquez pour ouvrir la zone de liste déroulante, puis cliquez sur **utiliser ce schéma**.</span><span class="sxs-lookup"><span data-stu-id="bf353-117">In the **Use** column of the desired schema definition row, click to open the drop-down box, and then click **Use this schema**.</span></span>  
  
     <span data-ttu-id="bf353-118">Le fichier de définition de schéma est maintenant associé à votre fichier DBML ou votre fichier mappage XML.</span><span class="sxs-lookup"><span data-stu-id="bf353-118">The schema definition file is now associated with your DBML or XML mapping file.</span></span>  
  
     <span data-ttu-id="bf353-119">Assurez-vous qu'aucune autre définition de schéma n'est sélectionnée.</span><span class="sxs-lookup"><span data-stu-id="bf353-119">Make sure no other schema definitions are selected.</span></span>  
  
7.  <span data-ttu-id="bf353-120">Sur le **vue** menu, cliquez sur **liste d’erreurs**.</span><span class="sxs-lookup"><span data-stu-id="bf353-120">On the **View** menu, click **Error List**.</span></span>  
  
     <span data-ttu-id="bf353-121">Déterminez si des erreurs, avertissements ou messages ont été générés.</span><span class="sxs-lookup"><span data-stu-id="bf353-121">Determine whether errors, warnings, or messages have been generated.</span></span> <span data-ttu-id="bf353-122">Si ce n'est pas le cas, le fichier XML est valide par rapport à la définition de schéma.</span><span class="sxs-lookup"><span data-stu-id="bf353-122">If not, the XML file is valid against the schema definition.</span></span>  
  
## <a name="alternate-method-for-supplying-schema-definition"></a><span data-ttu-id="bf353-123">Méthode alternative pour fournir la définition de schéma</span><span class="sxs-lookup"><span data-stu-id="bf353-123">Alternate Method for Supplying Schema Definition</span></span>  
 <span data-ttu-id="bf353-124">Si pour une raison quelconque le .xsd approprié fichier n’apparaît pas dans le **schémas XML** boîte de dialogue, vous pouvez télécharger le fichier .xsd à partir d’une rubrique d’aide.</span><span class="sxs-lookup"><span data-stu-id="bf353-124">If for some reason the appropriate .xsd file does not appear in the **XML Schemas** dialog box, you can download the .xsd file from a Help topic.</span></span> <span data-ttu-id="bf353-125">Les étapes suivantes vous aident à enregistrer le fichier téléchargé dans le format Unicode requis par l'Éditeur XML [!INCLUDE[vs_current_short](../../../../../../includes/vs-current-short-md.md)].</span><span class="sxs-lookup"><span data-stu-id="bf353-125">The following steps help you save the downloaded file in the Unicode format required by the [!INCLUDE[vs_current_short](../../../../../../includes/vs-current-short-md.md)] XML Editor.</span></span>  
  
#### <a name="to-copy-a-schema-definition-file-from-a-help-topic"></a><span data-ttu-id="bf353-126">Pour copier un fichier de définition de schéma à partir d'une rubrique d'aide</span><span class="sxs-lookup"><span data-stu-id="bf353-126">To copy a schema definition file from a Help topic</span></span>  
  
1.  <span data-ttu-id="bf353-127">Recherchez la rubrique d'aide qui contient la définition de schéma comme décrit précédemment dans cette rubrique.</span><span class="sxs-lookup"><span data-stu-id="bf353-127">Locate the Help topic that contains the schema definition as described earlier in this topic.</span></span>  
  
    -   <span data-ttu-id="bf353-128">Pour les fichiers .dbml, consultez [la génération de Code dans LINQ to SQL](../../../../../../docs/framework/data/adonet/sql/linq/code-generation-in-linq-to-sql.md).</span><span class="sxs-lookup"><span data-stu-id="bf353-128">For .dbml files, see [Code Generation in LINQ to SQL](../../../../../../docs/framework/data/adonet/sql/linq/code-generation-in-linq-to-sql.md).</span></span>  
  
    -   <span data-ttu-id="bf353-129">Pour les fichiers de mappage externe, consultez [mappage externe](../../../../../../docs/framework/data/adonet/sql/linq/external-mapping.md).</span><span class="sxs-lookup"><span data-stu-id="bf353-129">For external mapping files, see [External Mapping](../../../../../../docs/framework/data/adonet/sql/linq/external-mapping.md).</span></span>  
  
2.  <span data-ttu-id="bf353-130">Cliquez sur **copier le Code** pour copier le fichier de code dans le Presse-papiers.</span><span class="sxs-lookup"><span data-stu-id="bf353-130">Click **Copy Code** to copy the code file to the Clipboard.</span></span>  
  
3.  <span data-ttu-id="bf353-131">Lancez le Bloc-notes pour créer un nouveau fichier.</span><span class="sxs-lookup"><span data-stu-id="bf353-131">Start Notepad to create a new file.</span></span>  
  
4.  <span data-ttu-id="bf353-132">Collez le code du Presse-papiers dans un fichier Bloc-notes.</span><span class="sxs-lookup"><span data-stu-id="bf353-132">Paste the code from the clipboard into Notepad file.</span></span>  
  
5.  <span data-ttu-id="bf353-133">Dans le bloc-notes **fichier** menu, cliquez sur **Enregistrer sous**.</span><span class="sxs-lookup"><span data-stu-id="bf353-133">On the Notepad **File** menu, click **Save As**.</span></span>  
  
6.  <span data-ttu-id="bf353-134">Dans le **codage** boîte, sélectionnez **Unicode**.</span><span class="sxs-lookup"><span data-stu-id="bf353-134">In the **Encoding** box, select **Unicode**.</span></span>  
  
    > [!IMPORTANT]
    >  <span data-ttu-id="bf353-135">Cette sélection garantit que le marqueur d'ordre d'octet Unicode 16 bits (`FFFE`) est ajouté au fichier texte.</span><span class="sxs-lookup"><span data-stu-id="bf353-135">This selection guarantees that the Unicode-16 byte-order marker (`FFFE`) is prepended to the text file.</span></span>  
  
7.  <span data-ttu-id="bf353-136">Dans le **nom de fichier** zone, créez un nom de fichier avec une extension .xsd.</span><span class="sxs-lookup"><span data-stu-id="bf353-136">In the **File name** box, create a file name with an .xsd extension.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bf353-137">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="bf353-137">See Also</span></span>  
 [<span data-ttu-id="bf353-138">Référence</span><span class="sxs-lookup"><span data-stu-id="bf353-138">Reference</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/reference.md)
