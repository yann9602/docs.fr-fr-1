---
title: "Procédure pas à pas : manipulation de données (Visual Basic)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: vb
ms.assetid: 1f6a54f6-ec33-452a-a37d-48122207bf14
caps.latest.revision: "2"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: b4bc7baee8e95243cf05a52f49c37aa2d8916666
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/17/2018
---
# <a name="walkthrough-manipulating-data-visual-basic"></a><span data-ttu-id="870c8-102">Procédure pas à pas : manipulation de données (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="870c8-102">Walkthrough: Manipulating Data (Visual Basic)</span></span>
<span data-ttu-id="870c8-103">Cette procédure pas à pas fournit un scénario [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] complet essentiel pour l'ajout, la modification et la suppression de données dans une base de données.</span><span class="sxs-lookup"><span data-stu-id="870c8-103">This walkthrough provides a fundamental end-to-end [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] scenario for adding, modifying, and deleting data in a database.</span></span> <span data-ttu-id="870c8-104">Vous utiliserez une copie de l'exemple de base de données Northwind pour ajouter un client, modifier le nom d'un client et supprimer une commande.</span><span class="sxs-lookup"><span data-stu-id="870c8-104">You will use a copy of the sample Northwind database to add a customer, change the name of a customer, and delete an order.</span></span>  
  
 [!INCLUDE[note_settings_general](../../../../../../includes/note-settings-general-md.md)]  
  
 <span data-ttu-id="870c8-105">Cette procédure pas à pas a été écrite à l'aide des paramètres de développement Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="870c8-105">This walkthrough was written by using Visual Basic Development Settings.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="870c8-106">Prérequis</span><span class="sxs-lookup"><span data-stu-id="870c8-106">Prerequisites</span></span>  
 <span data-ttu-id="870c8-107">Elle requiert les éléments suivants :</span><span class="sxs-lookup"><span data-stu-id="870c8-107">This walkthrough requires the following:</span></span>  
  
-   <span data-ttu-id="870c8-108">Les fichiers sont stockés dans un dossier dédié, c:\linqtest2.</span><span class="sxs-lookup"><span data-stu-id="870c8-108">This walkthrough uses a dedicated folder ("c:\linqtest2") to hold files.</span></span> <span data-ttu-id="870c8-109">Vous devez créer ce dossier avant de commencer la procédure pas à pas.</span><span class="sxs-lookup"><span data-stu-id="870c8-109">Create this folder before you begin the walkthrough.</span></span>  
  
-   <span data-ttu-id="870c8-110">Exemple de base de données Northwind.</span><span class="sxs-lookup"><span data-stu-id="870c8-110">The Northwind sample database.</span></span>  
  
     <span data-ttu-id="870c8-111">Si cette base de données n'est pas disponible sur votre ordinateur de développement, vous pouvez la télécharger à partir du site de téléchargement Microsoft.</span><span class="sxs-lookup"><span data-stu-id="870c8-111">If you do not have this database on your development computer, you can download it from the Microsoft download site.</span></span> <span data-ttu-id="870c8-112">Pour obtenir des instructions, consultez [téléchargement d’exemples de bases de données](../../../../../../docs/framework/data/adonet/sql/linq/downloading-sample-databases.md).</span><span class="sxs-lookup"><span data-stu-id="870c8-112">For instructions, see [Downloading Sample Databases](../../../../../../docs/framework/data/adonet/sql/linq/downloading-sample-databases.md).</span></span> <span data-ttu-id="870c8-113">Après avoir téléchargé la base de données, copiez le fichier northwnd.mdf dans le dossier c:\linqtest2.</span><span class="sxs-lookup"><span data-stu-id="870c8-113">After you have downloaded the database, copy the northwnd.mdf file to the c:\linqtest2 folder.</span></span>  
  
