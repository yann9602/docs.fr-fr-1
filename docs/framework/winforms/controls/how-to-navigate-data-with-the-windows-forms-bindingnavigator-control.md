---
title: "Comment : naviguer parmi les données avec le contrôle BindingNavigator Windows Forms"
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
- BindingNavigator control [Windows Forms], navigating data
- data [Windows Forms], navigating
- data navigation
- examples [Windows Forms], BindingNavigator control
ms.assetid: 0e5d4f34-bc9b-47cf-9b8d-93acbb1f1dbb
caps.latest.revision: "18"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 6c5b49d84f98213e95c83c5476007297149adc16
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-navigate-data-with-the-windows-forms-bindingnavigator-control"></a><span data-ttu-id="72769-102">Comment : naviguer parmi les données avec le contrôle BindingNavigator Windows Forms</span><span class="sxs-lookup"><span data-stu-id="72769-102">How to: Navigate Data with the Windows Forms BindingNavigator Control</span></span>
<span data-ttu-id="72769-103">Le contrôle <xref:System.Windows.Forms.BindingNavigator> dans Windows Forms permet aux développeurs de fournir aux utilisateurs finaux une interface utilisateur de  navigation et de manipulation de données simple sur les formulaires qu'ils créent.</span><span class="sxs-lookup"><span data-stu-id="72769-103">The advent of the <xref:System.Windows.Forms.BindingNavigator> control in Windows Forms enables developers to provide end users with a simple data navigation and manipulation user interface on the forms they create.</span></span>  
  
 <span data-ttu-id="72769-104">Le contrôle <xref:System.Windows.Forms.BindingNavigator> est un contrôle <xref:System.Windows.Forms.ToolStrip> avec des boutons préconfigurés pour la navigation vers quatre enregistrements (premier, dernier, suivant et précédent) dans un jeu de données, ainsi que des boutons pour ajouter et supprimer des enregistrements.</span><span class="sxs-lookup"><span data-stu-id="72769-104">The <xref:System.Windows.Forms.BindingNavigator> control is a <xref:System.Windows.Forms.ToolStrip> control with buttons preconfigured for navigation to the first, last, next, and previous record in a data set, as well as buttons to add and delete records.</span></span> <span data-ttu-id="72769-105">L'ajout de boutons au contrôle <xref:System.Windows.Forms.BindingNavigator> est facile, car il s'agit d'un contrôle <xref:System.Windows.Forms.ToolStrip>.</span><span class="sxs-lookup"><span data-stu-id="72769-105">Adding buttons to the <xref:System.Windows.Forms.BindingNavigator> control is easy, because it is a <xref:System.Windows.Forms.ToolStrip> control.</span></span>  <span data-ttu-id="72769-106">Consultez également [Comment : ajouter des boutons Charger, Enregistrer et Annuler au contrôle BindingNavigator Windows Forms](http://msdn.microsoft.com/library/safa4957\(v=vs.110\)).</span><span class="sxs-lookup"><span data-stu-id="72769-106">Also see [How to: Add Load, Save, and Cancel Buttons to the Windows Forms BindingNavigator Control](http://msdn.microsoft.com/library/safa4957\(v=vs.110\)).</span></span>  
  
 <span data-ttu-id="72769-107">Pour chaque bouton sur le contrôle <xref:System.Windows.Forms.BindingNavigator>, il existe un membre correspondant du composant <xref:System.Windows.Forms.BindingSource> qui active par programmation la même fonctionnalité.</span><span class="sxs-lookup"><span data-stu-id="72769-107">For each button on the <xref:System.Windows.Forms.BindingNavigator> control, there is a corresponding member of the <xref:System.Windows.Forms.BindingSource> component that programmatically allows the same functionality.</span></span> <span data-ttu-id="72769-108">Par exemple, le bouton <xref:System.Windows.Forms.BindingNavigator.MoveFirstItem%2A> correspond à la méthode <xref:System.Windows.Forms.BindingSource.MoveFirst%2A> du composant <xref:System.Windows.Forms.BindingSource>, le bouton <xref:System.Windows.Forms.BindingNavigator.DeleteItem%2A> correspond à la méthode <xref:System.Windows.Forms.BindingSource.RemoveCurrent%2A>, et ainsi de suite.</span><span class="sxs-lookup"><span data-stu-id="72769-108">For example, the <xref:System.Windows.Forms.BindingNavigator.MoveFirstItem%2A> button corresponds to the <xref:System.Windows.Forms.BindingSource.MoveFirst%2A> method of the <xref:System.Windows.Forms.BindingSource> component, the <xref:System.Windows.Forms.BindingNavigator.DeleteItem%2A> button corresponds to the <xref:System.Windows.Forms.BindingSource.RemoveCurrent%2A> method, and so on.</span></span> <span data-ttu-id="72769-109">Ainsi, pour activer le contrôle <xref:System.Windows.Forms.BindingNavigator> pour parcourir des enregistrements de données, il suffit d'affecter à sa propriété <xref:System.Windows.Forms.BindingNavigator.BindingSource%2A> le composant <xref:System.Windows.Forms.BindingSource> approprié sur le formulaire.</span><span class="sxs-lookup"><span data-stu-id="72769-109">As a result, enabling the <xref:System.Windows.Forms.BindingNavigator> control to navigate data records is a simple as setting its <xref:System.Windows.Forms.BindingNavigator.BindingSource%2A> property to the appropriate <xref:System.Windows.Forms.BindingSource> component on the form.</span></span>  
  
