---
title: "Procédure pas à pas : gestion des erreurs qui se produisent lors de la saisie de données dans le contrôle DataGridView Windows Forms"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- error handling [Windows Forms], dataGridView control
- data grids [Windows Forms], error handling
- DataGridView control [Windows Forms], error handling
- data entry [Windows Forms], error handling
- error handling [Windows Forms], data entry
- walkthroughs [Windows Forms], DataGridView control
ms.assetid: 30a68b85-d3af-4946-83c1-1e2d010d0511
caps.latest.revision: "17"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 7c602af6799da57fec904c87da7bed77c0040eff
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="walkthrough-handling-errors-that-occur-during-data-entry-in-the-windows-forms-datagridview-control"></a><span data-ttu-id="1030b-102">Procédure pas à pas : gestion des erreurs qui se produisent lors de la saisie de données dans le contrôle DataGridView Windows Forms</span><span class="sxs-lookup"><span data-stu-id="1030b-102">Walkthrough: Handling Errors that Occur During Data Entry in the Windows Forms DataGridView Control</span></span>
<span data-ttu-id="1030b-103">Gestion des erreurs dans le magasin de données sous-jacent sont une fonctionnalité requise pour une application de saisie de données.</span><span class="sxs-lookup"><span data-stu-id="1030b-103">Handling errors from the underlying data store is a required feature for a data-entry application.</span></span> <span data-ttu-id="1030b-104">Windows Forms <xref:System.Windows.Forms.DataGridView> contrôle facilite cette procédure en exposant les <xref:System.Windows.Forms.DataGridView.DataError> événement, qui est déclenché lorsque le magasin de données détecte une violation de contrainte ou une règle métier.</span><span class="sxs-lookup"><span data-stu-id="1030b-104">The Windows Forms <xref:System.Windows.Forms.DataGridView> control makes this easy by exposing the <xref:System.Windows.Forms.DataGridView.DataError> event, which is raised when the data store detects a constraint violation or a broken business rule.</span></span>  
  
 <span data-ttu-id="1030b-105">Dans cette procédure pas à pas, vous allez récupérer des lignes à partir de la `Customers` de table dans la base de données Northwind et les afficher dans un <xref:System.Windows.Forms.DataGridView> contrôle.</span><span class="sxs-lookup"><span data-stu-id="1030b-105">In this walkthrough, you will retrieve rows from the `Customers` table in the Northwind sample database and display them in a <xref:System.Windows.Forms.DataGridView> control.</span></span> <span data-ttu-id="1030b-106">Lorsqu’un doublon `CustomerID` est détectée dans une nouvelle ligne ou une ligne existante modifiée, le <xref:System.Windows.Forms.DataGridView.DataError> événement se produit, qui sera géré en affichant un <xref:System.Windows.Forms.MessageBox> qui décrit l’exception.</span><span class="sxs-lookup"><span data-stu-id="1030b-106">When a duplicate `CustomerID` value is detected in a new row or an edited existing row, the <xref:System.Windows.Forms.DataGridView.DataError> event will occur, which will be handled by displaying a <xref:System.Windows.Forms.MessageBox> that describes the exception.</span></span>  
  
 <span data-ttu-id="1030b-107">Pour copier le code dans cette rubrique sous forme de liste unique, consultez [Comment : gérer les erreurs que se produisent au cours de saisie de données dans le contrôle DataGridView Windows Forms](../../../../docs/framework/winforms/controls/handle-errors-that-occur-during-data-entry-in-the-datagrid.md).</span><span class="sxs-lookup"><span data-stu-id="1030b-107">To copy the code in this topic as a single listing, see [How to: Handle Errors That Occur During Data Entry in the Windows Forms DataGridView Control](../../../../docs/framework/winforms/controls/handle-errors-that-occur-during-data-entry-in-the-datagrid.md).</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="1030b-108">Conditions préalables</span><span class="sxs-lookup"><span data-stu-id="1030b-108">Prerequisites</span></span>  
 <span data-ttu-id="1030b-109">Pour exécuter cette procédure pas à pas, vous avez besoin des éléments suivants :</span><span class="sxs-lookup"><span data-stu-id="1030b-109">In order to complete this walkthrough, you will need:</span></span>  
  
