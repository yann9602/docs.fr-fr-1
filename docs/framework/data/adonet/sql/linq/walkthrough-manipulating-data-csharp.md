---
title: "Procédure pas à pas : manipulation de données (C#)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 24adfbe0-0ad6-449f-997d-8808e0770d2e
caps.latest.revision: "2"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: ac02ea6c07797c600fe9ce9c7b197a95fc84da61
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="walkthrough-manipulating-data-c"></a><span data-ttu-id="ff8fd-102">Procédure pas à pas : manipulation de données (C#)</span><span class="sxs-lookup"><span data-stu-id="ff8fd-102">Walkthrough: Manipulating Data (C#)</span></span>
<span data-ttu-id="ff8fd-103">Cette procédure pas à pas fournit un scénario [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] complet essentiel pour l'ajout, la modification et la suppression de données dans une base de données.</span><span class="sxs-lookup"><span data-stu-id="ff8fd-103">This walkthrough provides a fundamental end-to-end [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] scenario for adding, modifying, and deleting data in a database.</span></span> <span data-ttu-id="ff8fd-104">Vous utiliserez une copie de l'exemple de base de données Northwind pour ajouter un client, modifier le nom d'un client et supprimer une commande.</span><span class="sxs-lookup"><span data-stu-id="ff8fd-104">You will use a copy of the sample Northwind database to add a customer, change the name of a customer, and delete an order.</span></span>  
  
 [!INCLUDE[note_settings_general](../../../../../../includes/note-settings-general-md.md)]  
  
 <span data-ttu-id="ff8fd-105">Cette procédure pas à pas a été écrite à l'aide des paramètres de développement Visual C#.</span><span class="sxs-lookup"><span data-stu-id="ff8fd-105">This walkthrough was written by using Visual C# Development Settings.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="ff8fd-106">Prérequis</span><span class="sxs-lookup"><span data-stu-id="ff8fd-106">Prerequisites</span></span>  
 <span data-ttu-id="ff8fd-107">Elle requiert les éléments suivants :</span><span class="sxs-lookup"><span data-stu-id="ff8fd-107">This walkthrough requires the following:</span></span>  
  
-   <span data-ttu-id="ff8fd-108">Les fichiers sont stockés dans un dossier dédié, c:\linqtest6.</span><span class="sxs-lookup"><span data-stu-id="ff8fd-108">This walkthrough uses a dedicated folder ("c:\linqtest6") to hold files.</span></span> <span data-ttu-id="ff8fd-109">Vous devez créer ce dossier avant de commencer la procédure pas à pas.</span><span class="sxs-lookup"><span data-stu-id="ff8fd-109">Create this folder before you begin the walkthrough.</span></span>  
  
-   <span data-ttu-id="ff8fd-110">Exemple de base de données Northwind.</span><span class="sxs-lookup"><span data-stu-id="ff8fd-110">The Northwind sample database.</span></span>  
  
     <span data-ttu-id="ff8fd-111">Si cette base de données n'est pas disponible sur votre ordinateur de développement, vous pouvez la télécharger à partir du site de téléchargement Microsoft.</span><span class="sxs-lookup"><span data-stu-id="ff8fd-111">If you do not have this database on your development computer, you can download it from the Microsoft download site.</span></span> <span data-ttu-id="ff8fd-112">Pour obtenir des instructions, consultez [téléchargement d’exemples de bases de données](../../../../../../docs/framework/data/adonet/sql/linq/downloading-sample-databases.md).</span><span class="sxs-lookup"><span data-stu-id="ff8fd-112">For instructions, see [Downloading Sample Databases](../../../../../../docs/framework/data/adonet/sql/linq/downloading-sample-databases.md).</span></span> <span data-ttu-id="ff8fd-113">Après avoir téléchargé la base de données, copiez le fichier northwnd.mdf dans le dossier c:\linqtest6.</span><span class="sxs-lookup"><span data-stu-id="ff8fd-113">After you have downloaded the database, copy the northwnd.mdf file to the c:\linqtest6 folder.</span></span>  
  
-   <span data-ttu-id="ff8fd-114">Fichier de code C# généré à partir de la base de données Northwind.</span><span class="sxs-lookup"><span data-stu-id="ff8fd-114">A C# code file generated from the Northwind database.</span></span>  
  
     <span data-ttu-id="ff8fd-115">Vous pouvez générer ce fichier à l'aide du [!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)] ou de l'outil SQLMetal.</span><span class="sxs-lookup"><span data-stu-id="ff8fd-115">You can generate this file by using either the [!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)] or the SQLMetal tool.</span></span> <span data-ttu-id="ff8fd-116">Cette procédure pas à pas a été écrite à l'aide de l'outil SQLMetal, avec la ligne de commande suivante :</span><span class="sxs-lookup"><span data-stu-id="ff8fd-116">This walkthrough was written by using the SQLMetal tool with the following command line:</span></span>  
  
     <span data-ttu-id="ff8fd-117">**SqlMetal /code:"c:\linqtest6\northwind.cs » / Language : CSharp « C:\linqtest6\northwnd.mdf » / au pluriel**</span><span class="sxs-lookup"><span data-stu-id="ff8fd-117">**sqlmetal /code:"c:\linqtest6\northwind.cs" /language:csharp "C:\linqtest6\northwnd.mdf" /pluralize**</span></span>  
  
     <span data-ttu-id="ff8fd-118">Pour plus d’informations, consultez [SqlMetal.exe (outil de génération de code)](../../../../../../docs/framework/tools/sqlmetal-exe-code-generation-tool.md).</span><span class="sxs-lookup"><span data-stu-id="ff8fd-118">For more information, see [SqlMetal.exe (Code Generation Tool)](../../../../../../docs/framework/tools/sqlmetal-exe-code-generation-tool.md).</span></span>  
  
