---
title: "Comment : trier et filtrer des données ADO.NET avec le composant BindingSource Windows Forms"
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
- sorting data
- data sorting [Windows Forms], ADO.NET
- data [Windows Forms], filtering
- BindingSource component [Windows Forms], sorting and filtering data
- filtering [Windows Forms], ADO.NET
- data [Windows Forms], sorting
- ADO.NET [Windows Forms]
ms.assetid: 6c206daf-d706-4602-9dbe-435343052063
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 46947e314394d56b5ef0439f33910bb493012db3
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-sort-and-filter-adonet-data-with-the-windows-forms-bindingsource-component"></a><span data-ttu-id="02675-102">Comment : trier et filtrer des données ADO.NET avec le composant BindingSource Windows Forms</span><span class="sxs-lookup"><span data-stu-id="02675-102">How to: Sort and Filter ADO.NET Data with the Windows Forms BindingSource Component</span></span>
<span data-ttu-id="02675-103">Vous pouvez exposer le tri et filtrage de <xref:System.Windows.Forms.BindingSource> contrôler via le <xref:System.Windows.Forms.BindingSource.Sort%2A> et <xref:System.Windows.Forms.BindingSource.Filter%2A> propriétés.</span><span class="sxs-lookup"><span data-stu-id="02675-103">You can expose the sorting and filtering capability of <xref:System.Windows.Forms.BindingSource> control through the <xref:System.Windows.Forms.BindingSource.Sort%2A> and <xref:System.Windows.Forms.BindingSource.Filter%2A> properties.</span></span> <span data-ttu-id="02675-104">Vous pouvez appliquer un tri simple lorsque la source de données sous-jacente est une <xref:System.ComponentModel.IBindingList>, et vous pouvez appliquer le filtrage et tri avancé lorsque la source de données est un <xref:System.ComponentModel.IBindingListView>.</span><span class="sxs-lookup"><span data-stu-id="02675-104">You can apply simple sorting when the underlying data source is an <xref:System.ComponentModel.IBindingList>, and you can apply filtering and advanced sorting when the data source is an <xref:System.ComponentModel.IBindingListView>.</span></span> <span data-ttu-id="02675-105">Le <xref:System.Windows.Forms.BindingSource.Sort%2A> propriété requiert standard [!INCLUDE[vstecado](../../../../includes/vstecado-md.md)] syntaxe : une chaîne représentant le nom d’une colonne de données dans la source de données suivie `ASC` ou `DESC` pour indiquer si la liste doit être triée dans l’ordre croissant ou décroissant.</span><span class="sxs-lookup"><span data-stu-id="02675-105">The <xref:System.Windows.Forms.BindingSource.Sort%2A> property requires standard [!INCLUDE[vstecado](../../../../includes/vstecado-md.md)] syntax: a string representing the name of a column of data in the data source followed by `ASC` or `DESC` to indicate whether the list should be sorted in ascending or descending order.</span></span> <span data-ttu-id="02675-106">Vous pouvez définir le tri avancé ou un tri sur plusieurs colonnes en séparant chaque colonne avec un séparateur de virgule.</span><span class="sxs-lookup"><span data-stu-id="02675-106">You can set advanced sorting or multiple-column sorting by separating each column with a comma separator.</span></span> <span data-ttu-id="02675-107">Le <xref:System.Windows.Forms.BindingSource.Filter%2A> propriété prend une expression de chaîne.</span><span class="sxs-lookup"><span data-stu-id="02675-107">The <xref:System.Windows.Forms.BindingSource.Filter%2A> property takes a string expression.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="02675-108">Le stockage d'informations sensibles (telles qu'un mot de passe) dans la chaîne de connexion peut affecter la sécurité de votre application.</span><span class="sxs-lookup"><span data-stu-id="02675-108">Storing sensitive information, such as a password, within the connection string can affect the security of your application.</span></span> <span data-ttu-id="02675-109">L'utilisation de l'authentification Windows (également appelée sécurité intégrée) offre un moyen plus sûr de contrôler l'accès à une base de données.</span><span class="sxs-lookup"><span data-stu-id="02675-109">Using Windows Authentication (also known as integrated security) is a more secure way to control access to a database.</span></span> <span data-ttu-id="02675-110">Pour plus d’informations, consultez [Protection des informations de connexion](../../../../docs/framework/data/adonet/protecting-connection-information.md).</span><span class="sxs-lookup"><span data-stu-id="02675-110">For more information, see [Protecting Connection Information](../../../../docs/framework/data/adonet/protecting-connection-information.md).</span></span>  
  
### <a name="to-filter-data-with-the-bindingsource"></a><span data-ttu-id="02675-111">Pour filtrer les données avec le composant BindingSource</span><span class="sxs-lookup"><span data-stu-id="02675-111">To filter data with the BindingSource</span></span>  
  