-   <span data-ttu-id="1030b-110">Accès à un serveur doté de la base de données Northwind SQL Server.</span><span class="sxs-lookup"><span data-stu-id="1030b-110">Access to a server that has the Northwind SQL Server sample database.</span></span>  
  
## <a name="creating-the-form"></a><span data-ttu-id="1030b-111">Création du formulaire</span><span class="sxs-lookup"><span data-stu-id="1030b-111">Creating the Form</span></span>  
  
#### <a name="to-handle-data-entry-errors-in-the-datagridview-control"></a><span data-ttu-id="1030b-112">Pour gérer les erreurs de saisie de données dans le contrôle DataGridView</span><span class="sxs-lookup"><span data-stu-id="1030b-112">To handle data-entry errors in the DataGridView control</span></span>  
  
1.  <span data-ttu-id="1030b-113">Créez une classe qui dérive de <xref:System.Windows.Forms.Form> et contient un <xref:System.Windows.Forms.DataGridView> contrôle et un <xref:System.Windows.Forms.BindingSource> composant.</span><span class="sxs-lookup"><span data-stu-id="1030b-113">Create a class that derives from <xref:System.Windows.Forms.Form> and contains a <xref:System.Windows.Forms.DataGridView> control and a <xref:System.Windows.Forms.BindingSource> component.</span></span>  
  
     <span data-ttu-id="1030b-114">L’exemple de code suivant fournit l’initialisation de base et inclut un `Main` (méthode).</span><span class="sxs-lookup"><span data-stu-id="1030b-114">The following code example provides basic initialization and includes a `Main` method.</span></span>  
  
     [!code-csharp[System.Windows.Forms.DataGridView.DataError#01](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.DataError/CS/errorhandling.cs#01)]
     [!code-vb[System.Windows.Forms.DataGridView.DataError#01](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.DataError/VB/errorhandling.vb#01)]  
    [!code-csharp[System.Windows.Forms.DataGridView.DataError#02](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.DataError/CS/errorhandling.cs#02)]
    [!code-vb[System.Windows.Forms.DataGridView.DataError#02](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.DataError/VB/errorhandling.vb#02)]  
  
2.  <span data-ttu-id="1030b-115">Implémentez une méthode dans la définition de classe de votre formulaire pour gérer les détails de la connexion à la base de données.</span><span class="sxs-lookup"><span data-stu-id="1030b-115">Implement a method in your form's class definition for handling the details of connecting to the database.</span></span>  
  
     <span data-ttu-id="1030b-116">Cet exemple de code utilise un `GetData` méthode qui retourne un remplis <xref:System.Data.DataTable> objet.</span><span class="sxs-lookup"><span data-stu-id="1030b-116">This code example uses a `GetData` method that returns a populated <xref:System.Data.DataTable> object.</span></span> <span data-ttu-id="1030b-117">Vérifiez que vous le `connectionString` variable une valeur qui est appropriée pour votre base de données.</span><span class="sxs-lookup"><span data-stu-id="1030b-117">Be sure that you set the `connectionString` variable to a value that is appropriate for your database.</span></span>  
  
    > [!IMPORTANT]
    >  <span data-ttu-id="1030b-118">Le stockage d'informations sensibles (telles qu'un mot de passe) dans la chaîne de connexion peut affecter la sécurité de votre application.</span><span class="sxs-lookup"><span data-stu-id="1030b-118">Storing sensitive information, such as a password, within the connection string can affect the security of your application.</span></span> <span data-ttu-id="1030b-119">L'utilisation de l'authentification Windows (également appelée sécurité intégrée) offre un moyen plus sûr de contrôler l'accès à une base de données.</span><span class="sxs-lookup"><span data-stu-id="1030b-119">Using Windows Authentication (also known as integrated security) is a more secure way to control access to a database.</span></span> <span data-ttu-id="1030b-120">Pour plus d’informations, consultez [Protection des informations de connexion](../../../../docs/framework/data/adonet/protecting-connection-information.md).</span><span class="sxs-lookup"><span data-stu-id="1030b-120">For more information, see [Protecting Connection Information](../../../../docs/framework/data/adonet/protecting-connection-information.md).</span></span>  
  
     [!code-csharp[System.Windows.Forms.DataGridView.DataError#30](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.DataError/CS/errorhandling.cs#30)]
     [!code-vb[System.Windows.Forms.DataGridView.DataError#30](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.DataError/VB/errorhandling.vb#30)]  
  
3.  <span data-ttu-id="1030b-121">Implémentez un gestionnaire pour de votre formulaire <xref:System.Windows.Forms.Form.Load> événement qui initialise le <xref:System.Windows.Forms.DataGridView> et <xref:System.Windows.Forms.BindingSource> et configure la liaison de données.</span><span class="sxs-lookup"><span data-stu-id="1030b-121">Implement a handler for your form's <xref:System.Windows.Forms.Form.Load> event that initializes the <xref:System.Windows.Forms.DataGridView> and <xref:System.Windows.Forms.BindingSource> and sets up the data binding.</span></span>  
  
     [!code-csharp[System.Windows.Forms.DataGridView.DataError#10](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.DataError/CS/errorhandling.cs#10)]
     [!code-vb[System.Windows.Forms.DataGridView.DataError#10](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.DataError/VB/errorhandling.vb#10)]  
  
4.  <span data-ttu-id="1030b-122">Gérer les <xref:System.Windows.Forms.DataGridView.DataError> événement sur le <xref:System.Windows.Forms.DataGridView>.</span><span class="sxs-lookup"><span data-stu-id="1030b-122">Handle the <xref:System.Windows.Forms.DataGridView.DataError> event on the <xref:System.Windows.Forms.DataGridView>.</span></span>  
  
     <span data-ttu-id="1030b-123">Si le contexte de l’erreur est une opération de validation, affichez l’erreur dans un <xref:System.Windows.Forms.MessageBox>.</span><span class="sxs-lookup"><span data-stu-id="1030b-123">If the context for the error is a commit operation, display the error in a <xref:System.Windows.Forms.MessageBox>.</span></span>  
  
     [!code-csharp[System.Windows.Forms.DataGridView.DataError#20](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.DataError/CS/errorhandling.cs#20)]
     [!code-vb[System.Windows.Forms.DataGridView.DataError#20](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.DataError/VB/errorhandling.vb#20)]  
  
## <a name="testing-the-application"></a><span data-ttu-id="1030b-124">Test de l'application</span><span class="sxs-lookup"><span data-stu-id="1030b-124">Testing the Application</span></span>  
 <span data-ttu-id="1030b-125">Vous pouvez maintenant tester le formulaire pour vous assurer qu’il se comporte comme prévu.</span><span class="sxs-lookup"><span data-stu-id="1030b-125">You can now test the form to make sure it behaves as expected.</span></span>  
  
#### <a name="to-test-the-form"></a><span data-ttu-id="1030b-126">Pour tester le formulaire</span><span class="sxs-lookup"><span data-stu-id="1030b-126">To test the form</span></span>  
  
-   <span data-ttu-id="1030b-127">Appuyez sur F5 pour exécuter l'application.</span><span class="sxs-lookup"><span data-stu-id="1030b-127">Press F5 to run the application.</span></span>  
  
     <span data-ttu-id="1030b-128">Vous verrez un <xref:System.Windows.Forms.DataGridView> contrôle rempli avec des données à partir de la table Customers.</span><span class="sxs-lookup"><span data-stu-id="1030b-128">You will see a <xref:System.Windows.Forms.DataGridView> control filled with data from the Customers table.</span></span> <span data-ttu-id="1030b-129">Si vous entrez une valeur en double pour `CustomerID` et valider la modification, la valeur de cellule reprendra automatiquement et vous verrez un <xref:System.Windows.Forms.MessageBox> qui affiche l’erreur de saisie de données.</span><span class="sxs-lookup"><span data-stu-id="1030b-129">If you enter a duplicate value for `CustomerID` and commit the edit, the cell value will revert automatically and you will see a <xref:System.Windows.Forms.MessageBox> that displays the data entry error.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="1030b-130">Étapes suivantes</span><span class="sxs-lookup"><span data-stu-id="1030b-130">Next Steps</span></span>  
 <span data-ttu-id="1030b-131">Cette application vous donne une connaissance élémentaire de la <xref:System.Windows.Forms.DataGridView> fonctionnalités du contrôle.</span><span class="sxs-lookup"><span data-stu-id="1030b-131">This application gives you a basic understanding of the <xref:System.Windows.Forms.DataGridView> control's capabilities.</span></span> <span data-ttu-id="1030b-132">Vous pouvez personnaliser l’apparence et le comportement de la <xref:System.Windows.Forms.DataGridView> contrôle de plusieurs manières :</span><span class="sxs-lookup"><span data-stu-id="1030b-132">You can customize the appearance and behavior of the <xref:System.Windows.Forms.DataGridView> control in several ways:</span></span>  
  
-   <span data-ttu-id="1030b-133">Modifier les styles de bordure et en-tête.</span><span class="sxs-lookup"><span data-stu-id="1030b-133">Change border and header styles.</span></span> <span data-ttu-id="1030b-134">Pour plus d’informations, consultez [Comment : modifier la bordure et les Styles de quadrillage dans le contrôle DataGridView Windows Forms](../../../../docs/framework/winforms/controls/change-the-border-and-gridline-styles-in-the-datagrid.md).</span><span class="sxs-lookup"><span data-stu-id="1030b-134">For more information, see [How to: Change the Border and Gridline Styles in the Windows Forms DataGridView Control](../../../../docs/framework/winforms/controls/change-the-border-and-gridline-styles-in-the-datagrid.md).</span></span>  
  
-   <span data-ttu-id="1030b-135">Activer ou restreindre l’entrée d’utilisateur à le <xref:System.Windows.Forms.DataGridView> contrôle.</span><span class="sxs-lookup"><span data-stu-id="1030b-135">Enable or restrict user input to the <xref:System.Windows.Forms.DataGridView> control.</span></span> <span data-ttu-id="1030b-136">Pour plus d’informations, consultez [Comment : empêcher l’ajout ligne et la suppression dans le contrôle DataGridView Windows Forms](../../../../docs/framework/winforms/controls/prevent-row-addition-and-deletion-datagridview.md), et [Comment : rendre en lecture seule les colonnes dans le contrôle DataGridView Windows Forms](../../../../docs/framework/winforms/controls/how-to-make-columns-read-only-in-the-windows-forms-datagridview-control.md).</span><span class="sxs-lookup"><span data-stu-id="1030b-136">For more information, see [How to: Prevent Row Addition and Deletion in the Windows Forms DataGridView Control](../../../../docs/framework/winforms/controls/prevent-row-addition-and-deletion-datagridview.md), and [How to: Make Columns Read-Only in the Windows Forms DataGridView Control](../../../../docs/framework/winforms/controls/how-to-make-columns-read-only-in-the-windows-forms-datagridview-control.md).</span></span>  
  
-   <span data-ttu-id="1030b-137">Valider l’entrée d’utilisateur pour le <xref:System.Windows.Forms.DataGridView> contrôle.</span><span class="sxs-lookup"><span data-stu-id="1030b-137">Validate user input to the <xref:System.Windows.Forms.DataGridView> control.</span></span> <span data-ttu-id="1030b-138">Pour plus d’informations, consultez [procédure pas à pas : validation des données dans le contrôle DataGridView Windows Forms](../../../../docs/framework/winforms/controls/walkthrough-validating-data-in-the-windows-forms-datagridview-control.md).</span><span class="sxs-lookup"><span data-stu-id="1030b-138">For more information, see [Walkthrough: Validating Data in the Windows Forms DataGridView Control](../../../../docs/framework/winforms/controls/walkthrough-validating-data-in-the-windows-forms-datagridview-control.md).</span></span>  
  
-   <span data-ttu-id="1030b-139">Gérer des jeux de données très volumineux à l’aide du mode virtuel.</span><span class="sxs-lookup"><span data-stu-id="1030b-139">Handle very large data sets using virtual mode.</span></span> <span data-ttu-id="1030b-140">Pour plus d’informations, consultez [procédure pas à pas : implémentation du Mode virtuel dans le contrôle DataGridView Windows Forms](../../../../docs/framework/winforms/controls/implementing-virtual-mode-wf-datagridview-control.md).</span><span class="sxs-lookup"><span data-stu-id="1030b-140">For more information, see [Walkthrough: Implementing Virtual Mode in the Windows Forms DataGridView Control](../../../../docs/framework/winforms/controls/implementing-virtual-mode-wf-datagridview-control.md).</span></span>  
  
-   <span data-ttu-id="1030b-141">Personnaliser l’apparence des cellules.</span><span class="sxs-lookup"><span data-stu-id="1030b-141">Customize the appearance of cells.</span></span> <span data-ttu-id="1030b-142">Pour plus d’informations, consultez [Comment : personnaliser l’apparence des cellules dans le contrôle DataGridView Windows Forms](../../../../docs/framework/winforms/controls/customize-the-appearance-of-cells-in-the-datagrid.md) et [Comment : définir des Styles de cellule par défaut pour le contrôle DataGridView Windows Forms](../../../../docs/framework/winforms/controls/how-to-set-default-cell-styles-for-the-windows-forms-datagridview-control.md).</span><span class="sxs-lookup"><span data-stu-id="1030b-142">For more information, see [How to: Customize the Appearance of Cells in the Windows Forms DataGridView Control](../../../../docs/framework/winforms/controls/customize-the-appearance-of-cells-in-the-datagrid.md) and [How to: Set Default Cell Styles for the Windows Forms DataGridView Control](../../../../docs/framework/winforms/controls/how-to-set-default-cell-styles-for-the-windows-forms-datagridview-control.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1030b-143">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="1030b-143">See Also</span></span>  
 <xref:System.Windows.Forms.DataGridView>  
 <xref:System.Windows.Forms.BindingSource>  
 [<span data-ttu-id="1030b-144">Saisie de données dans le contrôle DataGridView Windows Forms</span><span class="sxs-lookup"><span data-stu-id="1030b-144">Data Entry in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/data-entry-in-the-windows-forms-datagridview-control.md)  
 [<span data-ttu-id="1030b-145">Guide pratique pour gérer les erreurs qui se produisent lors de l'entrée de données dans le contrôle DataGridView Windows Forms</span><span class="sxs-lookup"><span data-stu-id="1030b-145">How to: Handle Errors That Occur During Data Entry in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/handle-errors-that-occur-during-data-entry-in-the-datagrid.md)  
 [<span data-ttu-id="1030b-146">Procédure pas à pas : validation des données dans le contrôle DataGridView Windows Forms</span><span class="sxs-lookup"><span data-stu-id="1030b-146">Walkthrough: Validating Data in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/walkthrough-validating-data-in-the-windows-forms-datagridview-control.md)  
 [<span data-ttu-id="1030b-147">Protection des informations de connexion</span><span class="sxs-lookup"><span data-stu-id="1030b-147">Protecting Connection Information</span></span>](../../../../docs/framework/data/adonet/protecting-connection-information.md)
