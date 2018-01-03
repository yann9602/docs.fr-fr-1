---
title: "Procédure pas à pas : utilisation de procédures stockées uniquement (Visual Basic)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: vb
ms.assetid: 5a736a30-ba66-4adb-b87c-57d19476e862
caps.latest.revision: "4"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: 2eed4db8ee76d6f7bea8b0628219e858a1db9695
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="walkthrough-using-only-stored-procedures-visual-basic"></a><span data-ttu-id="b7967-102">Procédure pas à pas : utilisation de procédures stockées uniquement (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="b7967-102">Walkthrough: Using Only Stored Procedures (Visual Basic)</span></span>
<span data-ttu-id="b7967-103">Cette procédure pas à pas fournit un scénario [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] de base complet pour accéder aux données à l'aide de procédures stockées uniquement.</span><span class="sxs-lookup"><span data-stu-id="b7967-103">This walkthrough provides a basic end-to-end [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] scenario for accessing data by using stored procedures only.</span></span> <span data-ttu-id="b7967-104">Cette approche est souvent utilisée par les administrateurs de base de données pour limiter les moyens d'accès au magasin de données.</span><span class="sxs-lookup"><span data-stu-id="b7967-104">This approach is often used by database administrators to limit how the datastore is accessed.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="b7967-105">Vous pouvez également utiliser des procédures stockées dans les applications [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] pour substituer le comportement par défaut, plus particulièrement pour les processus `Create`, `Update` et `Delete`.</span><span class="sxs-lookup"><span data-stu-id="b7967-105">You can also use stored procedures in [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] applications to override default behavior, especially for `Create`, `Update`, and `Delete` processes.</span></span> <span data-ttu-id="b7967-106">Pour plus d’informations, consultez [personnalisation des opérations d’insertion, mise à jour et supprimer](../../../../../../docs/framework/data/adonet/sql/linq/customizing-insert-update-and-delete-operations.md).</span><span class="sxs-lookup"><span data-stu-id="b7967-106">For more information, see [Customizing Insert, Update, and Delete Operations](../../../../../../docs/framework/data/adonet/sql/linq/customizing-insert-update-and-delete-operations.md).</span></span>  
  
 <span data-ttu-id="b7967-107">Dans cette procédure pas à pas, vous utiliserez deux méthodes mappées aux procédures stockées dans l'exemple de base de données Northwind : CustOrdersDetail et CustOrderHist.</span><span class="sxs-lookup"><span data-stu-id="b7967-107">For purposes of this walkthrough, you will use two methods that have been mapped to stored procedures in the Northwind sample database: CustOrdersDetail and CustOrderHist.</span></span> <span data-ttu-id="b7967-108">Le mappage se produit lorsque vous exécutez l'outil en ligne de commande SQLMetal pour générer un fichier [!INCLUDE[vbprvb](../../../../../../includes/vbprvb-md.md)].</span><span class="sxs-lookup"><span data-stu-id="b7967-108">The mapping occurs when you run the SqlMetal command-line tool to generate a [!INCLUDE[vbprvb](../../../../../../includes/vbprvb-md.md)] file.</span></span> <span data-ttu-id="b7967-109">Pour plus d'informations, consultez la section Composants requis par la suite dans cette procédure pas à pas.</span><span class="sxs-lookup"><span data-stu-id="b7967-109">For more information, see the Prerequisites section later in this walkthrough.</span></span>  
  
 <span data-ttu-id="b7967-110">Cette procédure pas à pas ne s'appuie pas sur le [!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)].</span><span class="sxs-lookup"><span data-stu-id="b7967-110">This walkthrough does not rely on the [!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)].</span></span> <span data-ttu-id="b7967-111">Les développeurs qui utilisent [!INCLUDE[vs_current_short](../../../../../../includes/vs-current-short-md.md)] peuvent également utiliser le [!INCLUDE[vs_ordesigner_short](../../../../../../includes/vs-ordesigner-short-md.md)] pour implémenter les fonctionnalités de procédure stockée.</span><span class="sxs-lookup"><span data-stu-id="b7967-111">Developers using [!INCLUDE[vs_current_short](../../../../../../includes/vs-current-short-md.md)] can also use the [!INCLUDE[vs_ordesigner_short](../../../../../../includes/vs-ordesigner-short-md.md)] to implement stored procedure functionality.</span></span> <span data-ttu-id="b7967-112">Consultez [LINQ to SQL des outils dans Visual Studio](/visualstudio/data-tools/linq-to-sql-tools-in-visual-studio2).</span><span class="sxs-lookup"><span data-stu-id="b7967-112">See [LINQ to SQL Tools in Visual Studio](/visualstudio/data-tools/linq-to-sql-tools-in-visual-studio2).</span></span>  
  
 [!INCLUDE[note_settings_general](../../../../../../includes/note-settings-general-md.md)]  
  
 <span data-ttu-id="b7967-113">Cette procédure pas à pas a été écrite à l'aide des paramètres de développement Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="b7967-113">This walkthrough was written by using Visual Basic Development Settings.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="b7967-114">Prérequis</span><span class="sxs-lookup"><span data-stu-id="b7967-114">Prerequisites</span></span>  
 <span data-ttu-id="b7967-115">Elle requiert les éléments suivants :</span><span class="sxs-lookup"><span data-stu-id="b7967-115">This walkthrough requires the following:</span></span>  
  
-   <span data-ttu-id="b7967-116">Les fichiers sont stockés dans un dossier dédié, c:\linqtest3.</span><span class="sxs-lookup"><span data-stu-id="b7967-116">This walkthrough uses a dedicated folder ("c:\linqtest3") to hold files.</span></span> <span data-ttu-id="b7967-117">Vous devez créer ce dossier avant de commencer la procédure pas à pas.</span><span class="sxs-lookup"><span data-stu-id="b7967-117">Create this folder before you begin the walkthrough.</span></span>  
  
-   <span data-ttu-id="b7967-118">Exemple de base de données Northwind.</span><span class="sxs-lookup"><span data-stu-id="b7967-118">The Northwind sample database.</span></span>  
  
     <span data-ttu-id="b7967-119">Si cette base de données n'est pas disponible sur votre ordinateur de développement, vous pouvez la télécharger à partir du site de téléchargement Microsoft.</span><span class="sxs-lookup"><span data-stu-id="b7967-119">If you do not have this database on your development computer, you can download it from the Microsoft download site.</span></span> <span data-ttu-id="b7967-120">Pour obtenir des instructions, consultez [téléchargement d’exemples de bases de données](../../../../../../docs/framework/data/adonet/sql/linq/downloading-sample-databases.md).</span><span class="sxs-lookup"><span data-stu-id="b7967-120">For instructions, see [Downloading Sample Databases](../../../../../../docs/framework/data/adonet/sql/linq/downloading-sample-databases.md).</span></span> <span data-ttu-id="b7967-121">Après avoir téléchargé la base de données, copiez le fichier northwnd.mdf dans le dossier c:\linqtest3.</span><span class="sxs-lookup"><span data-stu-id="b7967-121">After you have downloaded the database, copy the northwnd.mdf file to the c:\linqtest3 folder.</span></span>  
  
-   <span data-ttu-id="b7967-122">Fichier de code [!INCLUDE[vbprvb](../../../../../../includes/vbprvb-md.md)] généré à partir de la base de données Northwind.</span><span class="sxs-lookup"><span data-stu-id="b7967-122">A [!INCLUDE[vbprvb](../../../../../../includes/vbprvb-md.md)] code file generated from the Northwind database.</span></span>  
  
     <span data-ttu-id="b7967-123">Cette procédure pas à pas a été écrite à l'aide de l'outil SQLMetal, avec la ligne de commande suivante :</span><span class="sxs-lookup"><span data-stu-id="b7967-123">This walkthrough was written by using the SqlMetal tool with the following command line:</span></span>  
  
     <span data-ttu-id="b7967-124">**SqlMetal /code:"c:\linqtest3\northwind.vb » / Language : VB « c:\linqtest3\northwnd.mdf » /sprocs /functions / au pluriel**</span><span class="sxs-lookup"><span data-stu-id="b7967-124">**sqlmetal /code:"c:\linqtest3\northwind.vb" /language:vb "c:\linqtest3\northwnd.mdf" /sprocs /functions /pluralize**</span></span>  
  
     <span data-ttu-id="b7967-125">Pour plus d’informations, consultez [SqlMetal.exe (outil de génération de code)](../../../../../../docs/framework/tools/sqlmetal-exe-code-generation-tool.md).</span><span class="sxs-lookup"><span data-stu-id="b7967-125">For more information, see [SqlMetal.exe (Code Generation Tool)](../../../../../../docs/framework/tools/sqlmetal-exe-code-generation-tool.md).</span></span>  
  
## <a name="overview"></a><span data-ttu-id="b7967-126">Vue d'ensemble</span><span class="sxs-lookup"><span data-stu-id="b7967-126">Overview</span></span>  
 <span data-ttu-id="b7967-127">Cette procédure pas à pas se compose de six tâches principales :</span><span class="sxs-lookup"><span data-stu-id="b7967-127">This walkthrough consists of six main tasks:</span></span>  
  
-   <span data-ttu-id="b7967-128">Configuration de la solution [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] dans [!INCLUDE[vs_current_short](../../../../../../includes/vs-current-short-md.md)].</span><span class="sxs-lookup"><span data-stu-id="b7967-128">Setting up the [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] solution in [!INCLUDE[vs_current_short](../../../../../../includes/vs-current-short-md.md)].</span></span>  
  
-   <span data-ttu-id="b7967-129">Ajout de l'assembly System.Data.Linq au projet.</span><span class="sxs-lookup"><span data-stu-id="b7967-129">Adding the System.Data.Linq assembly to the project.</span></span>  
  
-   <span data-ttu-id="b7967-130">Ajout du fichier de code de base de données au projet.</span><span class="sxs-lookup"><span data-stu-id="b7967-130">Adding the database code file to the project.</span></span>  
  
-   <span data-ttu-id="b7967-131">Création d'une connexion à la base de données.</span><span class="sxs-lookup"><span data-stu-id="b7967-131">Creating a connection to the database.</span></span>  
  
-   <span data-ttu-id="b7967-132">Configuration de l'interface utilisateur.</span><span class="sxs-lookup"><span data-stu-id="b7967-132">Setting up the user interface.</span></span>  
  
-   <span data-ttu-id="b7967-133">Exécution et test de l'application.</span><span class="sxs-lookup"><span data-stu-id="b7967-133">Running and testing the application.</span></span>  
  
## <a name="creating-a-linq-to-sql-solution"></a><span data-ttu-id="b7967-134">Création d'une solution LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="b7967-134">Creating a LINQ to SQL Solution</span></span>  
 <span data-ttu-id="b7967-135">Au cours de cette première tâche, vous allez créer une solution [!INCLUDE[vs_current_short](../../../../../../includes/vs-current-short-md.md)] qui contient les références nécessaires pour générer et exécuter un projet [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].</span><span class="sxs-lookup"><span data-stu-id="b7967-135">In this first task, you create a [!INCLUDE[vs_current_short](../../../../../../includes/vs-current-short-md.md)] solution that contains the necessary references to build and run a [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] project.</span></span>  
  
#### <a name="to-create-a-linq-to-sql-solution"></a><span data-ttu-id="b7967-136">Pour créer une solution LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="b7967-136">To create a LINQ to SQL solution</span></span>  
  
1.  <span data-ttu-id="b7967-137">Sur le [!INCLUDE[vs_current_short](../../../../../../includes/vs-current-short-md.md)] **fichier** menu, cliquez sur **nouveau projet**.</span><span class="sxs-lookup"><span data-stu-id="b7967-137">On the [!INCLUDE[vs_current_short](../../../../../../includes/vs-current-short-md.md)] **File** menu, click **New Project**.</span></span>  
  
2.  <span data-ttu-id="b7967-138">Dans le volet **Types de projets** dans la boîte de dialogue **Nouveau projet** , développez **Visual Basic**, puis cliquez sur **Windows**.</span><span class="sxs-lookup"><span data-stu-id="b7967-138">In the **Project types** pane in the **New Project** dialog box, expand **Visual Basic**, and then click **Windows**.</span></span>  
  
3.  <span data-ttu-id="b7967-139">Dans le volet **Modèles** , cliquez sur **Application Windows Forms**.</span><span class="sxs-lookup"><span data-stu-id="b7967-139">In the **Templates** pane, click **Windows Forms Application**.</span></span>  
  
4.  <span data-ttu-id="b7967-140">Dans le **nom** , tapez **SprocOnlyApp**.</span><span class="sxs-lookup"><span data-stu-id="b7967-140">In the **Name** box, type **SprocOnlyApp**.</span></span>  
  
5.  <span data-ttu-id="b7967-141">Cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="b7967-141">Click **OK**.</span></span>  
  
     <span data-ttu-id="b7967-142">Le Concepteur Windows Forms s'ouvre.</span><span class="sxs-lookup"><span data-stu-id="b7967-142">The Windows Forms Designer opens.</span></span>  
  
## <a name="adding-the-linq-to-sql-assembly-reference"></a><span data-ttu-id="b7967-143">Ajout de la référence à l'assembly LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="b7967-143">Adding the LINQ to SQL Assembly Reference</span></span>  
 <span data-ttu-id="b7967-144">L'assembly [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] n'est pas inclus dans le modèle Application Windows Forms standard.</span><span class="sxs-lookup"><span data-stu-id="b7967-144">The [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] assembly is not included in the standard Windows Forms Application template.</span></span> <span data-ttu-id="b7967-145">Vous devrez ajouter l'assembly vous-même, comme expliqué dans les étapes suivantes :</span><span class="sxs-lookup"><span data-stu-id="b7967-145">You will have to add the assembly yourself, as explained in the following steps:</span></span>  
  
#### <a name="to-add-systemdatalinqdll"></a><span data-ttu-id="b7967-146">Pour ajouter System.Data.Linq.dll</span><span class="sxs-lookup"><span data-stu-id="b7967-146">To add System.Data.Linq.dll</span></span>  
  
1.  <span data-ttu-id="b7967-147">Dans **l’Explorateur de solutions**, cliquez sur **afficher tous les fichiers**.</span><span class="sxs-lookup"><span data-stu-id="b7967-147">In **Solution Explorer**, click **Show All Files**.</span></span>  
  
2.  <span data-ttu-id="b7967-148">Dans **l’Explorateur de solutions**, avec le bouton droit **références**, puis cliquez sur **ajouter une référence**.</span><span class="sxs-lookup"><span data-stu-id="b7967-148">In **Solution Explorer**, right-click **References**, and then click **Add Reference**.</span></span>  
  
3.  <span data-ttu-id="b7967-149">Dans le **ajouter une référence** boîte de dialogue, cliquez sur **.NET**et cliquez sur l’assembly System.Data.Linq, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="b7967-149">In the **Add Reference** dialog box, click **.NET**, click the System.Data.Linq assembly, and then click **OK**.</span></span>  
  
     <span data-ttu-id="b7967-150">L'assembly est ajouté au projet.</span><span class="sxs-lookup"><span data-stu-id="b7967-150">The assembly is added to the project.</span></span>  
  
## <a name="adding-the-northwind-code-file-to-the-project"></a><span data-ttu-id="b7967-151">Ajout du fichier de code Northwind au projet</span><span class="sxs-lookup"><span data-stu-id="b7967-151">Adding the Northwind Code File to the Project</span></span>  
 <span data-ttu-id="b7967-152">Ces étapes supposent que vous avez utilisé l'outil SQLMetal pour générer un fichier de code à partir de l'exemple de base de données Northwind.</span><span class="sxs-lookup"><span data-stu-id="b7967-152">This step assumes that you have used the SqlMetal tool to generate a code file from the Northwind sample database.</span></span> <span data-ttu-id="b7967-153">Pour plus d'informations, consultez la section Composants requis au début de cette procédure pas à pas.</span><span class="sxs-lookup"><span data-stu-id="b7967-153">For more information, see the Prerequisites section earlier in this walkthrough.</span></span>  
  
#### <a name="to-add-the-northwind-code-file-to-the-project"></a><span data-ttu-id="b7967-154">Pour ajouter le fichier de code Northwind au projet</span><span class="sxs-lookup"><span data-stu-id="b7967-154">To add the northwind code file to the project</span></span>  
  
1.  <span data-ttu-id="b7967-155">Sur le **projet** menu, cliquez sur **ajouter un élément existant**.</span><span class="sxs-lookup"><span data-stu-id="b7967-155">On the **Project** menu, click **Add Existing Item**.</span></span>  
  
2.  <span data-ttu-id="b7967-156">Dans le **ajouter un élément existant** boîte de dialogue, accédez à c:\linqtest3\northwind.vb, puis cliquez sur **ajouter**.</span><span class="sxs-lookup"><span data-stu-id="b7967-156">In the **Add Existing Item** dialog box, move to c:\linqtest3\northwind.vb, and then click **Add**.</span></span>  
  
     <span data-ttu-id="b7967-157">Le fichier northwind.vb est ajouté au projet.</span><span class="sxs-lookup"><span data-stu-id="b7967-157">The northwind.vb file is added to the project.</span></span>  
  
## <a name="creating-a-database-connection"></a><span data-ttu-id="b7967-158">Création d'une connexion à une base de données</span><span class="sxs-lookup"><span data-stu-id="b7967-158">Creating a Database Connection</span></span>  
 <span data-ttu-id="b7967-159">Au cours de cette étape, vous allez définir la connexion à l'exemple de base de données Northwind.</span><span class="sxs-lookup"><span data-stu-id="b7967-159">In this step, you define the connection to the Northwind sample database.</span></span> <span data-ttu-id="b7967-160">Cette procédure pas à pas utilise "c:\linqtest3\northwnd.mdf" comme chemin d'accès.</span><span class="sxs-lookup"><span data-stu-id="b7967-160">This walkthrough uses "c:\linqtest3\northwnd.mdf" as the path.</span></span>  
  
#### <a name="to-create-the-database-connection"></a><span data-ttu-id="b7967-161">Pour créer la connexion de base de données</span><span class="sxs-lookup"><span data-stu-id="b7967-161">To create the database connection</span></span>  
  
1.  <span data-ttu-id="b7967-162">Dans **l’Explorateur de solutions**, avec le bouton droit **Form1.vb**, puis cliquez sur **afficher le Code**.</span><span class="sxs-lookup"><span data-stu-id="b7967-162">In **Solution Explorer**, right-click **Form1.vb**, and then click **View Code**.</span></span>  
  
     <span data-ttu-id="b7967-163">`Class Form1` apparaît dans l'éditeur de code.</span><span class="sxs-lookup"><span data-stu-id="b7967-163">`Class Form1` appears in the code editor.</span></span>  
  
2.  <span data-ttu-id="b7967-164">Tapez le code suivant dans le bloc de code `Form1` :</span><span class="sxs-lookup"><span data-stu-id="b7967-164">Type the following code into the `Form1` code block:</span></span>  
  
     [!code-vb[DLinqWalk4VB#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqWalk4VB/vb/Form1.vb#1)]  
  
## <a name="setting-up-the-user-interface"></a><span data-ttu-id="b7967-165">Configuration de l'interface utilisateur.</span><span class="sxs-lookup"><span data-stu-id="b7967-165">Setting up the User Interface</span></span>  
 <span data-ttu-id="b7967-166">Au cours de cette tâche, vous allez créez une interface pour permettre aux utilisateurs d'exécuter des procédures stockées pour accéder aux données de la base de données.</span><span class="sxs-lookup"><span data-stu-id="b7967-166">In this task you create an interface so that users can execute stored procedures to access data in the database.</span></span> <span data-ttu-id="b7967-167">Dans l'application que vous développez avec cette procédure pas à pas, les utilisateurs peuvent accéder aux données de la base de données uniquement en utilisant les procédures stockées incorporées dans l'application.</span><span class="sxs-lookup"><span data-stu-id="b7967-167">In the application that you are developing with this walkthrough, users can access data in the database only by using the stored procedures embedded in the application.</span></span>  
  
#### <a name="to-set-up-the-user-interface"></a><span data-ttu-id="b7967-168">Pour configurer l'interface utilisateur</span><span class="sxs-lookup"><span data-stu-id="b7967-168">To set up the user interface</span></span>  
  
1.  <span data-ttu-id="b7967-169">Revenir à la fenêtre Concepteur de formulaires (**Form1.vb]**).</span><span class="sxs-lookup"><span data-stu-id="b7967-169">Return to the Windows Forms Designer (**Form1.vb[Design]**).</span></span>  
  
2.  <span data-ttu-id="b7967-170">Dans le menu **Affichage** , cliquez sur **Boîte à outils**.</span><span class="sxs-lookup"><span data-stu-id="b7967-170">On the **View** menu, click **Toolbox**.</span></span>  
  
     <span data-ttu-id="b7967-171">La boîte à outils s'ouvre.</span><span class="sxs-lookup"><span data-stu-id="b7967-171">The toolbox opens.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="b7967-172">Cliquez sur le **masquage automatique** punaise pour garder la boîte à outils ouverte pendant que vous effectuez les autres étapes de cette section.</span><span class="sxs-lookup"><span data-stu-id="b7967-172">Click the **AutoHide** pushpin to keep the toolbox open while you perform the remaining steps in this section.</span></span>  
  
3.  <span data-ttu-id="b7967-173">Faites glisser deux boutons, deux zones de texte et deux étiquettes à partir de la boîte à outils vers **Form1**.</span><span class="sxs-lookup"><span data-stu-id="b7967-173">Drag two buttons, two text boxes, and two labels from the toolbox onto **Form1**.</span></span>  
  
     <span data-ttu-id="b7967-174">Disposez les contrôles comme dans l'illustration associée.</span><span class="sxs-lookup"><span data-stu-id="b7967-174">Arrange the controls as in the accompanying illustration.</span></span> <span data-ttu-id="b7967-175">Développez **Form1** afin que les contrôles s’ajustent facilement.</span><span class="sxs-lookup"><span data-stu-id="b7967-175">Expand **Form1** so that the controls fit easily.</span></span>  
  
4.  <span data-ttu-id="b7967-176">Avec le bouton droit **Label1**, puis cliquez sur **propriétés**.</span><span class="sxs-lookup"><span data-stu-id="b7967-176">Right-click **Label1**, and then click **Properties**.</span></span>  
  
5.  <span data-ttu-id="b7967-177">Modifier la **texte** propriété à partir de **Label1** à **Enter OrderID :**.</span><span class="sxs-lookup"><span data-stu-id="b7967-177">Change the **Text** property from **Label1** to **Enter OrderID:**.</span></span>  
  
6.  <span data-ttu-id="b7967-178">Dans la même façon pour **Label2**, modifiez le **texte** propriété à partir de **Label2** à **Enter CustomerID :**.</span><span class="sxs-lookup"><span data-stu-id="b7967-178">In the same way for **Label2**, change the **Text** property from **Label2** to **Enter CustomerID:**.</span></span>  
  
7.  <span data-ttu-id="b7967-179">Dans la même façon, modifiez le **texte** propriété **Button1** à **Order Details**.</span><span class="sxs-lookup"><span data-stu-id="b7967-179">In the same way, change the **Text** property for **Button1** to **Order Details**.</span></span>  
  
8.  <span data-ttu-id="b7967-180">Modifier la **texte** propriété **Button2** à **l’historique des commandes**.</span><span class="sxs-lookup"><span data-stu-id="b7967-180">Change the **Text** property for **Button2** to **Order History**.</span></span>  
  
     <span data-ttu-id="b7967-181">Élargissez les contrôles boutons afin que tout le texte soit visible.</span><span class="sxs-lookup"><span data-stu-id="b7967-181">Widen the button controls so that all the text is visible.</span></span>  
  
#### <a name="to-handle-button-clicks"></a><span data-ttu-id="b7967-182">Pour gérer des clics de bouton</span><span class="sxs-lookup"><span data-stu-id="b7967-182">To handle button clicks</span></span>  
  
1.  <span data-ttu-id="b7967-183">Double-cliquez sur **Order Details** sur **Form1** pour créer le `Button1` Gestionnaire d’événements et ouvrez l’éditeur de code.</span><span class="sxs-lookup"><span data-stu-id="b7967-183">Double-click **Order Details** on **Form1** to create the `Button1` event handler and open the code editor.</span></span>  
  
2.  <span data-ttu-id="b7967-184">Tapez le code suivant dans le gestionnaire d'événements `Button1` :</span><span class="sxs-lookup"><span data-stu-id="b7967-184">Type the following code into the `Button1` handler:</span></span>  
  
     [!code-vb[DLinqWalk4VB#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqWalk4VB/vb/Form1.vb#2)]  
  
3.  <span data-ttu-id="b7967-185">Double-cliquez maintenant sur **Button2** sur Form1 pour créer le `Button2` Gestionnaire d’événements et ouvrez l’éditeur de code.</span><span class="sxs-lookup"><span data-stu-id="b7967-185">Now double-click **Button2** on Form1 to create the `Button2` event handler and open the code editor.</span></span>  
  
4.  <span data-ttu-id="b7967-186">Tapez le code suivant dans le gestionnaire d'événements `Button2` :</span><span class="sxs-lookup"><span data-stu-id="b7967-186">Type the following code into the `Button2` handler:</span></span>  
  
     [!code-vb[DLinqWalk4VB#3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqWalk4VB/vb/Form1.vb#3)]  
  
## <a name="testing-the-application"></a><span data-ttu-id="b7967-187">Test de l'application</span><span class="sxs-lookup"><span data-stu-id="b7967-187">Testing the Application</span></span>  
 <span data-ttu-id="b7967-188">Vous allez maintenant tester votre application.</span><span class="sxs-lookup"><span data-stu-id="b7967-188">Now it is time to test your application.</span></span> <span data-ttu-id="b7967-189">Notez que votre contact avec le magasin de données est limité aux actions que les deux procédures stockées peuvent accepter.</span><span class="sxs-lookup"><span data-stu-id="b7967-189">Note that your contact with the datastore is limited to whatever actions the two stored procedures can take.</span></span> <span data-ttu-id="b7967-190">Ces actions consistent à retourner les produits inclus pour n'importe quel orderID que vous entrez ou à retourner un historique des produits commandés pour n'importe quel CustomerID que vous entrez.</span><span class="sxs-lookup"><span data-stu-id="b7967-190">Those actions are to return the products included for any orderID you enter, or to return a history of products ordered for any CustomerID you enter.</span></span>  
  
#### <a name="to-test-the-application"></a><span data-ttu-id="b7967-191">Pour tester l'application</span><span class="sxs-lookup"><span data-stu-id="b7967-191">To test the application</span></span>  
  
1.  <span data-ttu-id="b7967-192">Appuyez sur F5 pour démarrer le débogage.</span><span class="sxs-lookup"><span data-stu-id="b7967-192">Press F5 to start debugging.</span></span>  
  
     <span data-ttu-id="b7967-193">Form1 s'affiche.</span><span class="sxs-lookup"><span data-stu-id="b7967-193">Form1 appears.</span></span>  
  
2.  <span data-ttu-id="b7967-194">Dans le **Enter OrderID** , tapez **10249** puis cliquez sur **Order Details**.</span><span class="sxs-lookup"><span data-stu-id="b7967-194">In the **Enter OrderID** box, type **10249** and then click **Order Details**.</span></span>  
  
     <span data-ttu-id="b7967-195">Un message répertorie les produits inclus dans la commande 10249.</span><span class="sxs-lookup"><span data-stu-id="b7967-195">A message box lists the products included in order 10249.</span></span>  
  
     <span data-ttu-id="b7967-196">Cliquez sur **OK** pour fermer la boîte de message.</span><span class="sxs-lookup"><span data-stu-id="b7967-196">Click **OK** to close the message box.</span></span>  
  
3.  <span data-ttu-id="b7967-197">Dans le **Enter CustomerID** , tapez `ALFKI`, puis cliquez sur **l’historique des commandes**.</span><span class="sxs-lookup"><span data-stu-id="b7967-197">In the **Enter CustomerID** box, type `ALFKI`, and then click **Order History**.</span></span>  
  
     <span data-ttu-id="b7967-198">Un message répertorie l'historique des commandes pour le client ALFKI.</span><span class="sxs-lookup"><span data-stu-id="b7967-198">A message box lists the order history for customer ALFKI.</span></span>  
  
     <span data-ttu-id="b7967-199">Cliquez sur **OK** pour fermer la boîte de message.</span><span class="sxs-lookup"><span data-stu-id="b7967-199">Click **OK** to close the message box.</span></span>  
  
4.  <span data-ttu-id="b7967-200">Dans le **Enter OrderID** , tapez `123`, puis cliquez sur **Order Details**.</span><span class="sxs-lookup"><span data-stu-id="b7967-200">In the **Enter OrderID** box, type `123`, and then click **Order Details**.</span></span>  
  
     <span data-ttu-id="b7967-201">Le message suivant s'affiche : « Aucun résultat ».</span><span class="sxs-lookup"><span data-stu-id="b7967-201">A message box displays "No results."</span></span>  
  
     <span data-ttu-id="b7967-202">Cliquez sur **OK** pour fermer la boîte de message.</span><span class="sxs-lookup"><span data-stu-id="b7967-202">Click **OK** to close the message box.</span></span>  
  
5.  <span data-ttu-id="b7967-203">Sur le **déboguer** menu, cliquez sur **arrêter le débogage**.</span><span class="sxs-lookup"><span data-stu-id="b7967-203">On the **Debug** menu, click **Stop debugging**.</span></span>  
  
     <span data-ttu-id="b7967-204">La session de débogage s'arrête.</span><span class="sxs-lookup"><span data-stu-id="b7967-204">The debug session closes.</span></span>  
  
6.  <span data-ttu-id="b7967-205">Si vous avez terminé les tests, vous pouvez cliquer sur **fermer le projet** sur la **fichier** menu et enregistrez votre projet lorsque vous y êtes invité.</span><span class="sxs-lookup"><span data-stu-id="b7967-205">If you have finished experimenting, you can click **Close Project** on the **File** menu, and save your project when you are prompted.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="b7967-206">Étapes suivantes</span><span class="sxs-lookup"><span data-stu-id="b7967-206">Next Steps</span></span>  
 <span data-ttu-id="b7967-207">Vous pouvez améliorer ce projet en apportant des modifications.</span><span class="sxs-lookup"><span data-stu-id="b7967-207">You can enhance this project by making some changes.</span></span> <span data-ttu-id="b7967-208">Par exemple, vous pouvez répertorier les procédures stockées disponibles dans une zone de liste et demander à l'utilisateur de sélectionner les procédures à exécuter.</span><span class="sxs-lookup"><span data-stu-id="b7967-208">For example, you could list available stored procedures in a list box and have the user select which procedures to execute.</span></span> <span data-ttu-id="b7967-209">Vous pouvez également transmettre en continu la sortie des rapports dans un fichier texte.</span><span class="sxs-lookup"><span data-stu-id="b7967-209">You could also stream the output of the reports to a text file.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b7967-210">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="b7967-210">See Also</span></span>  
 [<span data-ttu-id="b7967-211">Apprentissage par les procédures pas à pas</span><span class="sxs-lookup"><span data-stu-id="b7967-211">Learning by Walkthroughs</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/learning-by-walkthroughs.md)  
 [<span data-ttu-id="b7967-212">Procédures stockées</span><span class="sxs-lookup"><span data-stu-id="b7967-212">Stored Procedures</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/stored-procedures.md)
