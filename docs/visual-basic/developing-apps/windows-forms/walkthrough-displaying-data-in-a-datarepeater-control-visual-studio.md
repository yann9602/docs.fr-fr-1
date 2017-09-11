---
title: "Procédure pas à pas : Affichage des données dans un contrôle DataRepeater (Visual Studio) | Documents Microsoft"
ms.date: 2015-07-20
ms.prod: .net
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
dev_langs:
- VB
helpviewer_keywords:
- DataRepeater, walkthrough
ms.assetid: 65dcdb95-6c3e-47cc-987d-190000f71653
caps.latest.revision: 12
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: b795b8f3bb42aecdbdfade62f4943239fec6eac4
ms.contentlocale: fr-fr
ms.lasthandoff: 04/12/2017

---
# <a name="walkthrough-displaying-data-in-a-datarepeater-control-visual-studio"></a><span data-ttu-id="ee781-102">Procédure pas à pas : affichage de données dans un contrôle DataRepeater (Visual Studio)</span><span class="sxs-lookup"><span data-stu-id="ee781-102">Walkthrough: Displaying Data in a DataRepeater Control (Visual Studio)</span></span>
<span data-ttu-id="ee781-103">Cette procédure pas à pas fournit un scénario de démarrage à la fin de base pour afficher les données liées dans un <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>contrôle.</xref:Microsoft.VisualBasic.PowerPacks.DataRepeater></span><span class="sxs-lookup"><span data-stu-id="ee781-103">This walkthrough provides a basic start-to-finish scenario for displaying bound data in a <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> control.</span></span>  
  