## <a name="overview"></a><span data-ttu-id="ff8fd-119">Vue d'ensemble</span><span class="sxs-lookup"><span data-stu-id="ff8fd-119">Overview</span></span>  
 <span data-ttu-id="ff8fd-120">Cette procédure pas à pas se compose de six tâches principales :</span><span class="sxs-lookup"><span data-stu-id="ff8fd-120">This walkthrough consists of six main tasks:</span></span>  
  
-   <span data-ttu-id="ff8fd-121">Création de la solution [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] dans [!INCLUDE[vs_current_short](../../../../../../includes/vs-current-short-md.md)].</span><span class="sxs-lookup"><span data-stu-id="ff8fd-121">Creating the [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] solution in [!INCLUDE[vs_current_short](../../../../../../includes/vs-current-short-md.md)].</span></span>  
  
-   <span data-ttu-id="ff8fd-122">Ajout du fichier de code de base de données au projet.</span><span class="sxs-lookup"><span data-stu-id="ff8fd-122">Adding the database code file to the project.</span></span>  
  
-   <span data-ttu-id="ff8fd-123">Création d'un objet représentant un client.</span><span class="sxs-lookup"><span data-stu-id="ff8fd-123">Creating a new customer object.</span></span>  
  
-   <span data-ttu-id="ff8fd-124">Modification du nom de contact d'un client.</span><span class="sxs-lookup"><span data-stu-id="ff8fd-124">Modifying the contact name of a customer.</span></span>  
  
-   <span data-ttu-id="ff8fd-125">Suppression d'une commande.</span><span class="sxs-lookup"><span data-stu-id="ff8fd-125">Deleting an order.</span></span>  
  
-   <span data-ttu-id="ff8fd-126">Soumission de ces modifications à la base de données Northwind.</span><span class="sxs-lookup"><span data-stu-id="ff8fd-126">Submitting these changes to the Northwind database.</span></span>  
  