-   <span data-ttu-id="870c8-114">Fichier de code Visual Basic généré à partir de la base de données Northwind.</span><span class="sxs-lookup"><span data-stu-id="870c8-114">A Visual Basic code file generated from the Northwind database.</span></span>  
  
     <span data-ttu-id="870c8-115">Vous pouvez générer ce fichier à l'aide du [!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)] ou de l'outil SQLMetal.</span><span class="sxs-lookup"><span data-stu-id="870c8-115">You can generate this file by using either the [!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)] or the SQLMetal tool.</span></span> <span data-ttu-id="870c8-116">Cette procédure pas à pas a été écrite à l'aide de l'outil SQLMetal, avec la ligne de commande suivante :</span><span class="sxs-lookup"><span data-stu-id="870c8-116">This walkthrough was written by using the SQLMetal tool with the following command line:</span></span>  
  
     <span data-ttu-id="870c8-117">**sqlmetal /code:"c:\linqtest2\northwind.vb" /language:vb "C:\linqtest2\northwnd.mdf" /pluralize**</span><span class="sxs-lookup"><span data-stu-id="870c8-117">**sqlmetal /code:"c:\linqtest2\northwind.vb" /language:vb "C:\linqtest2\northwnd.mdf" /pluralize**</span></span>  
  
     <span data-ttu-id="870c8-118">Pour plus d’informations, consultez [SqlMetal.exe (outil de génération de code)](../../../../../../docs/framework/tools/sqlmetal-exe-code-generation-tool.md).</span><span class="sxs-lookup"><span data-stu-id="870c8-118">For more information, see [SqlMetal.exe (Code Generation Tool)](../../../../../../docs/framework/tools/sqlmetal-exe-code-generation-tool.md).</span></span>  
  
## <a name="overview"></a><span data-ttu-id="870c8-119">Vue d'ensemble</span><span class="sxs-lookup"><span data-stu-id="870c8-119">Overview</span></span>  
 <span data-ttu-id="870c8-120">Cette procédure pas à pas se compose de six tâches principales :</span><span class="sxs-lookup"><span data-stu-id="870c8-120">This walkthrough consists of six main tasks:</span></span>  
  
-   <span data-ttu-id="870c8-121">Création de la solution [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] dans [!INCLUDE[vs_current_short](../../../../../../includes/vs-current-short-md.md)].</span><span class="sxs-lookup"><span data-stu-id="870c8-121">Creating the [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] solution in [!INCLUDE[vs_current_short](../../../../../../includes/vs-current-short-md.md)].</span></span>  
  
-   <span data-ttu-id="870c8-122">Ajout du fichier de code de base de données au projet.</span><span class="sxs-lookup"><span data-stu-id="870c8-122">Adding the database code file to the project.</span></span>  
  
-   <span data-ttu-id="870c8-123">Création d'un objet représentant un client.</span><span class="sxs-lookup"><span data-stu-id="870c8-123">Creating a new customer object.</span></span>  
  
-   <span data-ttu-id="870c8-124">Modification du nom de contact d'un client.</span><span class="sxs-lookup"><span data-stu-id="870c8-124">Modifying the contact name of a customer.</span></span>  
  
-   <span data-ttu-id="870c8-125">Suppression d'une commande.</span><span class="sxs-lookup"><span data-stu-id="870c8-125">Deleting an order.</span></span>  
  
-   <span data-ttu-id="870c8-126">Soumission de ces modifications à la base de données Northwind.</span><span class="sxs-lookup"><span data-stu-id="870c8-126">Submitting these changes to the Northwind database.</span></span>  
  
## <a name="creating-a-linq-to-sql-solution"></a><span data-ttu-id="870c8-127">Création d'une solution LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="870c8-127">Creating a LINQ to SQL Solution</span></span>  
 <span data-ttu-id="870c8-128">Au cours de cette première tâche, vous allez créer une solution [!INCLUDE[vs_current_short](../../../../../../includes/vs-current-short-md.md)] qui contient les références nécessaires pour générer et exécuter un projet [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].</span><span class="sxs-lookup"><span data-stu-id="870c8-128">In this first task, you create a [!INCLUDE[vs_current_short](../../../../../../includes/vs-current-short-md.md)] solution that contains the necessary references to build and run a [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] project.</span></span>  
  
#### <a name="to-create-a-linq-to-sql-solution"></a><span data-ttu-id="870c8-129">Pour créer une solution LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="870c8-129">To create a LINQ to SQL solution</span></span>  
  
1.  <span data-ttu-id="870c8-130">Sur le [!INCLUDE[vs_current_short](../../../../../../includes/vs-current-short-md.md)] **fichier** menu, cliquez sur **nouveau projet**.</span><span class="sxs-lookup"><span data-stu-id="870c8-130">On the [!INCLUDE[vs_current_short](../../../../../../includes/vs-current-short-md.md)] **File** menu, click **New Project**.</span></span>  
  
2.  <span data-ttu-id="870c8-131">Dans le **types de projet** volet dans le **nouveau projet** boîte de dialogue, cliquez sur **Visual Basic**.</span><span class="sxs-lookup"><span data-stu-id="870c8-131">In the **Project types** pane in the **New Project** dialog box, click **Visual Basic**.</span></span>  
  