## <a name="prerequisite"></a><span data-ttu-id="ee781-104">Prérequis</span><span class="sxs-lookup"><span data-stu-id="ee781-104">Prerequisite</span></span>  
 <span data-ttu-id="ee781-105">Cette procédure pas à pas requiert l'exemple de base de données Northwind.</span><span class="sxs-lookup"><span data-stu-id="ee781-105">This walkthrough requires the Northwind sample database.</span></span>  
  
 <span data-ttu-id="ee781-106">Si cette base de données n’est pas disponible sur votre ordinateur de développement, vous pouvez la télécharger à partir du [Centre de téléchargement Microsoft](http://go.microsoft.com/fwlink/?LinkID=98088).</span><span class="sxs-lookup"><span data-stu-id="ee781-106">If you do not have this database on your development computer, you can download it from the [Microsoft Download Center](http://go.microsoft.com/fwlink/?LinkID=98088).</span></span> <span data-ttu-id="ee781-107">Pour obtenir des instructions, consultez la page [téléchargement d’exemples de bases de données](https://msdn.microsoft.com/library/bb399411).</span><span class="sxs-lookup"><span data-stu-id="ee781-107">For instructions, see [Downloading Sample Databases](https://msdn.microsoft.com/library/bb399411).</span></span>  
  
## <a name="overview"></a><span data-ttu-id="ee781-108">Vue d'ensemble</span><span class="sxs-lookup"><span data-stu-id="ee781-108">Overview</span></span>  
 <span data-ttu-id="ee781-109">La première partie de cette procédure pas à pas se compose de quatre tâches principales :</span><span class="sxs-lookup"><span data-stu-id="ee781-109">The first part of this walkthrough consists of four main tasks:</span></span>  
  
-   <span data-ttu-id="ee781-110">Création d’une solution.</span><span class="sxs-lookup"><span data-stu-id="ee781-110">Creating a solution.</span></span>  
  
-   <span data-ttu-id="ee781-111">Ajout d’un <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>contrôle.</xref:Microsoft.VisualBasic.PowerPacks.DataRepeater></span><span class="sxs-lookup"><span data-stu-id="ee781-111">Adding a <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> control.</span></span>  
  
-   <span data-ttu-id="ee781-112">Ajout d’une source de données.</span><span class="sxs-lookup"><span data-stu-id="ee781-112">Adding a data source.</span></span>  
  
-   <span data-ttu-id="ee781-113">Ajout de contrôles liés aux données.</span><span class="sxs-lookup"><span data-stu-id="ee781-113">Adding data-bound controls.</span></span>  
  
[!INCLUDE[note_settings_general](../../../csharp/language-reference/compiler-messages/includes/note_settings_general_md.md)]  
  
## <a name="creating-a-datarepeater-solution"></a><span data-ttu-id="ee781-114">Création d’une solution DataRepeater.</span><span class="sxs-lookup"><span data-stu-id="ee781-114">Creating a DataRepeater Solution</span></span>  
 <span data-ttu-id="ee781-115">Dans la première étape, vous allez créer un projet et une solution.</span><span class="sxs-lookup"><span data-stu-id="ee781-115">In the first step, you create a project and solution.</span></span>  
  
#### <a name="to-create-a-datarepeater-solution"></a><span data-ttu-id="ee781-116">Pour créer une solution DataRepeater</span><span class="sxs-lookup"><span data-stu-id="ee781-116">To create a DataRepeater solution</span></span>  
  
1.  <span data-ttu-id="ee781-117">Dans le menu **Fichier** de Visual Studio, cliquez sur **Nouveau projet**.</span><span class="sxs-lookup"><span data-stu-id="ee781-117">On the Visual Studio **File** menu, click **New Project**.</span></span>  
  
2.  <span data-ttu-id="ee781-118">Dans le volet **Types de projets** dans la boîte de dialogue **Nouveau projet** , développez **Visual Basic**, puis cliquez sur **Windows**.</span><span class="sxs-lookup"><span data-stu-id="ee781-118">In the **Project types** pane in the **New Project** dialog box, expand **Visual Basic**, and then click **Windows**.</span></span>  
  
3.  <span data-ttu-id="ee781-119">Dans le volet **Modèles** , cliquez sur **Application Windows Forms**.</span><span class="sxs-lookup"><span data-stu-id="ee781-119">In the **Templates** pane, click **Windows Forms Application**.</span></span>  
  
4.  <span data-ttu-id="ee781-120">Dans la zone **Nom** , tapez `DataRepeaterApp`.</span><span class="sxs-lookup"><span data-stu-id="ee781-120">In the **Name** box, type `DataRepeaterApp`.</span></span>  
  
5.  <span data-ttu-id="ee781-121">Cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="ee781-121">Click **OK**.</span></span>  
  
     <span data-ttu-id="ee781-122">Le Concepteur Windows Forms s'ouvre.</span><span class="sxs-lookup"><span data-stu-id="ee781-122">The Windows Forms Designer opens.</span></span>  
  
6.  <span data-ttu-id="ee781-123">Sélectionnez le formulaire dans le Concepteur Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="ee781-123">Select the form in the Windows Forms Designer.</span></span> <span data-ttu-id="ee781-124">Dans la fenêtre **Propriétés** , affectez à la propriété **Size** la valeur `800, 700`.</span><span class="sxs-lookup"><span data-stu-id="ee781-124">In the **Properties** window, set the **Size** property to `800, 700`.</span></span>  
  
## <a name="adding-a-datarepeater-control"></a><span data-ttu-id="ee781-125">Ajout d’un contrôle DataRepeater</span><span class="sxs-lookup"><span data-stu-id="ee781-125">Adding a DataRepeater Control</span></span>  
 <span data-ttu-id="ee781-126">Dans cette étape, vous allez ajouter un <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>contrôle au formulaire.</xref:Microsoft.VisualBasic.PowerPacks.DataRepeater></span><span class="sxs-lookup"><span data-stu-id="ee781-126">In this step, you add a <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> control to the form.</span></span>  
  
#### <a name="to-add-a-datarepeater-control"></a><span data-ttu-id="ee781-127">Pour ajouter un contrôle DataRepeater</span><span class="sxs-lookup"><span data-stu-id="ee781-127">To add a DataRepeater control</span></span>  
  
1.  <span data-ttu-id="ee781-128">Dans le menu **Affichage** , cliquez sur **Boîte à outils**.</span><span class="sxs-lookup"><span data-stu-id="ee781-128">On the **View** menu, click **Toolbox**.</span></span>  
  
     <span data-ttu-id="ee781-129">La **Boîte à outils** s'ouvre.</span><span class="sxs-lookup"><span data-stu-id="ee781-129">The **Toolbox** opens.</span></span>  
  
2.  <span data-ttu-id="ee781-130">Sélectionnez l’onglet **Visual Basic PowerPack** .</span><span class="sxs-lookup"><span data-stu-id="ee781-130">Select the **Visual Basic PowerPacks** tab.</span></span>  
  
3.  <span data-ttu-id="ee781-131">Faites glisser un <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>contrôler sur **Form1**.</xref:Microsoft.VisualBasic.PowerPacks.DataRepeater></span><span class="sxs-lookup"><span data-stu-id="ee781-131">Drag a <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> control onto **Form1**.</span></span>  
  
4.  <span data-ttu-id="ee781-132">Dans la fenêtre Propriétés, affectez à la propriété **Location** la valeur `0, 25`.</span><span class="sxs-lookup"><span data-stu-id="ee781-132">In the Properties window, set the **Location** property to `0, 25`.</span></span>  
  
5.  <span data-ttu-id="ee781-133">Affectez à la propriété **Size** la valeur `460, 600`.</span><span class="sxs-lookup"><span data-stu-id="ee781-133">Set the **Size** property to `460, 600`.</span></span>  
  
## <a name="adding-a-data-source"></a><span data-ttu-id="ee781-134">Ajout d’une source de données</span><span class="sxs-lookup"><span data-stu-id="ee781-134">Adding a Data Source</span></span>  
 <span data-ttu-id="ee781-135">Dans cette étape, vous ajoutez une source de données pour la <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>contrôle.</xref:Microsoft.VisualBasic.PowerPacks.DataRepeater></span><span class="sxs-lookup"><span data-stu-id="ee781-135">In this step, you add a data source for the <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> control.</span></span>  
  
#### <a name="to-add-a-data-source"></a><span data-ttu-id="ee781-136">Pour ajouter une source de données</span><span class="sxs-lookup"><span data-stu-id="ee781-136">To add a data source</span></span>  
  
1.  <span data-ttu-id="ee781-137">Dans le menu **Données** , cliquez sur **Afficher les sources de données**.</span><span class="sxs-lookup"><span data-stu-id="ee781-137">On the **Data** menu, click **Show Data Sources**.</span></span>  
  
2.  <span data-ttu-id="ee781-138">Dans la fenêtre **Sources de données** , cliquez sur **Ajouter une nouvelle source de données**.</span><span class="sxs-lookup"><span data-stu-id="ee781-138">In the **Data Sources** window, click **Add New Data Source**.</span></span>  
  
3.  <span data-ttu-id="ee781-139">Sélectionnez **Base de données** dans la page **Choisir un type de source de données** , puis cliquez sur **Suivant**.</span><span class="sxs-lookup"><span data-stu-id="ee781-139">Select **Database** on the **Choose a Data Source Type** page, and then click **Next**.</span></span>  
  
4.  <span data-ttu-id="ee781-140">Sur la page **Choisir votre connexion de données** , effectuez l'une des opérations suivantes :</span><span class="sxs-lookup"><span data-stu-id="ee781-140">On the **Choose Your Data Connection** page, perform one of the following steps:</span></span>  
  
    -   <span data-ttu-id="ee781-141">Si une connexion de données à l'exemple de base de données Northwind est disponible dans la liste déroulante, sélectionnez-la.</span><span class="sxs-lookup"><span data-stu-id="ee781-141">If a data connection to the Northwind sample database is available in the drop-down list, click it.</span></span>  
  
         <span data-ttu-id="ee781-142">ou</span><span class="sxs-lookup"><span data-stu-id="ee781-142">-or-</span></span>  
  
    -   <span data-ttu-id="ee781-143">Cliquez sur le bouton **Nouvelle connexion** pour configurer une nouvelle connexion de données.</span><span class="sxs-lookup"><span data-stu-id="ee781-143">Click **New Connection** to configure a new data connection.</span></span> <span data-ttu-id="ee781-144">Pour plus d’informations, consultez [Comment : créer des connexions aux bases de données SQL Server](http://msdn.microsoft.com/en-us/360c340d-e5a6-4a7e-a569-e95d500be43d).</span><span class="sxs-lookup"><span data-stu-id="ee781-144">For more information, see [How to: Create Connections to SQL Server Databases](http://msdn.microsoft.com/en-us/360c340d-e5a6-4a7e-a569-e95d500be43d).</span></span>  
  
5.  <span data-ttu-id="ee781-145">Si la base de données requiert un mot de passe, sélectionnez l'option permettant d'inclure les données sensibles, puis cliquez sur **Suivant**.</span><span class="sxs-lookup"><span data-stu-id="ee781-145">If the database requires a password, select the option to include sensitive data, and then click **Next**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="ee781-146">Si une boîte de dialogue s’affiche, cliquez sur **Oui** pour enregistrer le fichier dans votre projet.</span><span class="sxs-lookup"><span data-stu-id="ee781-146">If a dialog box appears, click **Yes** to save the file to your project.</span></span>  
  
6.  <span data-ttu-id="ee781-147">Cliquez sur **Suivant** dans la page **Enregistrer la chaîne de connexion dans le fichier de configuration de l’application** .</span><span class="sxs-lookup"><span data-stu-id="ee781-147">Click **Next** on the **Save Connection String to the Application Configuration file** page.</span></span>  
  
7.  <span data-ttu-id="ee781-148">Développez le nœud **Tables** dans la page **Choisir vos objets de base de données** .</span><span class="sxs-lookup"><span data-stu-id="ee781-148">Expand the **Tables** node on the **Choose Your Database Objects** page.</span></span>  
  
8.  <span data-ttu-id="ee781-149">Cochez les cases correspondant aux tables **Customers** et **Orders** , puis cliquez sur **Terminer**.</span><span class="sxs-lookup"><span data-stu-id="ee781-149">Select the check boxes next to the **Customers** and **Orders** tables, and then click **Finish**.</span></span>  
  
     <span data-ttu-id="ee781-150">**NorthwindDataSet** est ajouté à votre projet et les tables **Customers** et **Orders** apparaissent dans la fenêtre **Sources de données** .</span><span class="sxs-lookup"><span data-stu-id="ee781-150">**NorthwindDataSet** is added to your project and the **Customers** and **Orders** tables appear in the **Data Sources** window.</span></span>  
  
## <a name="adding-data-bound-controls"></a><span data-ttu-id="ee781-151">Ajout de contrôles liés aux données</span><span class="sxs-lookup"><span data-stu-id="ee781-151">Adding Data-Bound Controls</span></span>  
 <span data-ttu-id="ee781-152">Dans cette étape, vous allez ajouter des contrôles liés aux données le <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>.</xref:Microsoft.VisualBasic.PowerPacks.DataRepeater></span><span class="sxs-lookup"><span data-stu-id="ee781-152">In this step, you add data-bound controls to the <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>.</span></span>  
  
#### <a name="to-add-data-bound-controls"></a><span data-ttu-id="ee781-153">Pour ajouter des contrôles liés aux données</span><span class="sxs-lookup"><span data-stu-id="ee781-153">To add data-bound controls</span></span>  
  
1.  <span data-ttu-id="ee781-154">Dans la fenêtre **Sources de données** , sélectionnez le nœud de niveau supérieur pour la table **Customers** .</span><span class="sxs-lookup"><span data-stu-id="ee781-154">In the **Data Sources** window, select the top-level node for the **Customers** table.</span></span>  
  
2.  <span data-ttu-id="ee781-155">Choisissez le type de déplacement **Détails** pour la table en cliquant sur **Détails** dans la liste déroulante du nœud de la table.</span><span class="sxs-lookup"><span data-stu-id="ee781-155">Change the drop type of the table to **Details** by clicking **Details** in the drop-down list on the table node.</span></span>  
  
3.  <span data-ttu-id="ee781-156">Sélectionnez le **clients** table nœud et faites-le glisser sur la région de modèle d’élément (région supérieure) de la <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>contrôle.</xref:Microsoft.VisualBasic.PowerPacks.DataRepeater></span><span class="sxs-lookup"><span data-stu-id="ee781-156">Select the **Customers** table node and drag it onto the item template region (the upper region) of the <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> control.</span></span>  
  
     <span data-ttu-id="ee781-157">Un <xref:System.Windows.Forms.BindingNavigator>contrôle est ajouté au formulaire et la **NorthwindDataSet**, **CustomersBindingSource**, **CustomersTableAdapter**, **TableAdapterManager**, et **CustomersBindingNavigator** composants sont ajoutés à la barre d’état du composant.</xref:System.Windows.Forms.BindingNavigator></span><span class="sxs-lookup"><span data-stu-id="ee781-157">A <xref:System.Windows.Forms.BindingNavigator> control is added to the form, and the **NorthwindDataSet**, **CustomersBindingSource**, **CustomersTableAdapter**, **TableAdapterManager**, and **CustomersBindingNavigator** components are added to the Component Tray.</span></span>  
  
4.  <span data-ttu-id="ee781-158">Sélectionnez tous les champs et les étiquettes associées et placez-les à proximité de la bordure gauche de la région du modèle d’élément.</span><span class="sxs-lookup"><span data-stu-id="ee781-158">Select all of the fields and their associated labels and position them near the left edge of the item template region.</span></span>  
  
5.  <span data-ttu-id="ee781-159">Sélectionnez les cinq derniers champs (**Region**, **Postal Code**, **Country**, **Phone**et **Fax**) et les étiquettes associées ,puis déplacez-les en haut à droite des six premiers champs.</span><span class="sxs-lookup"><span data-stu-id="ee781-159">Select the last five fields (**Region**, **Postal Code**, **Country**, **Phone**, and **Fax**) and their associated labels and move them up and to the right of the first six fields.</span></span>  
  
6.  <span data-ttu-id="ee781-160">Sélectionnez le modèle d’élément (région supérieure du contrôle).</span><span class="sxs-lookup"><span data-stu-id="ee781-160">Select the item template (the upper region of the control).</span></span>  
  
7.  <span data-ttu-id="ee781-161">Dans la fenêtre Propriétés, affectez à la propriété **Size** la valeur `427, 170`.</span><span class="sxs-lookup"><span data-stu-id="ee781-161">In the Properties window, set the **Size** property to `427, 170`.</span></span>  
  
 <span data-ttu-id="ee781-162">À ce stade, vous disposez d’une application opérationnelle qui affiche une liste récurrente de clients.</span><span class="sxs-lookup"><span data-stu-id="ee781-162">At this point, you have a working application that will display a repeating list of customers.</span></span> <span data-ttu-id="ee781-163">Vous pouvez appuyer sur F5 pour exécuter l’application, modifier les données et ajouter ou supprimer des enregistrements client.</span><span class="sxs-lookup"><span data-stu-id="ee781-163">You can press F5 to run the application, change the data, and add or delete customer records.</span></span>  
  
 <span data-ttu-id="ee781-164">Lors des étapes facultatives suivantes, vous allez apprendre à personnaliser le <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>contrôle.</xref:Microsoft.VisualBasic.PowerPacks.DataRepeater></span><span class="sxs-lookup"><span data-stu-id="ee781-164">In the next optional steps, you will learn how to customize the <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> control.</span></span>  
  
## <a name="next-steps-optional"></a><span data-ttu-id="ee781-165">Étapes suivantes (facultatif)</span><span class="sxs-lookup"><span data-stu-id="ee781-165">Next Steps (Optional)</span></span>  
 <span data-ttu-id="ee781-166">Cette partie de la procédure pas à pas comporte quatre tâches facultatives :</span><span class="sxs-lookup"><span data-stu-id="ee781-166">This part of the walkthrough consists of four optional tasks:</span></span>  
  
-   <span data-ttu-id="ee781-167">Modification de l’apparence de la <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>contrôle.</xref:Microsoft.VisualBasic.PowerPacks.DataRepeater></span><span class="sxs-lookup"><span data-stu-id="ee781-167">Changing the appearance of the <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> control.</span></span>  
  
-   <span data-ttu-id="ee781-168">Ajout d’une interdiction d’ajout ou de suppression des enregistrements.</span><span class="sxs-lookup"><span data-stu-id="ee781-168">Preventing users from adding or deleting records.</span></span>  
  
-   <span data-ttu-id="ee781-169">Ajout de la fonction de recherche pour la <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>contrôle.</xref:Microsoft.VisualBasic.PowerPacks.DataRepeater></span><span class="sxs-lookup"><span data-stu-id="ee781-169">Adding search capability to the <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> control.</span></span>  
  
-   <span data-ttu-id="ee781-170">Ajout d’une table maître et détail vers le <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>contrôle.</xref:Microsoft.VisualBasic.PowerPacks.DataRepeater></span><span class="sxs-lookup"><span data-stu-id="ee781-170">Adding a master and detail table to the <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> control.</span></span>  
  
## <a name="changing-the-appearance-of-the-datarepeater-control"></a><span data-ttu-id="ee781-171">Modification de l’apparence du contrôle DataRepeater</span><span class="sxs-lookup"><span data-stu-id="ee781-171">Changing the Appearance of the DataRepeater Control</span></span>  
 <span data-ttu-id="ee781-172">Cette étape facultative, vous modifiez le `BackColor` de la <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>contrôle au moment du design.</xref:Microsoft.VisualBasic.PowerPacks.DataRepeater></span><span class="sxs-lookup"><span data-stu-id="ee781-172">In this optional step, you change the `BackColor` of the <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> control at design time.</span></span> <span data-ttu-id="ee781-173">Vous allez aussi ajouter du code pour afficher les lignes dans des couleurs qui alternent et modifier la propriété `ForeColor` d’une étiquette de façon conditionnelle.</span><span class="sxs-lookup"><span data-stu-id="ee781-173">You also add code to display rows in alternating colors and to change a label's `ForeColor` conditionally.</span></span>  
  
#### <a name="to-change-the-appearance-of-the-control"></a><span data-ttu-id="ee781-174">Pour modifier l’apparence du contrôle</span><span class="sxs-lookup"><span data-stu-id="ee781-174">To change the appearance of the control</span></span>  
  
1.  <span data-ttu-id="ee781-175">Dans le Concepteur Windows Forms, sélectionnez la région principale (inférieure) de la <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>contrôle.</xref:Microsoft.VisualBasic.PowerPacks.DataRepeater></span><span class="sxs-lookup"><span data-stu-id="ee781-175">In the Windows Forms Designer, select the main (lower) region of the <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> control.</span></span>  
  
2.  <span data-ttu-id="ee781-176">Dans la fenêtre Propriétés, définissez la propriété `BackColor` en choisissant le blanc.</span><span class="sxs-lookup"><span data-stu-id="ee781-176">In the Properties window, set the `BackColor` property to white.</span></span>  
  
3.  <span data-ttu-id="ee781-177">Double-cliquez sur le <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>pour ouvrir l’éditeur de Code.</xref:Microsoft.VisualBasic.PowerPacks.DataRepeater></span><span class="sxs-lookup"><span data-stu-id="ee781-177">Double-click the <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> to open the Code Editor.</span></span>  
  
4.  <span data-ttu-id="ee781-178">Dans l’éditeur de code, dans la liste déroulante d’événements, cliquez sur **DrawItem**.</span><span class="sxs-lookup"><span data-stu-id="ee781-178">In the Code Editor, in the Event drop-down list, click **DrawItem**.</span></span>  
  
5.  <span data-ttu-id="ee781-179">Dans la <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.DrawItem>Gestionnaire d’événements, ajoutez le code suivant pour alterner la `BackColor`:</xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.DrawItem></span><span class="sxs-lookup"><span data-stu-id="ee781-179">In the <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.DrawItem> event handler, add the following code to alternate the `BackColor`:</span></span>  
  
     <span data-ttu-id="ee781-180">[!code-cs[N °&1; de VbPowerPacksDataRepeaterWalkthrough](../../../visual-basic/developing-apps/windows-forms/codesnippet/CSharp/walkthrough-displaying-data-in-a-datarepeater-control-visual-studio_1.cs) ] 
     [!code-vb [VbPowerPacksDataRepeaterWalkthrough n °&1;](../../../visual-basic/developing-apps/windows-forms/codesnippet/VisualBasic/walkthrough-displaying-data-in-a-datarepeater-control-visual-studio_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="ee781-180">[!code-cs[VbPowerPacksDataRepeaterWalkthrough#1](../../../visual-basic/developing-apps/windows-forms/codesnippet/CSharp/walkthrough-displaying-data-in-a-datarepeater-control-visual-studio_1.cs)]
 [!code-vb[VbPowerPacksDataRepeaterWalkthrough#1](../../../visual-basic/developing-apps/windows-forms/codesnippet/VisualBasic/walkthrough-displaying-data-in-a-datarepeater-control-visual-studio_1.vb)]</span></span>  
  
6.  <span data-ttu-id="ee781-181">Dans la <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.DrawItem>Gestionnaire d’événements, ajoutez le code suivant pour modifier la `ForeColor` d’une étiquette en fonction d’une condition :</xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.DrawItem></span><span class="sxs-lookup"><span data-stu-id="ee781-181">In the <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.DrawItem> event handler, add the following code to change the `ForeColor` of a label depending on a condition:</span></span>  
  
     <span data-ttu-id="ee781-182">[!code-cs[VbPowerPacksDataRepeaterWalkthrough n °&2;](../../../visual-basic/developing-apps/windows-forms/codesnippet/CSharp/walkthrough-displaying-data-in-a-datarepeater-control-visual-studio_2.cs) ] 
     [!code-vb [VbPowerPacksDataRepeaterWalkthrough n °&2;](../../../visual-basic/developing-apps/windows-forms/codesnippet/VisualBasic/walkthrough-displaying-data-in-a-datarepeater-control-visual-studio_2.vb)]</span><span class="sxs-lookup"><span data-stu-id="ee781-182">[!code-cs[VbPowerPacksDataRepeaterWalkthrough#2](../../../visual-basic/developing-apps/windows-forms/codesnippet/CSharp/walkthrough-displaying-data-in-a-datarepeater-control-visual-studio_2.cs)]
 [!code-vb[VbPowerPacksDataRepeaterWalkthrough#2](../../../visual-basic/developing-apps/windows-forms/codesnippet/VisualBasic/walkthrough-displaying-data-in-a-datarepeater-control-visual-studio_2.vb)]</span></span>  
  
7.  <span data-ttu-id="ee781-183">Appuyez sur F5 pour exécuter l’application et visualiser les personnalisations.</span><span class="sxs-lookup"><span data-stu-id="ee781-183">Press F5 to run the application and see the customizations.</span></span>  
  
## <a name="preventing-users-from-adding-or-deleting-records"></a><span data-ttu-id="ee781-184">Interdiction d’ajout ou de suppression des enregistrements</span><span class="sxs-lookup"><span data-stu-id="ee781-184">Preventing Users from Adding or Deleting Records</span></span>  
 <span data-ttu-id="ee781-185">Cette étape facultative, vous ajoutez le code qui empêche les utilisateurs d’ajouter ou supprimer des enregistrements dans la <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>contrôle.</xref:Microsoft.VisualBasic.PowerPacks.DataRepeater></span><span class="sxs-lookup"><span data-stu-id="ee781-185">In this optional step, you add code that prevents users from adding or deleting records in the <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> control.</span></span>  
  
#### <a name="to-prevent-users-from-adding-and-deleting-records"></a><span data-ttu-id="ee781-186">Pour empêcher les utilisateurs d’ajouter et de supprimer des enregistrements</span><span class="sxs-lookup"><span data-stu-id="ee781-186">To prevent users from adding and deleting records</span></span>  
  
1.  <span data-ttu-id="ee781-187">Dans le Concepteur Windows Forms, double-cliquez sur le formulaire pour ouvrir l’éditeur de code.</span><span class="sxs-lookup"><span data-stu-id="ee781-187">In the Windows Forms Designer, double-click the form to open the Code Editor.</span></span>  
  
2.  <span data-ttu-id="ee781-188">Ajoutez le code suivant à l’événement `Form_Load` .</span><span class="sxs-lookup"><span data-stu-id="ee781-188">Add the following code to the `Form_Load` event:</span></span>  
  
     <span data-ttu-id="ee781-189">[!code-cs[VbPowerPacksDataRepeaterWalkthrough n °&3;](../../../visual-basic/developing-apps/windows-forms/codesnippet/CSharp/walkthrough-displaying-data-in-a-datarepeater-control-visual-studio_3.cs) ] 
     [!code-vb [VbPowerPacksDataRepeaterWalkthrough n°&3;](../../../visual-basic/developing-apps/windows-forms/codesnippet/VisualBasic/walkthrough-displaying-data-in-a-datarepeater-control-visual-studio_3.vb)]</span><span class="sxs-lookup"><span data-stu-id="ee781-189">[!code-cs[VbPowerPacksDataRepeaterWalkthrough#3](../../../visual-basic/developing-apps/windows-forms/codesnippet/CSharp/walkthrough-displaying-data-in-a-datarepeater-control-visual-studio_3.cs)]
 [!code-vb[VbPowerPacksDataRepeaterWalkthrough#3](../../../visual-basic/developing-apps/windows-forms/codesnippet/VisualBasic/walkthrough-displaying-data-in-a-datarepeater-control-visual-studio_3.vb)]</span></span>  
  
3.  <span data-ttu-id="ee781-190">Dans la liste déroulante Nom de la classe, cliquez sur **BindingNavigatorDeleteItem**.</span><span class="sxs-lookup"><span data-stu-id="ee781-190">In the Class Name drop-down list, click **BindingNavigatorDeleteItem**.</span></span> <span data-ttu-id="ee781-191">Dans la liste déroulante Nom de la méthode, cliquez sur **EnabledChanged**.</span><span class="sxs-lookup"><span data-stu-id="ee781-191">In the Method Name drop-down list, click **EnabledChanged**.</span></span>  
  
4.  <span data-ttu-id="ee781-192">Ajoutez le code suivant au gestionnaire d'événements `BindingNavigatorDeleteItem_EnabledChanged` :</span><span class="sxs-lookup"><span data-stu-id="ee781-192">Add the following code to the `BindingNavigatorDeleteItem_EnabledChanged` event handler:</span></span>  
  
     <span data-ttu-id="ee781-193">[!code-cs[VbPowerPacksDataRepeaterWalkthrough n °&4;](../../../visual-basic/developing-apps/windows-forms/codesnippet/CSharp/walkthrough-displaying-data-in-a-datarepeater-control-visual-studio_4.cs) ] 
     [!code-vb [VbPowerPacksDataRepeaterWalkthrough n °&4;](../../../visual-basic/developing-apps/windows-forms/codesnippet/VisualBasic/walkthrough-displaying-data-in-a-datarepeater-control-visual-studio_4.vb)]</span><span class="sxs-lookup"><span data-stu-id="ee781-193">[!code-cs[VbPowerPacksDataRepeaterWalkthrough#4](../../../visual-basic/developing-apps/windows-forms/codesnippet/CSharp/walkthrough-displaying-data-in-a-datarepeater-control-visual-studio_4.cs)]
 [!code-vb[VbPowerPacksDataRepeaterWalkthrough#4](../../../visual-basic/developing-apps/windows-forms/codesnippet/VisualBasic/walkthrough-displaying-data-in-a-datarepeater-control-visual-studio_4.vb)]</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="ee781-194">Cette étape est nécessaire car le <xref:System.Windows.Forms.BindingSource>activera le **DeleteItem** bouton chaque fois que l’enregistrement actuel est modifié.</xref:System.Windows.Forms.BindingSource></span><span class="sxs-lookup"><span data-stu-id="ee781-194">This step is necessary because the <xref:System.Windows.Forms.BindingSource> will enable the **DeleteItem** button every time that the current record changes.</span></span>  
  
5.  <span data-ttu-id="ee781-195">Appuyez sur F5 pour exécuter l'application.</span><span class="sxs-lookup"><span data-stu-id="ee781-195">Press F5 to run the application.</span></span> <span data-ttu-id="ee781-196">Notez que le bouton **DeleteItem** est désactivé et que vous ne pouvez pas supprimer des éléments en appuyant sur la touche SUPPR.</span><span class="sxs-lookup"><span data-stu-id="ee781-196">Notice that the **DeleteItem** button is disabled and that you cannot delete items by pressing the DELETE key.</span></span>  
  
## <a name="adding-search-capability-to-the-datarepeater-control"></a><span data-ttu-id="ee781-197">Ajout d’une fonction de recherche au contrôle DataRepeater</span><span class="sxs-lookup"><span data-stu-id="ee781-197">Adding Search Capability to the DataRepeater Control</span></span>  
 <span data-ttu-id="ee781-198">Cette étape facultative, vous implémentez la fonction de recherche d’une valeur dans la <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>contrôle.</xref:Microsoft.VisualBasic.PowerPacks.DataRepeater></span><span class="sxs-lookup"><span data-stu-id="ee781-198">In this optional step, you implement the capability to search for a value in the <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> control.</span></span> <span data-ttu-id="ee781-199">Si la chaîne recherchée est trouvée, le contrôle sélectionne l’élément qui contient la valeur et affiche cet élément.</span><span class="sxs-lookup"><span data-stu-id="ee781-199">If the search string is found, the control selects the item that contains the value and scrolls the item into view.</span></span>  
  
#### <a name="to-add-search-capability"></a><span data-ttu-id="ee781-200">Pour ajouter la fonction de recherche</span><span class="sxs-lookup"><span data-stu-id="ee781-200">To add search capability</span></span>  
  
1.  <span data-ttu-id="ee781-201">Faites glisser un <xref:System.Windows.Forms.TextBox>contrôler à partir de la **boîte à outils** sur le formulaire qui contient le <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>contrôle.</xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> </xref:System.Windows.Forms.TextBox></span><span class="sxs-lookup"><span data-stu-id="ee781-201">Drag a <xref:System.Windows.Forms.TextBox> control from the **Toolbox** onto the form that contains the <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> control.</span></span>  
  
     <span data-ttu-id="ee781-202">Placez-la sous la <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>contrôle.</xref:Microsoft.VisualBasic.PowerPacks.DataRepeater></span><span class="sxs-lookup"><span data-stu-id="ee781-202">Position it under the <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> control.</span></span>  
  
2.  <span data-ttu-id="ee781-203">Dans la fenêtre Propriétés, attribuez à la propriété **Name** la valeur **SearchTextBox**.</span><span class="sxs-lookup"><span data-stu-id="ee781-203">In the Properties window, change the **Name** property to **SearchTextBox**.</span></span>  
  
3.  <span data-ttu-id="ee781-204">Faites glisser un <xref:System.Windows.Forms.Button>contrôler à partir de la **boîte à outils** sur le formulaire qui contient le <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>contrôle.</xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> </xref:System.Windows.Forms.Button></span><span class="sxs-lookup"><span data-stu-id="ee781-204">Drag a <xref:System.Windows.Forms.Button> control from the **Toolbox** onto the form that contains the <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> control.</span></span> <span data-ttu-id="ee781-205">Placez-la sous la <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>contrôle.</xref:Microsoft.VisualBasic.PowerPacks.DataRepeater></span><span class="sxs-lookup"><span data-stu-id="ee781-205">Position it under the <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> control.</span></span>  
  
4.  <span data-ttu-id="ee781-206">Dans la fenêtre Propriétés, attribuez à la propriété **Name** la valeur **SearchButton**.</span><span class="sxs-lookup"><span data-stu-id="ee781-206">In the Properties window, change the **Name** property to **SearchButton**.</span></span> <span data-ttu-id="ee781-207">Affectez à la propriété **Text** la valeur **Search**.</span><span class="sxs-lookup"><span data-stu-id="ee781-207">Change the **Text** property to **Search**.</span></span>  
  
5.  <span data-ttu-id="ee781-208">Double-cliquez sur le <xref:System.Windows.Forms.Button>contrôler pour ouvrir l’éditeur de Code et ajoutez le code suivant à la `SearchButton_Click` Gestionnaire d’événements.</xref:System.Windows.Forms.Button></span><span class="sxs-lookup"><span data-stu-id="ee781-208">Double-click the <xref:System.Windows.Forms.Button> control to open the Code Editor, and add the following code to the `SearchButton_Click` event handler.</span></span>  
  
     <span data-ttu-id="ee781-209">[!code-cs[VbPowerPacksDataRepeaterWalkthrough&5;](../../../visual-basic/developing-apps/windows-forms/codesnippet/CSharp/walkthrough-displaying-data-in-a-datarepeater-control-visual-studio_5.cs) ] 
     [!code-vb [VbPowerPacksDataRepeaterWalkthrough n °&5;](../../../visual-basic/developing-apps/windows-forms/codesnippet/VisualBasic/walkthrough-displaying-data-in-a-datarepeater-control-visual-studio_5.vb)]</span><span class="sxs-lookup"><span data-stu-id="ee781-209">[!code-cs[VbPowerPacksDataRepeaterWalkthrough#5](../../../visual-basic/developing-apps/windows-forms/codesnippet/CSharp/walkthrough-displaying-data-in-a-datarepeater-control-visual-studio_5.cs)]
 [!code-vb[VbPowerPacksDataRepeaterWalkthrough#5](../../../visual-basic/developing-apps/windows-forms/codesnippet/VisualBasic/walkthrough-displaying-data-in-a-datarepeater-control-visual-studio_5.vb)]</span></span>  
  
6.  <span data-ttu-id="ee781-210">Appuyez sur F5 pour exécuter l'application.</span><span class="sxs-lookup"><span data-stu-id="ee781-210">Press F5 to run the application.</span></span> <span data-ttu-id="ee781-211">Tapez un ID client dans **SearchTextBox** et cliquez sur le bouton **Search** .</span><span class="sxs-lookup"><span data-stu-id="ee781-211">Type a customer ID in **SearchTextBox** and click the **Search** button.</span></span>  
  
## <a name="adding-a-master-and-detail-table-to-the-datarepeater"></a><span data-ttu-id="ee781-212">Ajout d’une table principale et détaillée au contrôle DataRepeater</span><span class="sxs-lookup"><span data-stu-id="ee781-212">Adding a Master and Detail Table to the DataRepeater</span></span>  
 <span data-ttu-id="ee781-213">Cette étape facultative, vous ajoutez un deuxième <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>contrôle pour afficher les commandes associées à chaque client.</xref:Microsoft.VisualBasic.PowerPacks.DataRepeater></span><span class="sxs-lookup"><span data-stu-id="ee781-213">In this optional step, you add a second <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> control to display related orders for each customer.</span></span>  
  
#### <a name="to-add-a-master-and-detail-table"></a><span data-ttu-id="ee781-214">Pour ajouter une table principale et détaillée</span><span class="sxs-lookup"><span data-stu-id="ee781-214">To add a master and detail table</span></span>  
  
1.  <span data-ttu-id="ee781-215">Faites glisser un deuxième <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>contrôler à partir de la **Visual Basic PowerPacks** onglet dans le **boîte à outils** sur le formulaire.</xref:Microsoft.VisualBasic.PowerPacks.DataRepeater></span><span class="sxs-lookup"><span data-stu-id="ee781-215">Drag a second <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> control from the **Visual Basic PowerPacks** tab in the **Toolbox** onto the form.</span></span>  
  
2.  <span data-ttu-id="ee781-216">Dans la fenêtre Propriétés, affectez à la propriété **Location** la valeur `465, 25`.</span><span class="sxs-lookup"><span data-stu-id="ee781-216">In the Properties window, set the **Location** property to `465, 25`.</span></span>  
  
3.  <span data-ttu-id="ee781-217">Affectez à la propriété **Size** la valeur `315, 600`.</span><span class="sxs-lookup"><span data-stu-id="ee781-217">Set the **Size** property to `315, 600`.</span></span>  
  
4.  <span data-ttu-id="ee781-218">Dans la fenêtre **Sources de données** , développez le nœud de la table **Customers** et sélectionnez le nœud détaillé de la table **Orders** .</span><span class="sxs-lookup"><span data-stu-id="ee781-218">In the **Data Sources** window, expand the **Customers** table node and select the detail node for the **Orders** table.</span></span>  
  
5.  <span data-ttu-id="ee781-219">Modifiez le type de déplacement de cette table **Orders** en cliquant sur **Détails** dans la liste déroulante du nœud de la table.</span><span class="sxs-lookup"><span data-stu-id="ee781-219">Change the drop type of this **Orders** table to Details by clicking **Details** in the drop-down list on the table node.</span></span>  
  
6.  <span data-ttu-id="ee781-220">Faites glisser ce **commandes** sur la région de modèle d’élément (région supérieure) du deuxième nœud de la table <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>contrôle.</xref:Microsoft.VisualBasic.PowerPacks.DataRepeater></span><span class="sxs-lookup"><span data-stu-id="ee781-220">Drag this **Orders** table node onto the item template region (the upper region) of the second <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> control.</span></span>  
  
     <span data-ttu-id="ee781-221">Un composant **OrdersBindingSource** et un composant **OrdersTableAdapter** sont ajoutés à la barre d’état des composants.</span><span class="sxs-lookup"><span data-stu-id="ee781-221">An **OrdersBindingSource** component and an **OrdersTableAdapter** component are added to the Component Tray.</span></span>  
  
7.  <span data-ttu-id="ee781-222">Appuyez sur F5 pour exécuter l'application.</span><span class="sxs-lookup"><span data-stu-id="ee781-222">Press F5 to run the application.</span></span> <span data-ttu-id="ee781-223">Lorsque vous sélectionnez chacun des clients dans la première <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>contrôler, les commandes de ce client s’affichent dans la seconde <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>contrôle.</xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> </xref:Microsoft.VisualBasic.PowerPacks.DataRepeater></span><span class="sxs-lookup"><span data-stu-id="ee781-223">When you select each customer in the first <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> control, the orders for that customer are displayed in the second <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> control.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ee781-224">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ee781-224">See Also</span></span>  
 <span data-ttu-id="ee781-225">[Introduction au contrôle DataRepeater](../../../visual-basic/developing-apps/windows-forms/introduction-to-the-datarepeater-control-visual-studio.md) </span><span class="sxs-lookup"><span data-stu-id="ee781-225">[Introduction to the DataRepeater Control](../../../visual-basic/developing-apps/windows-forms/introduction-to-the-datarepeater-control-visual-studio.md) </span></span>  
<span data-ttu-id="ee781-226"> [Comment : afficher des données liées dans un contrôle DataRepeater](../../../visual-basic/developing-apps/windows-forms/how-to-display-bound-data-in-a-datarepeater-control-visual-studio.md) </span><span class="sxs-lookup"><span data-stu-id="ee781-226"> [How to: Display Bound Data in a DataRepeater Control](../../../visual-basic/developing-apps/windows-forms/how-to-display-bound-data-in-a-datarepeater-control-visual-studio.md) </span></span>  
<span data-ttu-id="ee781-227"> [Comment : afficher les contrôles indépendants dans un contrôle DataRepeater](../../../visual-basic/developing-apps/windows-forms/how-to-display-unbound-controls-in-a-datarepeater-control-visual-studio.md) </span><span class="sxs-lookup"><span data-stu-id="ee781-227"> [How to: Display Unbound Controls in a DataRepeater Control](../../../visual-basic/developing-apps/windows-forms/how-to-display-unbound-controls-in-a-datarepeater-control-visual-studio.md) </span></span>  
<span data-ttu-id="ee781-228"> [Comment : modifier la disposition d’un contrôle DataRepeater](../../../visual-basic/developing-apps/windows-forms/how-to-change-the-layout-of-a-datarepeater-control-visual-studio.md) </span><span class="sxs-lookup"><span data-stu-id="ee781-228"> [How to: Change the Layout of a DataRepeater Control](../../../visual-basic/developing-apps/windows-forms/how-to-change-the-layout-of-a-datarepeater-control-visual-studio.md) </span></span>  
<span data-ttu-id="ee781-229"> [Comment : afficher des en-têtes d’élément dans un contrôle DataRepeater](../../../visual-basic/developing-apps/windows-forms/how-to-display-item-headers-in-a-datarepeater-control-visual-studio.md) </span><span class="sxs-lookup"><span data-stu-id="ee781-229"> [How to: Display Item Headers in a DataRepeater Control](../../../visual-basic/developing-apps/windows-forms/how-to-display-item-headers-in-a-datarepeater-control-visual-studio.md) </span></span>  
<span data-ttu-id="ee781-230"> [Comment : rechercher des données dans un contrôle DataRepeater](../../../visual-basic/developing-apps/windows-forms/how-to-search-data-in-a-datarepeater-control-visual-studio.md) </span><span class="sxs-lookup"><span data-stu-id="ee781-230"> [How to: Search Data in a DataRepeater Control](../../../visual-basic/developing-apps/windows-forms/how-to-search-data-in-a-datarepeater-control-visual-studio.md) </span></span>  
<span data-ttu-id="ee781-231"> [Comment : créer un formulaire maître/détail en utilisant deux contrôles DataRepeater (Visual Studio)](../../../visual-basic/developing-apps/windows-forms/how-to-create-a-master-detail-form-by-using-two-datarepeater-controls.md) </span><span class="sxs-lookup"><span data-stu-id="ee781-231"> [How to: Create a Master/Detail Form by Using Two DataRepeater Controls (Visual Studio)](../../../visual-basic/developing-apps/windows-forms/how-to-create-a-master-detail-form-by-using-two-datarepeater-controls.md) </span></span>  
<span data-ttu-id="ee781-232"> [Comment : modifier l’apparence d’un contrôle DataRepeater](../../../visual-basic/developing-apps/windows-forms/how-to-change-the-appearance-of-a-datarepeater-control-visual-studio.md) </span><span class="sxs-lookup"><span data-stu-id="ee781-232"> [How to: Change the Appearance of a DataRepeater Control](../../../visual-basic/developing-apps/windows-forms/how-to-change-the-appearance-of-a-datarepeater-control-visual-studio.md) </span></span>  
<span data-ttu-id="ee781-233"> [Comment : désactiver l’ajout et la suppression d’éléments du contrôle DataRepeater](../../../visual-basic/developing-apps/windows-forms/how-to-disable-adding-and-deleting-datarepeater-items-visual-studio.md) </span><span class="sxs-lookup"><span data-stu-id="ee781-233"> [How to: Disable Adding and Deleting DataRepeater Items](../../../visual-basic/developing-apps/windows-forms/how-to-disable-adding-and-deleting-datarepeater-items-visual-studio.md) </span></span>  
<span data-ttu-id="ee781-234"> [Dépannage des problèmes liés au contrôle DataRepeater](../../../visual-basic/developing-apps/windows-forms/troubleshooting-the-datarepeater-control-visual-studio.md)</span><span class="sxs-lookup"><span data-stu-id="ee781-234"> [Troubleshooting the DataRepeater Control](../../../visual-basic/developing-apps/windows-forms/troubleshooting-the-datarepeater-control-visual-studio.md)</span></span>