-   <span data-ttu-id="02675-112">Définir le <xref:System.Windows.Forms.BindingSource.Filter%2A> propriété expression que vous souhaitez utiliser.</span><span class="sxs-lookup"><span data-stu-id="02675-112">Set the <xref:System.Windows.Forms.BindingSource.Filter%2A> property to expression that you want.</span></span>  
  
     <span data-ttu-id="02675-113">Dans l’exemple de code suivant, l’expression est un nom de colonne suivi par la valeur souhaitée pour la colonne.</span><span class="sxs-lookup"><span data-stu-id="02675-113">In the following code example, the expression is a column name followed by value that you want for the column.</span></span>  
  
 [!code-csharp[System.Windows.Forms.DataConnectorFilterAndSort#11](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataConnectorFilterAndSort/CS/form1.cs#11)]
 [!code-vb[System.Windows.Forms.DataConnectorFilterAndSort#11](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataConnectorFilterAndSort/VB/form1.vb#11)]  
  
### <a name="to-sort-data-with-the-bindingsource"></a><span data-ttu-id="02675-114">Pour trier les données avec le composant BindingSource</span><span class="sxs-lookup"><span data-stu-id="02675-114">To sort data with the BindingSource</span></span>  
  
1.  <span data-ttu-id="02675-115">Définir le <xref:System.Windows.Forms.BindingSource.Sort%2A> propriété le nom de colonne que vous souhaitez suivi `ASC` ou `DESC` pour indiquer l’ordre croissant ou décroissant.</span><span class="sxs-lookup"><span data-stu-id="02675-115">Set the <xref:System.Windows.Forms.BindingSource.Sort%2A> property to the column name that you want followed by `ASC` or `DESC` to indicate the ascending or descending order.</span></span>  
  
2.  <span data-ttu-id="02675-116">Séparez plusieurs colonnes par une virgule.</span><span class="sxs-lookup"><span data-stu-id="02675-116">Separate multiple columns with a comma.</span></span>  
  
 [!code-csharp[System.Windows.Forms.DataConnectorFilterAndSort#12](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataConnectorFilterAndSort/CS/form1.cs#12)]
 [!code-vb[System.Windows.Forms.DataConnectorFilterAndSort#12](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataConnectorFilterAndSort/VB/form1.vb#12)]  
  
## <a name="example"></a><span data-ttu-id="02675-117">Exemple</span><span class="sxs-lookup"><span data-stu-id="02675-117">Example</span></span>  
 <span data-ttu-id="02675-118">L’exemple de code suivant charge des données à partir de la table Customers de la base de données Northwind dans un <xref:System.Windows.Forms.DataGridView> contrôler, puis filtre et trie les données affichées.</span><span class="sxs-lookup"><span data-stu-id="02675-118">The following code example loads data from the Customers table of the Northwind sample database into a <xref:System.Windows.Forms.DataGridView> control, and filters and sorts the displayed data.</span></span>  
  
 [!code-csharp[System.Windows.Forms.DataConnectorFilterAndSort#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataConnectorFilterAndSort/CS/form1.cs#1)]
 [!code-vb[System.Windows.Forms.DataConnectorFilterAndSort#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataConnectorFilterAndSort/VB/form1.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="02675-119">Compilation du code</span><span class="sxs-lookup"><span data-stu-id="02675-119">Compiling the Code</span></span>  
 <span data-ttu-id="02675-120">Pour exécuter cet exemple, collez le code dans un formulaire contenant un <xref:System.Windows.Forms.BindingSource> nommé `BindingSource1` et un <xref:System.Windows.Forms.DataGridView> nommé `dataGridView1`.</span><span class="sxs-lookup"><span data-stu-id="02675-120">To run this example, paste the code into a form that contains a <xref:System.Windows.Forms.BindingSource> named `BindingSource1` and a <xref:System.Windows.Forms.DataGridView> named `dataGridView1`.</span></span> <span data-ttu-id="02675-121">Gérer les <xref:System.Windows.Forms.Form.Load> événement pour le formulaire et appelez `InitializeSortedFilteredBindingSource` dans la méthode de gestionnaire d’événements de charge.</span><span class="sxs-lookup"><span data-stu-id="02675-121">Handle the <xref:System.Windows.Forms.Form.Load> event for the form and call `InitializeSortedFilteredBindingSource` in the load event handler method.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="02675-122">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="02675-122">See Also</span></span>  
 <xref:System.Windows.Forms.BindingSource.Sort%2A>  
 <xref:System.Windows.Forms.BindingSource.Filter%2A>  
 [<span data-ttu-id="02675-123">Guide pratique pour installer des exemples de bases de données</span><span class="sxs-lookup"><span data-stu-id="02675-123">How to: Install Sample Databases</span></span>](http://msdn.microsoft.com/library/ed1291f6-604c-4972-ae22-0345c6dea12e)  
 [<span data-ttu-id="02675-124">BindingSource, composant</span><span class="sxs-lookup"><span data-stu-id="02675-124">BindingSource Component</span></span>](../../../../docs/framework/winforms/controls/bindingsource-component.md)