## <a name="creating-a-linq-to-sql-solution"></a><span data-ttu-id="ff8fd-127">Création d'une solution LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="ff8fd-127">Creating a LINQ to SQL Solution</span></span>  
 <span data-ttu-id="ff8fd-128">Au cours de cette première tâche, vous allez créer une solution [!INCLUDE[vs_current_short](../../../../../../includes/vs-current-short-md.md)] qui contient les références nécessaires pour générer et exécuter un projet [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].</span><span class="sxs-lookup"><span data-stu-id="ff8fd-128">In this first task, you create a [!INCLUDE[vs_current_short](../../../../../../includes/vs-current-short-md.md)] solution that contains the necessary references to build and run a [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] project.</span></span>  
  
#### <a name="to-create-a-linq-to-sql-solution"></a><span data-ttu-id="ff8fd-129">Pour créer une solution LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="ff8fd-129">To create a LINQ to SQL solution</span></span>  
  
1.  <span data-ttu-id="ff8fd-130">Sur le [!INCLUDE[vs_current_short](../../../../../../includes/vs-current-short-md.md)] **fichier** menu, pointez sur **nouveau**, puis cliquez sur **projet**.</span><span class="sxs-lookup"><span data-stu-id="ff8fd-130">On the [!INCLUDE[vs_current_short](../../../../../../includes/vs-current-short-md.md)] **File** menu, point to **New**, and then click **Project**.</span></span>  
  
2.  <span data-ttu-id="ff8fd-131">Dans le **types de projet** volet dans le **nouveau projet** boîte de dialogue, cliquez sur **Visual C#**.</span><span class="sxs-lookup"><span data-stu-id="ff8fd-131">In the **Project types** pane in the **New Project** dialog box, click **Visual C#**.</span></span>  
  
3.  <span data-ttu-id="ff8fd-132">Dans le volet **Modèles**, cliquez sur **Application console**.</span><span class="sxs-lookup"><span data-stu-id="ff8fd-132">In the **Templates** pane, click **Console Application**.</span></span>  
  
4.  <span data-ttu-id="ff8fd-133">Dans le **nom** , tapez **LinqDataManipulationApp**.</span><span class="sxs-lookup"><span data-stu-id="ff8fd-133">In the **Name** box, type **LinqDataManipulationApp**.</span></span>  
  
5.  <span data-ttu-id="ff8fd-134">Dans le **emplacement** , vérifiez où vous souhaitez stocker vos fichiers projet.</span><span class="sxs-lookup"><span data-stu-id="ff8fd-134">In the **Location** box, verify where you want to store your project files.</span></span>  
  
6.  <span data-ttu-id="ff8fd-135">Cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="ff8fd-135">Click **OK**.</span></span>  
  
## <a name="adding-linq-references-and-directives"></a><span data-ttu-id="ff8fd-136">Ajout de références et de directives LINQ</span><span class="sxs-lookup"><span data-stu-id="ff8fd-136">Adding LINQ References and Directives</span></span>  
 <span data-ttu-id="ff8fd-137">Cette procédure pas à pas utilise des assemblys qui ne sont pas nécessairement installés par défaut dans votre projet.</span><span class="sxs-lookup"><span data-stu-id="ff8fd-137">This walkthrough uses assemblies that might not be installed by default in your project.</span></span> <span data-ttu-id="ff8fd-138">Si System.Data.Linq n'est pas répertorié comme une référence dans votre projet, ajoutez-le comme indiqué dans les étapes suivantes :</span><span class="sxs-lookup"><span data-stu-id="ff8fd-138">If System.Data.Linq is not listed as a reference in your project, add it, as explained in the following steps:</span></span>  
  
#### <a name="to-add-systemdatalinq"></a><span data-ttu-id="ff8fd-139">Pour ajouter System.Data.Linq</span><span class="sxs-lookup"><span data-stu-id="ff8fd-139">To add System.Data.Linq</span></span>  
  