### <a name="to-set-up-the-bindingnavigator-control"></a><span data-ttu-id="72769-110">Pour configurer le contrôle BindingNavigator</span><span class="sxs-lookup"><span data-stu-id="72769-110">To set up the BindingNavigator control</span></span>  
  
1.  <span data-ttu-id="72769-111">Ajoutez un composant <xref:System.Windows.Forms.BindingSource> nommé `bindingSource1` et deux contrôles <xref:System.Windows.Forms.TextBox> nommés `textBox1` et `textBox2`.</span><span class="sxs-lookup"><span data-stu-id="72769-111">Add a <xref:System.Windows.Forms.BindingSource> component named `bindingSource1` and two <xref:System.Windows.Forms.TextBox> controls named `textBox1` and `textBox2`.</span></span>  
  
2.  <span data-ttu-id="72769-112">Liez `bindingSource1` aux données et les contrôles de zone de texte à `bindingSource1`.</span><span class="sxs-lookup"><span data-stu-id="72769-112">Bind `bindingSource1` to data, and the textbox controls to `bindingSource1`.</span></span> <span data-ttu-id="72769-113">Pour cela, collez le code suivant dans votre formulaire et appelez `LoadData` à partir de la méthode de gestion d'événements <xref:System.Windows.Forms.Form.Load> ou du constructeur du formulaire.</span><span class="sxs-lookup"><span data-stu-id="72769-113">To do this, paste the following code into your form and call `LoadData` from the form's constructor or <xref:System.Windows.Forms.Form.Load> event-handling method.</span></span>  
  
     [!code-csharp[System.Windows.Forms.BindingNavigatorNavigate#2](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.BindingNavigatorNavigate/CS/Form1.cs#2)]
     [!code-vb[System.Windows.Forms.BindingNavigatorNavigate#2](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.BindingNavigatorNavigate/VB/Form1.vb#2)]  
  
3.  <span data-ttu-id="72769-114">Ajoutez un contrôle <xref:System.Windows.Forms.BindingNavigator> nommé `bindingNavigator1` à votre formulaire.</span><span class="sxs-lookup"><span data-stu-id="72769-114">Add a <xref:System.Windows.Forms.BindingNavigator> control named `bindingNavigator1` to your form.</span></span>  
  
4.  <span data-ttu-id="72769-115">Définissez la propriété <xref:System.Windows.Forms.BindingNavigator.BindingSource%2A> pour `bindingNavigator1` et `bindingSource1`.</span><span class="sxs-lookup"><span data-stu-id="72769-115">Set the <xref:System.Windows.Forms.BindingNavigator.BindingSource%2A> property for `bindingNavigator1` to `bindingSource1`.</span></span> <span data-ttu-id="72769-116">Vous pouvez la définir avec le concepteur ou dans le code.</span><span class="sxs-lookup"><span data-stu-id="72769-116">You can do this with the designer or in code.</span></span>  
  
     [!code-csharp[System.Windows.Forms.BindingNavigatorNavigate#3](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.BindingNavigatorNavigate/CS/Form1.cs#3)]
     [!code-vb[System.Windows.Forms.BindingNavigatorNavigate#3](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.BindingNavigatorNavigate/VB/Form1.vb#3)]  
  
## <a name="example"></a><span data-ttu-id="72769-117">Exemple</span><span class="sxs-lookup"><span data-stu-id="72769-117">Example</span></span>  
 <span data-ttu-id="72769-118">L'exemple de code suivant est l'exemple complet pour les étapes répertoriées précédemment.</span><span class="sxs-lookup"><span data-stu-id="72769-118">The following code example is the complete example for the steps listed previously.</span></span>  
  
 [!code-csharp[System.Windows.Forms.BindingNavigatorNavigate#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.BindingNavigatorNavigate/CS/Form1.cs#1)]
 [!code-vb[System.Windows.Forms.BindingNavigatorNavigate#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.BindingNavigatorNavigate/VB/Form1.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="72769-119">Compilation du code</span><span class="sxs-lookup"><span data-stu-id="72769-119">Compiling the Code</span></span>  
 <span data-ttu-id="72769-120">Cet exemple nécessite :</span><span class="sxs-lookup"><span data-stu-id="72769-120">This example requires:</span></span>  
  
-   <span data-ttu-id="72769-121">Références aux assemblys System, System.Data, System.Drawing, System.Windows.Forms et System.Xml.</span><span class="sxs-lookup"><span data-stu-id="72769-121">References to the System, System.Data, System.Drawing, System.Windows.Forms and System.Xml assemblies.</span></span>  
  
 <span data-ttu-id="72769-122">Pour plus d’informations sur la création de cet exemple à partir de la ligne de commande pour [!INCLUDE[vbprvb](../../../../includes/vbprvb-md.md)] ou [!INCLUDE[csprcs](../../../../includes/csprcs-md.md)], consultez [Génération à partir de la ligne de commande](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) ou [Génération à partir de la ligne de commande avec csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span><span class="sxs-lookup"><span data-stu-id="72769-122">For information about building this example from the command line for [!INCLUDE[vbprvb](../../../../includes/vbprvb-md.md)] or [!INCLUDE[csprcs](../../../../includes/csprcs-md.md)], see [Building from the Command Line](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) or [Command-line Building With csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span></span> <span data-ttu-id="72769-123">Vous pouvez également générer cet exemple dans [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)] en collant le code dans un nouveau projet.</span><span class="sxs-lookup"><span data-stu-id="72769-123">You can also build this example in [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)] by pasting the code into a new project.</span></span>  <span data-ttu-id="72769-124">Consultez également la page [Comment : compiler et exécuter un exemple complet de code Windows Forms à l’aide de Visual Studio](http://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).</span><span class="sxs-lookup"><span data-stu-id="72769-124">Also see [How to: Compile and Run a Complete Windows Forms Code Example Using Visual Studio](http://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="72769-125">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="72769-125">See Also</span></span>  
 <xref:System.Windows.Forms.BindingNavigator>  
 [<span data-ttu-id="72769-126">BindingNavigator, contrôle</span><span class="sxs-lookup"><span data-stu-id="72769-126">BindingNavigator Control</span></span>](../../../../docs/framework/winforms/controls/bindingnavigator-control-windows-forms.md)  
 [<span data-ttu-id="72769-127">Contrôle ToolStrip</span><span class="sxs-lookup"><span data-stu-id="72769-127">ToolStrip Control</span></span>](../../../../docs/framework/winforms/controls/toolstrip-control-windows-forms.md)