3.  <span data-ttu-id="870c8-132">Dans le volet **Modèles**, cliquez sur **Application console**.</span><span class="sxs-lookup"><span data-stu-id="870c8-132">In the **Templates** pane, click **Console Application**.</span></span>  
  
4.  <span data-ttu-id="870c8-133">Dans le **nom** , tapez **LinqDataManipulationApp**.</span><span class="sxs-lookup"><span data-stu-id="870c8-133">In the **Name** box, type **LinqDataManipulationApp**.</span></span>  
  
5.  <span data-ttu-id="870c8-134">Cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="870c8-134">Click **OK**.</span></span>  
  
## <a name="adding-linq-references-and-directives"></a><span data-ttu-id="870c8-135">Ajout de références et de directives LINQ</span><span class="sxs-lookup"><span data-stu-id="870c8-135">Adding LINQ References and Directives</span></span>  
 <span data-ttu-id="870c8-136">Cette procédure pas à pas utilise des assemblys qui ne sont pas nécessairement installés par défaut dans votre projet.</span><span class="sxs-lookup"><span data-stu-id="870c8-136">This walkthrough uses assemblies that might not be installed by default in your project.</span></span> <span data-ttu-id="870c8-137">Si `System.Data.Linq` n’est pas répertorié comme référence dans votre projet (cliquez sur **afficher tous les fichiers** dans **l’Explorateur de solutions** et développez le **références** nœud), ajoutez-le comme expliqué dans les étapes suivantes.</span><span class="sxs-lookup"><span data-stu-id="870c8-137">If `System.Data.Linq` is not listed as a reference in your project (click **Show All Files** in **Solution Explorer** and expand the **References** node), add it, as explained in the following steps.</span></span>  
  
#### <a name="to-add-systemdatalinq"></a><span data-ttu-id="870c8-138">Pour ajouter System.Data.Linq</span><span class="sxs-lookup"><span data-stu-id="870c8-138">To add System.Data.Linq</span></span>  
  
1.  <span data-ttu-id="870c8-139">Dans **l’Explorateur de solutions**, avec le bouton droit **références**, puis cliquez sur **ajouter une référence**.</span><span class="sxs-lookup"><span data-stu-id="870c8-139">In **Solution Explorer**, right-click **References**, and then click **Add Reference**.</span></span>  
  
2.  <span data-ttu-id="870c8-140">Dans le **ajouter une référence** boîte de dialogue, cliquez sur **.NET**et cliquez sur l’assembly System.Data.Linq, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="870c8-140">In the **Add Reference** dialog box, click **.NET**, click the System.Data.Linq assembly, and then click **OK**.</span></span>  
  
     <span data-ttu-id="870c8-141">L'assembly est ajouté au projet.</span><span class="sxs-lookup"><span data-stu-id="870c8-141">The assembly is added to the project.</span></span>  
  
