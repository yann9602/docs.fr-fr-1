---
title: "Comment : créer un formulaire maître / détail utilisant deux contrôles de DataGridView Windows Forms"
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
- DataGridView control [Windows Forms], master/detail form
- parent-child tables [Windows Forms], displaying on Windows Forms
- master-details lists [Windows Forms], creating
ms.assetid: 99f6e876-3f7f-4139-9063-e36587c95b02
caps.latest.revision: "23"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 0b18e26ff20496248e4525bc31722cf6fcbbc3da
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-create-a-masterdetail-form-using-two-windows-forms-datagridview-controls"></a><span data-ttu-id="f75bc-102">Comment : créer un formulaire maître/détail utilisant deux contrôles DataGridView Windows Form</span><span class="sxs-lookup"><span data-stu-id="f75bc-102">How to: Create a Master/Detail Form Using Two Windows Forms DataGridView Controls</span></span>
<span data-ttu-id="f75bc-103">L'exemple de code suivant crée un formulaire maître/détail avec deux contrôles <xref:System.Windows.Forms.DataGridView> liés à deux composants <xref:System.Windows.Forms.BindingSource>.</span><span class="sxs-lookup"><span data-stu-id="f75bc-103">The following code example creates a master/detail form using two <xref:System.Windows.Forms.DataGridView> controls bound to two <xref:System.Windows.Forms.BindingSource> components.</span></span> <span data-ttu-id="f75bc-104">La source de données est un <xref:System.Data.DataSet> qui contient les tables `Customers` et `Orders` de l'exemple de base de données Northwind SQL Server, ainsi qu'un <xref:System.Data.DataRelation> qui associe les deux par l'intermédiaire de la colonne `CustomerID`.</span><span class="sxs-lookup"><span data-stu-id="f75bc-104">The data source is a <xref:System.Data.DataSet> that contains the `Customers` and `Orders` tables from the Northwind SQL Server sample database along with a <xref:System.Data.DataRelation> that relates the two through the `CustomerID` column.</span></span>  
  
 <span data-ttu-id="f75bc-105">Un <xref:System.Windows.Forms.BindingSource> est lié à la table `Customers` parente dans le jeu de données.</span><span class="sxs-lookup"><span data-stu-id="f75bc-105">One <xref:System.Windows.Forms.BindingSource> is bound to the parent `Customers` table in the data set.</span></span> <span data-ttu-id="f75bc-106">Ces données sont affichées dans le contrôle <xref:System.Windows.Forms.DataGridView> maître.</span><span class="sxs-lookup"><span data-stu-id="f75bc-106">This data is displayed in the master <xref:System.Windows.Forms.DataGridView> control.</span></span> <span data-ttu-id="f75bc-107">L'autre <xref:System.Windows.Forms.BindingSource> est lié au premier connecteur de données.</span><span class="sxs-lookup"><span data-stu-id="f75bc-107">The other <xref:System.Windows.Forms.BindingSource> is bound to the first data connector.</span></span> <span data-ttu-id="f75bc-108">La propriété <xref:System.Windows.Forms.BindingSource.DataMember%2A> du deuxième <xref:System.Windows.Forms.BindingSource> a comme valeur le nom de <xref:System.Data.DataRelation>.</span><span class="sxs-lookup"><span data-stu-id="f75bc-108">The <xref:System.Windows.Forms.BindingSource.DataMember%2A> property of the second <xref:System.Windows.Forms.BindingSource> is set to the <xref:System.Data.DataRelation> name.</span></span> <span data-ttu-id="f75bc-109">Cela a pour conséquence l'affichage, par le contrôle <xref:System.Windows.Forms.DataGridView> détail, des lignes de la table `Orders` enfant qui correspondent à la ligne actuelle dans le contrôle <xref:System.Windows.Forms.DataGridView> maître.</span><span class="sxs-lookup"><span data-stu-id="f75bc-109">This causes the associated detail <xref:System.Windows.Forms.DataGridView> control to display the rows of the child `Orders` table that correspond to the current row in the master <xref:System.Windows.Forms.DataGridView> control.</span></span>  
  
 <span data-ttu-id="f75bc-110">Pour obtenir une explication complète de cet exemple de code, consultez [procédure pas à pas : création d’un maître/détail formulaire à l’aide de deux contrôles DataGridView Windows Forms](../../../../docs/framework/winforms/controls/creating-a-master-detail-form-using-two-datagridviews.md).</span><span class="sxs-lookup"><span data-stu-id="f75bc-110">For a complete explanation of this code example, see [Walkthrough: Creating a Master/Detail Form Using Two Windows Forms DataGridView Controls](../../../../docs/framework/winforms/controls/creating-a-master-detail-form-using-two-datagridviews.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="f75bc-111">Exemple</span><span class="sxs-lookup"><span data-stu-id="f75bc-111">Example</span></span>  
 [!code-csharp[System.Windows.Forms.DataGridViewMasterDetails#00](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMasterDetails/CS/masterdetails.cs#00)]
 [!code-vb[System.Windows.Forms.DataGridViewMasterDetails#00](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMasterDetails/VB/masterdetails.vb#00)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="f75bc-112">Compilation du code</span><span class="sxs-lookup"><span data-stu-id="f75bc-112">Compiling the Code</span></span>  
 <span data-ttu-id="f75bc-113">Cet exemple nécessite :</span><span class="sxs-lookup"><span data-stu-id="f75bc-113">This example requires:</span></span>  
  
 <span data-ttu-id="f75bc-114">des références aux assemblys System, System.Data, System.Windows.Forms et System.XML.</span><span class="sxs-lookup"><span data-stu-id="f75bc-114">References to the System, System.Data, System.Windows.Forms, and System.XML assemblies.</span></span>  
  
 <span data-ttu-id="f75bc-115">Pour plus d’informations sur la création de cet exemple à partir de la ligne de commande pour [!INCLUDE[vbprvb](../../../../includes/vbprvb-md.md)] ou [!INCLUDE[csprcs](../../../../includes/csprcs-md.md)], consultez [Génération à partir de la ligne de commande](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) ou [Génération à partir de la ligne de commande avec csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span><span class="sxs-lookup"><span data-stu-id="f75bc-115">For information about building this example from the command line for [!INCLUDE[vbprvb](../../../../includes/vbprvb-md.md)] or [!INCLUDE[csprcs](../../../../includes/csprcs-md.md)], see [Building from the Command Line](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) or [Command-line Building With csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span></span> <span data-ttu-id="f75bc-116">Vous pouvez également générer cet exemple dans [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)] en collant le code dans un nouveau projet.</span><span class="sxs-lookup"><span data-stu-id="f75bc-116">You can also build this example in [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)] by pasting the code into a new project.</span></span>  <span data-ttu-id="f75bc-117">Consultez également [Comment : compiler et exécuter un complète exemple Windows Forms Code à l’aide de Visual Studio](http://msdn.microsoft.com/library/Bb129228\(v=vs.110\))</span><span class="sxs-lookup"><span data-stu-id="f75bc-117">Also see [How to: Compile and Run a Complete Windows Forms Code Example Using Visual Studio](http://msdn.microsoft.com/library/Bb129228\(v=vs.110\))</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="f75bc-118">Sécurité .NET Framework</span><span class="sxs-lookup"><span data-stu-id="f75bc-118">.NET Framework Security</span></span>  
 <span data-ttu-id="f75bc-119">Le stockage d'informations sensibles (telles qu'un mot de passe) dans la chaîne de connexion peut affecter la sécurité de votre application.</span><span class="sxs-lookup"><span data-stu-id="f75bc-119">Storing sensitive information, such as a password, within the connection string can affect the security of your application.</span></span> <span data-ttu-id="f75bc-120">L'utilisation de l'authentification Windows (également appelée sécurité intégrée) offre un moyen plus sûr de contrôler l'accès à une base de données.</span><span class="sxs-lookup"><span data-stu-id="f75bc-120">Using Windows Authentication (also known as integrated security) is a more secure way to control access to a database.</span></span> <span data-ttu-id="f75bc-121">Pour plus d’informations, consultez [Protection des informations de connexion](../../../../docs/framework/data/adonet/protecting-connection-information.md).</span><span class="sxs-lookup"><span data-stu-id="f75bc-121">For more information, see [Protecting Connection Information](../../../../docs/framework/data/adonet/protecting-connection-information.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f75bc-122">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="f75bc-122">See Also</span></span>  
 <xref:System.Windows.Forms.DataGridView>  
 <xref:System.Windows.Forms.BindingSource>  
 [<span data-ttu-id="f75bc-123">Procédure pas à pas : création d'un formulaire maître/détail qui utilise deux contrôles DataGridView Windows Forms</span><span class="sxs-lookup"><span data-stu-id="f75bc-123">Walkthrough: Creating a Master/Detail Form Using Two Windows Forms DataGridView Controls</span></span>](../../../../docs/framework/winforms/controls/creating-a-master-detail-form-using-two-datagridviews.md)  
 [<span data-ttu-id="f75bc-124">Affichage des données dans le contrôle DataGridView Windows Forms</span><span class="sxs-lookup"><span data-stu-id="f75bc-124">Displaying Data in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/displaying-data-in-the-windows-forms-datagridview-control.md)  
 [<span data-ttu-id="f75bc-125">Protection des informations de connexion</span><span class="sxs-lookup"><span data-stu-id="f75bc-125">Protecting Connection Information</span></span>](../../../../docs/framework/data/adonet/protecting-connection-information.md)