1.  <span data-ttu-id="ff8fd-140">Dans **l’Explorateur de solutions**, avec le bouton droit **références**, puis cliquez sur **ajouter une référence**.</span><span class="sxs-lookup"><span data-stu-id="ff8fd-140">In **Solution Explorer**, right-click **References**, and then click **Add Reference**.</span></span>  
  
2.  <span data-ttu-id="ff8fd-141">Dans le **ajouter une référence** boîte de dialogue, cliquez sur **.NET**et cliquez sur l’assembly System.Data.Linq, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="ff8fd-141">In the **Add Reference** dialog box, click **.NET**, click the System.Data.Linq assembly, and then click **OK**.</span></span>  
  
     <span data-ttu-id="ff8fd-142">L'assembly est ajouté au projet.</span><span class="sxs-lookup"><span data-stu-id="ff8fd-142">The assembly is added to the project.</span></span>  
  
3.  <span data-ttu-id="ff8fd-143">Ajoutez les directives suivantes au haut de Program.cs :</span><span class="sxs-lookup"><span data-stu-id="ff8fd-143">Add the following directives at the top of Program.cs:</span></span>  
  
     [!code-csharp[DLinqWalk3CS#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqWalk3CS/cs/Program.cs#1)]  
  
## <a name="adding-the-northwind-code-file-to-the-project"></a><span data-ttu-id="ff8fd-144">Ajout du fichier de code Northwind au projet</span><span class="sxs-lookup"><span data-stu-id="ff8fd-144">Adding the Northwind Code File to the Project</span></span>  
 <span data-ttu-id="ff8fd-145">Ces étapes supposent que vous avez utilisé l'outil SQLMetal pour générer un fichier de code à partir de l'exemple de base de données Northwind.</span><span class="sxs-lookup"><span data-stu-id="ff8fd-145">These steps assume that you have used the SQLMetal tool to generate a code file from the Northwind sample database.</span></span> <span data-ttu-id="ff8fd-146">Pour plus d'informations, consultez la section Composants requis au début de cette procédure pas à pas.</span><span class="sxs-lookup"><span data-stu-id="ff8fd-146">For more information, see the Prerequisites section earlier in this walkthrough.</span></span>  
  
#### <a name="to-add-the-northwind-code-file-to-the-project"></a><span data-ttu-id="ff8fd-147">Pour ajouter le fichier de code Northwind au projet</span><span class="sxs-lookup"><span data-stu-id="ff8fd-147">To add the northwind code file to the project</span></span>  
  
1.  <span data-ttu-id="ff8fd-148">Sur le **projet** menu, cliquez sur **ajouter un élément existant**.</span><span class="sxs-lookup"><span data-stu-id="ff8fd-148">On the **Project** menu, click **Add Existing Item**.</span></span>  
  
2.  <span data-ttu-id="ff8fd-149">Dans le **ajouter un élément existant** boîte de dialogue, accédez à c:\linqtest6\northwind.cs, puis cliquez sur **ajouter**.</span><span class="sxs-lookup"><span data-stu-id="ff8fd-149">In the **Add Existing Item** dialog box, navigate to c:\linqtest6\northwind.cs, and then click **Add**.</span></span>  
  
     <span data-ttu-id="ff8fd-150">Le fichier northwind.cs est ajouté au projet.</span><span class="sxs-lookup"><span data-stu-id="ff8fd-150">The northwind.cs file is added to the project.</span></span>  
  
## <a name="setting-up-the-database-connection"></a><span data-ttu-id="ff8fd-151">Paramétrage de la connexion de base de données</span><span class="sxs-lookup"><span data-stu-id="ff8fd-151">Setting Up the Database Connection</span></span>  
 <span data-ttu-id="ff8fd-152">Commencez par tester votre connexion à la base de données.</span><span class="sxs-lookup"><span data-stu-id="ff8fd-152">First, test your connection to the database.</span></span> <span data-ttu-id="ff8fd-153">Notez en particulier que le nom de la base de données (Northwnd) ne comporte pas de caractère i.</span><span class="sxs-lookup"><span data-stu-id="ff8fd-153">Note especially that the database, Northwnd, has no i character.</span></span> <span data-ttu-id="ff8fd-154">Si vous générez des erreurs au cours des étapes suivantes, examinez le fichier northwind.cs pour déterminer comment la classe partielle Northwind est orthographiée.</span><span class="sxs-lookup"><span data-stu-id="ff8fd-154">If you generate errors in the next steps, review the northwind.cs file to determine how the Northwind partial class is spelled.</span></span>  
  
#### <a name="to-set-up-and-test-the-database-connection"></a><span data-ttu-id="ff8fd-155">Pour paramétrer et tester la connexion de base de données</span><span class="sxs-lookup"><span data-stu-id="ff8fd-155">To set up and test the database connection</span></span>  
  
1.  <span data-ttu-id="ff8fd-156">Tapez ou collez le code suivant dans la méthode `Main` de la classe Program :</span><span class="sxs-lookup"><span data-stu-id="ff8fd-156">Type or paste the following code into the `Main` method in the Program class:</span></span>  
  
     [!code-csharp[DLinqWalk3CS#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqWalk3CS/cs/Program.cs#2)]  
  
2.  <span data-ttu-id="ff8fd-157">Appuyez sur F5 pour tester l'application à ce stade.</span><span class="sxs-lookup"><span data-stu-id="ff8fd-157">Press F5 to test the application at this point.</span></span>  
  
     <span data-ttu-id="ff8fd-158">A **Console** fenêtre s’ouvre.</span><span class="sxs-lookup"><span data-stu-id="ff8fd-158">A **Console** window opens.</span></span>  
  
     <span data-ttu-id="ff8fd-159">Vous pouvez fermer l’application en appuyant sur entrée dans le **Console** fenêtre, ou en cliquant sur **arrêter le débogage** sur la [!INCLUDE[vs_current_short](../../../../../../includes/vs-current-short-md.md)] **déboguer** menu.</span><span class="sxs-lookup"><span data-stu-id="ff8fd-159">You can close the application by pressing Enter in the **Console** window, or by clicking **Stop Debugging** on the [!INCLUDE[vs_current_short](../../../../../../includes/vs-current-short-md.md)] **Debug** menu.</span></span>  
  
## <a name="creating-a-new-entity"></a><span data-ttu-id="ff8fd-160">Création d'une entité</span><span class="sxs-lookup"><span data-stu-id="ff8fd-160">Creating a New Entity</span></span>  
 <span data-ttu-id="ff8fd-161">La création d'une entité est une opération simple.</span><span class="sxs-lookup"><span data-stu-id="ff8fd-161">Creating a new entity is straightforward.</span></span> <span data-ttu-id="ff8fd-162">Vous pouvez créer des objets (`Customer`, par exemple) à l'aide du mot clé `new`.</span><span class="sxs-lookup"><span data-stu-id="ff8fd-162">You can create objects (such as `Customer`) by using the `new` keyword.</span></span>  
  
 <span data-ttu-id="ff8fd-163">Dans cette section et les suivantes, vous apporterez des modifications uniquement au cache local.</span><span class="sxs-lookup"><span data-stu-id="ff8fd-163">In this and the following sections, you are making changes only to the local cache.</span></span> <span data-ttu-id="ff8fd-164">Aucune modification n'est envoyée à la base de données tant que vous n'avez pas appelé <xref:System.Data.Linq.DataContext.SubmitChanges%2A> vers la fin de cette procédure pas à pas.</span><span class="sxs-lookup"><span data-stu-id="ff8fd-164">No changes are sent to the database until you call <xref:System.Data.Linq.DataContext.SubmitChanges%2A> toward the end of this walkthrough.</span></span>  
  
#### <a name="to-add-a-new-customer-entity-object"></a><span data-ttu-id="ff8fd-165">Pour ajouter un nouvel objet d'entité Customer</span><span class="sxs-lookup"><span data-stu-id="ff8fd-165">To add a new Customer entity object</span></span>  
  
1.  <span data-ttu-id="ff8fd-166">Créez un `Customer` en ajoutant le code suivant avant `Console.ReadLine();` dans la méthode `Main` :</span><span class="sxs-lookup"><span data-stu-id="ff8fd-166">Create a new `Customer` by adding the following code before `Console.ReadLine();` in the `Main` method:</span></span>  
  
     [!code-csharp[DLinqWalk3CS#3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqWalk3CS/cs/Program.cs#3)]  
  
2.  <span data-ttu-id="ff8fd-167">Appuyez sur F5 pour déboguer la solution.</span><span class="sxs-lookup"><span data-stu-id="ff8fd-167">Press F5 to debug the solution.</span></span>  
  
3.  <span data-ttu-id="ff8fd-168">Appuyez sur entrée dans le **Console** fenêtre pour arrêter le débogage et poursuivre la procédure pas à pas.</span><span class="sxs-lookup"><span data-stu-id="ff8fd-168">Press Enter in the **Console** window to stop debugging and continue the walkthrough.</span></span>  
  
## <a name="updating-an-entity"></a><span data-ttu-id="ff8fd-169">Mise à jour d'une entité</span><span class="sxs-lookup"><span data-stu-id="ff8fd-169">Updating an Entity</span></span>  
 <span data-ttu-id="ff8fd-170">Au cours des étapes suivantes, vous allez récupérer un objet `Customer` et modifier l'une de ses propriétés.</span><span class="sxs-lookup"><span data-stu-id="ff8fd-170">In the following steps, you will retrieve a `Customer` object and modify one of its properties.</span></span>  
  
#### <a name="to-change-the-name-of-a-customer"></a><span data-ttu-id="ff8fd-171">Pour modifier le nom d'un client</span><span class="sxs-lookup"><span data-stu-id="ff8fd-171">To change the name of a Customer</span></span>  
  
-   <span data-ttu-id="ff8fd-172">Ajoutez le code suivant au-dessus de `Console.ReadLine();` :</span><span class="sxs-lookup"><span data-stu-id="ff8fd-172">Add the following code above `Console.ReadLine();`:</span></span>  
  
     [!code-csharp[DLinqWalk3CS#4](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqWalk3CS/cs/Program.cs#4)]  
  
## <a name="deleting-an-entity"></a><span data-ttu-id="ff8fd-173">Suppression d'une entité</span><span class="sxs-lookup"><span data-stu-id="ff8fd-173">Deleting an Entity</span></span>  
 <span data-ttu-id="ff8fd-174">Vous pouvez supprimer la première commande à l'aide du même objet Customer.</span><span class="sxs-lookup"><span data-stu-id="ff8fd-174">Using the same customer object, you can delete the first order.</span></span>  
  
 <span data-ttu-id="ff8fd-175">Le code suivant montre comment couper les relations entre les lignes et supprimer une ligne de la base de données.</span><span class="sxs-lookup"><span data-stu-id="ff8fd-175">The following code demonstrates how to sever relationships between rows, and how to delete a row from the database.</span></span> <span data-ttu-id="ff8fd-176">Ajoutez le code suivant avant `Console.ReadLine` pour voir comment les objets peuvent être supprimés :</span><span class="sxs-lookup"><span data-stu-id="ff8fd-176">Add the following code before `Console.ReadLine` to see how objects can be deleted:</span></span>  
  
#### <a name="to-delete-a-row"></a><span data-ttu-id="ff8fd-177">Pour supprimer une ligne</span><span class="sxs-lookup"><span data-stu-id="ff8fd-177">To delete a row</span></span>  
  
-   <span data-ttu-id="ff8fd-178">Ajoutez le code suivant juste au-dessus de `Console.ReadLine();` :</span><span class="sxs-lookup"><span data-stu-id="ff8fd-178">Add the following code just above `Console.ReadLine();`:</span></span>  
  
     [!code-csharp[DLinqWalk3CS#5](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqWalk3CS/cs/Program.cs#5)]  
  
## <a name="submitting-changes-to-the-database"></a><span data-ttu-id="ff8fd-179">Soumission des modifications à la base de données</span><span class="sxs-lookup"><span data-stu-id="ff8fd-179">Submitting Changes to the Database</span></span>  
 <span data-ttu-id="ff8fd-180">La dernière étape requise pour la création, la mise à jour et la suppression d'objets consiste à soumettre les modifications à la base de données.</span><span class="sxs-lookup"><span data-stu-id="ff8fd-180">The final step required for creating, updating, and deleting objects, is to actually submit the changes to the database.</span></span> <span data-ttu-id="ff8fd-181">Sans cette étape, vos modifications restent locales et n'apparaissent pas dans les résultats de requêtes.</span><span class="sxs-lookup"><span data-stu-id="ff8fd-181">Without this step, your changes are only local and will not appear in query results.</span></span>  
  
#### <a name="to-submit-changes-to-the-database"></a><span data-ttu-id="ff8fd-182">Pour soumettre les modifications à la base de données</span><span class="sxs-lookup"><span data-stu-id="ff8fd-182">To submit changes to the database</span></span>  
  
1.  <span data-ttu-id="ff8fd-183">Insérez le code suivant juste au-dessus de `Console.ReadLine` :</span><span class="sxs-lookup"><span data-stu-id="ff8fd-183">Insert the following code just above `Console.ReadLine`:</span></span>  
  
     [!code-csharp[DLinqWalk3CS#6](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqWalk3CS/cs/Program.cs#6)]  
  
2.  <span data-ttu-id="ff8fd-184">Insérez le code suivant (après `SubmitChanges`) pour afficher les effets avant/après de la soumission des modifications :</span><span class="sxs-lookup"><span data-stu-id="ff8fd-184">Insert the following code (after `SubmitChanges`) to show the before and after effects of submitting the changes:</span></span>  
  
     [!code-csharp[DLinqWalk3CS#7](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqWalk3CS/cs/Program.cs#7)]  
  
3.  <span data-ttu-id="ff8fd-185">Appuyez sur F5 pour déboguer la solution.</span><span class="sxs-lookup"><span data-stu-id="ff8fd-185">Press F5 to debug the solution.</span></span>  
  
4.  <span data-ttu-id="ff8fd-186">Appuyez sur entrée dans le **Console** fenêtre pour fermer l’application.</span><span class="sxs-lookup"><span data-stu-id="ff8fd-186">Press Enter in the **Console** window to close the application.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="ff8fd-187">Une fois que vous avez soumis les modifications (ajouté le nouveau client), vous ne pouvez plus exécuter cette solution telle quelle.</span><span class="sxs-lookup"><span data-stu-id="ff8fd-187">After you have added the new customer by submitting the changes, you cannot execute this solution again as is.</span></span> <span data-ttu-id="ff8fd-188">Pour l'exécuter à nouveau, modifiez le nom du client et l'ID client à ajouter.</span><span class="sxs-lookup"><span data-stu-id="ff8fd-188">To execute the solution again, change the name of the customer and customer ID to be added.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ff8fd-189">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ff8fd-189">See Also</span></span>  
 [<span data-ttu-id="ff8fd-190">Apprentissage par les procédures pas à pas</span><span class="sxs-lookup"><span data-stu-id="ff8fd-190">Learning by Walkthroughs</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/learning-by-walkthroughs.md)