3.  <span data-ttu-id="870c8-142">Dans l’éditeur de code, ajoutez les directives suivantes au-dessus **Module1**:</span><span class="sxs-lookup"><span data-stu-id="870c8-142">In the code editor, add the following directives above **Module1**:</span></span>  
  
     [!code-vb[DLinqWalk3VB#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqWalk3VB/vb/Module1.vb#1)]  
  
## <a name="adding-the-northwind-code-file-to-the-project"></a><span data-ttu-id="870c8-143">Ajout du fichier de code Northwind au projet</span><span class="sxs-lookup"><span data-stu-id="870c8-143">Adding the Northwind Code File to the Project</span></span>  
 <span data-ttu-id="870c8-144">Ces étapes supposent que vous avez utilisé l'outil SQLMetal pour générer un fichier de code à partir de l'exemple de base de données Northwind.</span><span class="sxs-lookup"><span data-stu-id="870c8-144">These steps assume that you have used the SQLMetal tool to generate a code file from the Northwind sample database.</span></span> <span data-ttu-id="870c8-145">Pour plus d'informations, consultez la section Composants requis au début de cette procédure pas à pas.</span><span class="sxs-lookup"><span data-stu-id="870c8-145">For more information, see the Prerequisites section earlier in this walkthrough.</span></span>  
  
#### <a name="to-add-the-northwind-code-file-to-the-project"></a><span data-ttu-id="870c8-146">Pour ajouter le fichier de code Northwind au projet</span><span class="sxs-lookup"><span data-stu-id="870c8-146">To add the northwind code file to the project</span></span>  
  
1.  <span data-ttu-id="870c8-147">Sur le **projet** menu, cliquez sur **ajouter un élément existant**.</span><span class="sxs-lookup"><span data-stu-id="870c8-147">On the **Project** menu, click **Add Existing Item**.</span></span>  
  
2.  <span data-ttu-id="870c8-148">Dans le **ajouter un élément existant** boîte de dialogue, accédez à c:\linqtest2\northwind.vb, puis cliquez sur **ajouter**.</span><span class="sxs-lookup"><span data-stu-id="870c8-148">In the **Add Existing Item** dialog box, navigate to c:\linqtest2\northwind.vb, and then click **Add**.</span></span>  
  
     <span data-ttu-id="870c8-149">Le fichier northwind.vb est ajouté au projet.</span><span class="sxs-lookup"><span data-stu-id="870c8-149">The northwind.vb file is added to the project.</span></span>  
  
## <a name="setting-up-the-database-connection"></a><span data-ttu-id="870c8-150">Paramétrage de la connexion de base de données</span><span class="sxs-lookup"><span data-stu-id="870c8-150">Setting Up the Database Connection</span></span>  
 <span data-ttu-id="870c8-151">Commencez par tester votre connexion à la base de données.</span><span class="sxs-lookup"><span data-stu-id="870c8-151">First, test your connection to the database.</span></span> <span data-ttu-id="870c8-152">Notez en particulier que le nom de la base de données (Northwnd) ne comporte pas de caractère i.</span><span class="sxs-lookup"><span data-stu-id="870c8-152">Note especially that the name of the database, Northwnd, has no i character.</span></span> <span data-ttu-id="870c8-153">Si vous générez des erreurs au cours des étapes suivantes, examinez le fichier northwind.vb pour déterminer comment la classe partielle Northwind est orthographiée.</span><span class="sxs-lookup"><span data-stu-id="870c8-153">If you generate errors in the next steps, review the northwind.vb file to determine how the Northwind partial class is spelled.</span></span>  
  
#### <a name="to-set-up-and-test-the-database-connection"></a><span data-ttu-id="870c8-154">Pour paramétrer et tester la connexion de base de données</span><span class="sxs-lookup"><span data-stu-id="870c8-154">To set up and test the database connection</span></span>  
  
1.  <span data-ttu-id="870c8-155">Tapez ou collez le code suivant dans `Sub Main` :</span><span class="sxs-lookup"><span data-stu-id="870c8-155">Type or paste the following code into `Sub Main`:</span></span>  
  
     [!code-vb[DLinqWalk3VB#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqWalk3VB/vb/Module1.vb#2)]  
  
2.  <span data-ttu-id="870c8-156">Appuyez sur F5 pour tester l'application à ce stade.</span><span class="sxs-lookup"><span data-stu-id="870c8-156">Press F5 to test the application at this point.</span></span>  
  
     <span data-ttu-id="870c8-157">A **Console** fenêtre s’ouvre.</span><span class="sxs-lookup"><span data-stu-id="870c8-157">A **Console** window opens.</span></span>  
  
     <span data-ttu-id="870c8-158">Fermez l’application en appuyant sur entrée dans le **Console** fenêtre, ou en cliquant sur **arrêter le débogage** sur la [!INCLUDE[vs_current_short](../../../../../../includes/vs-current-short-md.md)] **déboguer** menu.</span><span class="sxs-lookup"><span data-stu-id="870c8-158">Close the application by pressing Enter in the **Console** window, or by clicking **Stop Debugging** on the [!INCLUDE[vs_current_short](../../../../../../includes/vs-current-short-md.md)] **Debug** menu.</span></span>  
  
## <a name="creating-a-new-entity"></a><span data-ttu-id="870c8-159">Création d'une entité</span><span class="sxs-lookup"><span data-stu-id="870c8-159">Creating a New Entity</span></span>  
 <span data-ttu-id="870c8-160">La création d'une entité est une opération simple.</span><span class="sxs-lookup"><span data-stu-id="870c8-160">Creating a new entity is straightforward.</span></span> <span data-ttu-id="870c8-161">Vous pouvez créer des objets (`Customer`, par exemple) à l'aide du mot clé `New`.</span><span class="sxs-lookup"><span data-stu-id="870c8-161">You can create objects (such as `Customer`) by using the `New` keyword.</span></span>  
  
 <span data-ttu-id="870c8-162">Dans cette section et les suivantes, vous apporterez des modifications uniquement au cache local.</span><span class="sxs-lookup"><span data-stu-id="870c8-162">In this and the following sections, you are making changes only to the local cache.</span></span> <span data-ttu-id="870c8-163">Aucune modification n'est envoyée à la base de données tant que vous n'avez pas appelé <xref:System.Data.Linq.DataContext.SubmitChanges%2A> vers la fin de cette procédure pas à pas.</span><span class="sxs-lookup"><span data-stu-id="870c8-163">No changes are sent to the database until you call <xref:System.Data.Linq.DataContext.SubmitChanges%2A> toward the end of this walkthrough.</span></span>  
  
#### <a name="to-add-a-new-customer-entity-object"></a><span data-ttu-id="870c8-164">Pour ajouter un nouvel objet d'entité Customer</span><span class="sxs-lookup"><span data-stu-id="870c8-164">To add a new Customer entity object</span></span>  
  
1.  <span data-ttu-id="870c8-165">Créez un `Customer` en ajoutant le code suivant avant `Console.ReadLine` dans `Sub Main` :</span><span class="sxs-lookup"><span data-stu-id="870c8-165">Create a new `Customer` by adding the following code before `Console.ReadLine` in `Sub Main`:</span></span>  
  
     [!code-vb[DLinqWalk3VB#3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqWalk3VB/vb/Module1.vb#3)]  
  
2.  <span data-ttu-id="870c8-166">Appuyez sur F5 pour déboguer la solution.</span><span class="sxs-lookup"><span data-stu-id="870c8-166">Press F5 to debug the solution.</span></span>  
  
     <span data-ttu-id="870c8-167">Les résultats suivants s'affichent dans la fenêtre de console :</span><span class="sxs-lookup"><span data-stu-id="870c8-167">The results that are shown in the console window are as follows:</span></span>  
  
     `Customers matching CA before insert:`  
  
     `Customer ID: CACTU`  
  
     `Customer ID: RICAR`  
  
     <span data-ttu-id="870c8-168">Notez que la nouvelle ligne n'apparaît pas dans les résultats.</span><span class="sxs-lookup"><span data-stu-id="870c8-168">Note that the new row does not appear in the results.</span></span> <span data-ttu-id="870c8-169">Les nouvelles données n'ont pas encore été soumises à la base de données.</span><span class="sxs-lookup"><span data-stu-id="870c8-169">The new data has not yet been submitted to the database.</span></span>  
  
3.  <span data-ttu-id="870c8-170">Appuyez sur entrée dans le **Console** fenêtre pour arrêter le débogage.</span><span class="sxs-lookup"><span data-stu-id="870c8-170">Press Enter in the **Console** window to stop debugging.</span></span>  
  
## <a name="updating-an-entity"></a><span data-ttu-id="870c8-171">Mise à jour d'une entité</span><span class="sxs-lookup"><span data-stu-id="870c8-171">Updating an Entity</span></span>  
 <span data-ttu-id="870c8-172">Au cours des étapes suivantes, vous allez récupérer un objet `Customer` et modifier l'une de ses propriétés.</span><span class="sxs-lookup"><span data-stu-id="870c8-172">In the following steps, you will retrieve a `Customer` object and modify one of its properties.</span></span>  
  
#### <a name="to-change-the-name-of-a-customer"></a><span data-ttu-id="870c8-173">Pour modifier le nom d'un client</span><span class="sxs-lookup"><span data-stu-id="870c8-173">To change the name of a Customer</span></span>  
  
-   <span data-ttu-id="870c8-174">Ajoutez le code suivant au-dessus de `Console.ReadLine()` :</span><span class="sxs-lookup"><span data-stu-id="870c8-174">Add the following code above `Console.ReadLine()`:</span></span>  
  
     [!code-vb[DLinqWalk3VB#4](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqWalk3VB/vb/Module1.vb#4)]  
  
## <a name="deleting-an-entity"></a><span data-ttu-id="870c8-175">Suppression d'une entité</span><span class="sxs-lookup"><span data-stu-id="870c8-175">Deleting an Entity</span></span>  
 <span data-ttu-id="870c8-176">Vous pouvez supprimer la première commande à l'aide du même objet Customer.</span><span class="sxs-lookup"><span data-stu-id="870c8-176">Using the same customer object, you can delete the first order.</span></span>  
  
 <span data-ttu-id="870c8-177">Le code suivant montre comment couper les relations entre les lignes et supprimer une ligne de la base de données.</span><span class="sxs-lookup"><span data-stu-id="870c8-177">The following code demonstrates how to sever relationships between rows, and how to delete a row from the database.</span></span>  
  
#### <a name="to-delete-a-row"></a><span data-ttu-id="870c8-178">Pour supprimer une ligne</span><span class="sxs-lookup"><span data-stu-id="870c8-178">To delete a row</span></span>  
  
-   <span data-ttu-id="870c8-179">Ajoutez le code suivant juste au-dessus de `Console.ReadLine()` :</span><span class="sxs-lookup"><span data-stu-id="870c8-179">Add the following code just above `Console.ReadLine()`:</span></span>  
  
     [!code-vb[DLinqWalk3VB#5](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqWalk3VB/vb/Module1.vb#5)]  
  
## <a name="submitting-changes-to-the-database"></a><span data-ttu-id="870c8-180">Soumission des modifications à la base de données</span><span class="sxs-lookup"><span data-stu-id="870c8-180">Submitting Changes to the Database</span></span>  
 <span data-ttu-id="870c8-181">La dernière étape requise pour la création, la mise à jour et la suppression d'objets consiste à soumettre les modifications à la base de données.</span><span class="sxs-lookup"><span data-stu-id="870c8-181">The final step required for creating, updating, and deleting objects is to actually submit the changes to the database.</span></span> <span data-ttu-id="870c8-182">Sans cette étape, vos modifications restent locales et n'apparaissent pas dans les résultats de requêtes.</span><span class="sxs-lookup"><span data-stu-id="870c8-182">Without this step, your changes are only local and will not appear in query results.</span></span>  
  
#### <a name="to-submit-changes-to-the-database"></a><span data-ttu-id="870c8-183">Pour soumettre les modifications à la base de données</span><span class="sxs-lookup"><span data-stu-id="870c8-183">To submit changes to the database</span></span>  
  
1.  <span data-ttu-id="870c8-184">Insérez le code suivant juste au-dessus de `Console.ReadLine` :</span><span class="sxs-lookup"><span data-stu-id="870c8-184">Insert the following code just above `Console.ReadLine`:</span></span>  
  
     [!code-vb[DLinqWalk3VB#6](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqWalk3VB/vb/Module1.vb#6)]  
  
2.  <span data-ttu-id="870c8-185">Insérez le code suivant (après `SubmitChanges`) pour afficher les effets avant/après de la soumission des modifications :</span><span class="sxs-lookup"><span data-stu-id="870c8-185">Insert the following code (after `SubmitChanges`) to show the before and after effects of submitting the changes:</span></span>  
  
     [!code-vb[DLinqWalk3VB#7](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqWalk3VB/vb/Module1.vb#7)]  
  
3.  <span data-ttu-id="870c8-186">Appuyez sur F5 pour déboguer la solution.</span><span class="sxs-lookup"><span data-stu-id="870c8-186">Press F5 to debug the solution.</span></span>  
  
     <span data-ttu-id="870c8-187">La fenêtre de console se présente comme suit :</span><span class="sxs-lookup"><span data-stu-id="870c8-187">The console window appears as follows:</span></span>  
  
    ```  
    Customers matching CA before update:  
    Customer ID: CACTU  
    Customer ID: RICAR  
  
    The Order Detail to be deleted is: OrderID = 10643  
  
    Customers matching CA after update:  
    Customer ID: A3VCA  
    Customer ID: CACTU  
    Customer ID: RICAR  
    ```  
  
4.  <span data-ttu-id="870c8-188">Appuyez sur entrée dans le **Console** fenêtre pour arrêter le débogage.</span><span class="sxs-lookup"><span data-stu-id="870c8-188">Press Enter in the **Console** window to stop debugging.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="870c8-189">Une fois que vous avez soumis les modifications (ajouté le nouveau client), vous ne pouvez plus exécuter cette solution telle quelle car vous ne pouvez plus ajouter le même client tel quel.</span><span class="sxs-lookup"><span data-stu-id="870c8-189">After you have added the new customer by submitting the changes, you cannot execute this solution again as is, because you cannot add the same customer again as is.</span></span> <span data-ttu-id="870c8-190">Pour exécuter à nouveau la solution, modifiez la valeur de l'ID client à ajouter.</span><span class="sxs-lookup"><span data-stu-id="870c8-190">To execute the solution again, change the value of the customer ID to be added.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="870c8-191">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="870c8-191">See Also</span></span>  
 [<span data-ttu-id="870c8-192">Apprentissage par les procédures pas à pas</span><span class="sxs-lookup"><span data-stu-id="870c8-192">Learning by Walkthroughs</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/learning-by-walkthroughs.md)
