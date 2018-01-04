---
title: "Comment : lier un contrôle Windows Forms à un type à l'aide du concepteur"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- controls [Windows Forms], binding to a type
- BindingSource component [Windows Forms], binding to a type
- types [Windows Forms], binding controls to
ms.assetid: 5ab984b5-c2d0-4638-a572-1c84013e8746
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: a25b0dc81a6511698394eb86343f09051befc87f
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-bind-a-windows-forms-control-to-a-type-using-the-designer"></a><span data-ttu-id="e63b8-102">Comment : lier un contrôle Windows Forms à un type à l'aide du concepteur</span><span class="sxs-lookup"><span data-stu-id="e63b8-102">How to: Bind a Windows Forms Control to a Type Using the Designer</span></span>
<span data-ttu-id="e63b8-103">Quand vous créez des contrôles qui interagissent avec des données, vous devez parfois lier un contrôle à un type plutôt qu’à un objet.</span><span class="sxs-lookup"><span data-stu-id="e63b8-103">When you are building controls that interact with data, you sometimes need to bind a control to a type, rather than an object.</span></span> <span data-ttu-id="e63b8-104">Cette situation se présente surtout au moment du design, quand les données peuvent ne pas être disponibles mais que vos contrôles liés aux données ont tout de même besoin d’afficher des informations à partir de l’interface publique d’un type.</span><span class="sxs-lookup"><span data-stu-id="e63b8-104">You typically need to bind a control to a type at design time, when data may not be available, but you still want your data-bound controls to display data from a type's public interface.</span></span> <span data-ttu-id="e63b8-105">Les procédures suivantes montrent comment créer un nouveau <xref:System.Windows.Forms.BindingSource> qui est liée à un type, puis comment lier une des propriétés du type pour le <xref:System.Windows.Forms.TextBox.Text%2A> propriété d’un <xref:System.Windows.Forms.TextBox>.</span><span class="sxs-lookup"><span data-stu-id="e63b8-105">The following procedures demonstrate how to create a new <xref:System.Windows.Forms.BindingSource> that is bound to a type, and then how to bind one of the type's properties to the <xref:System.Windows.Forms.TextBox.Text%2A> property of a <xref:System.Windows.Forms.TextBox>.</span></span>  
  
### <a name="to-bind-the-bindingsource-to-a-type"></a><span data-ttu-id="e63b8-106">Pour lier le BindingSource à un type</span><span class="sxs-lookup"><span data-stu-id="e63b8-106">To bind the BindingSource to a type</span></span>  
  
1.  <span data-ttu-id="e63b8-107">Créez un projet Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="e63b8-107">Create a Windows Forms project.</span></span>  
  
     <span data-ttu-id="e63b8-108">Pour plus d'informations, consultez [How to: Create a Windows Application Project](http://msdn.microsoft.com/en-us/b2f93fed-c635-4705-8d0e-cf079a264efa).</span><span class="sxs-lookup"><span data-stu-id="e63b8-108">For more information, see [How to: Create a Windows Application Project](http://msdn.microsoft.com/en-us/b2f93fed-c635-4705-8d0e-cf079a264efa).</span></span>  
  
2.  <span data-ttu-id="e63b8-109">Dans **conception** afficher, faites glisser un <xref:System.Windows.Forms.BindingSource> composant vers le formulaire.</span><span class="sxs-lookup"><span data-stu-id="e63b8-109">In **Design** view, drag a <xref:System.Windows.Forms.BindingSource> component onto the form.</span></span>  
  
3.  <span data-ttu-id="e63b8-110">Dans le **propriétés** fenêtre, cliquez sur la flèche pour la <xref:System.Windows.Forms.BindingSource.DataSource%2A> propriété.</span><span class="sxs-lookup"><span data-stu-id="e63b8-110">In the **Properties** window, click the arrow for the <xref:System.Windows.Forms.BindingSource.DataSource%2A> property.</span></span>  
  
4.  <span data-ttu-id="e63b8-111">Dans l’**éditeur de types d’interface utilisateur DataSource**, cliquez sur **Ajouter la source de données du projet**.</span><span class="sxs-lookup"><span data-stu-id="e63b8-111">In the **DataSource UI Type Editor**, click **Add Project Data Source**.</span></span>  
  
5.  <span data-ttu-id="e63b8-112">Sur la page **Choisir un type de source de données**, sélectionnez **Objet**, puis cliquez sur **Suivant**.</span><span class="sxs-lookup"><span data-stu-id="e63b8-112">On the **Choose a Data Source Type** page, select **Object** and click **Next**.</span></span>  
  
6.  <span data-ttu-id="e63b8-113">Sélectionnez le type à lier :</span><span class="sxs-lookup"><span data-stu-id="e63b8-113">Select the type to bind to:</span></span>  
  
    -   <span data-ttu-id="e63b8-114">Si le type avec lequel vous souhaitez établir une liaison se trouve dans le projet actuel, ou si l’assembly qui contient ce type est déjà ajouté en tant que référence, développez les nœuds pour rechercher le type souhaité et sélectionnez-le.</span><span class="sxs-lookup"><span data-stu-id="e63b8-114">If the type you want to bind to is in the current project, or the assembly that contains the type is already added as a reference, expand the nodes to find the type you want, and then select it.</span></span>  
  
         <span data-ttu-id="e63b8-115">- ou -</span><span class="sxs-lookup"><span data-stu-id="e63b8-115">-or-</span></span>  
  
    -   <span data-ttu-id="e63b8-116">Si le type avec lequel vous souhaitez établir une liaison se trouve actuellement dans un autre assembly, et non dans la liste de références, cliquez sur **Ajouter une référence**, puis cliquez sur l’onglet **Projets**. Sélectionnez le projet contenant l’objet métier de votre choix, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="e63b8-116">If the type you want to bind to is in another assembly, not currently in the list of references, click **Add Reference**, and then click the **Projects** tab. Select the project that contains the business object you want and click **OK**.</span></span> <span data-ttu-id="e63b8-117">Ce projet apparaît dans la liste des assemblys. Vous pouvez donc développer les nœuds pour rechercher le type que vous souhaitez, puis le sélectionner.</span><span class="sxs-lookup"><span data-stu-id="e63b8-117">This project will appear in the list of assemblies, so you can expand the nodes to find the type you want, and then select it.</span></span>  
  
        > [!NOTE]
        >  <span data-ttu-id="e63b8-118">Pour effectuer une liaison avec un type présent dans une infrastructure ou un assembly Microsoft, décochez la case **Masquer les assemblys qui commencent par Microsoft ou System**.</span><span class="sxs-lookup"><span data-stu-id="e63b8-118">If you want to bind to a type in a framework or Microsoft assembly, clear the **Hide assemblies that begin with Microsoft or System** check box.</span></span>  
  
7.  <span data-ttu-id="e63b8-119">Cliquez sur **Suivant**, puis sur **Terminer**.</span><span class="sxs-lookup"><span data-stu-id="e63b8-119">Click **Next**, and then click **Finish**.</span></span>  
  
### <a name="to-bind-the-control-to-the-bindingsource"></a><span data-ttu-id="e63b8-120">Pour lier le contrôle au BindingSource</span><span class="sxs-lookup"><span data-stu-id="e63b8-120">To bind the control to the BindingSource</span></span>  
  
1.  <span data-ttu-id="e63b8-121">Ajoutez un <xref:System.Windows.Forms.TextBox> au formulaire.</span><span class="sxs-lookup"><span data-stu-id="e63b8-121">Add a <xref:System.Windows.Forms.TextBox> to the form.</span></span>  
  
2.  <span data-ttu-id="e63b8-122">Dans la fenêtre **Propriétés**, développez le nœud **(DataBindings)**.</span><span class="sxs-lookup"><span data-stu-id="e63b8-122">In the **Properties** window, expand the **(DataBindings)** node.</span></span>  
  
3.  <span data-ttu-id="e63b8-123">Cliquez sur la flèche en regard du <xref:System.Windows.Forms.TextBox.Text%2A> propriété.</span><span class="sxs-lookup"><span data-stu-id="e63b8-123">Click the arrow next to the <xref:System.Windows.Forms.TextBox.Text%2A> property.</span></span>  
  
4.  <span data-ttu-id="e63b8-124">Dans le **éditeur de Type de source de données de l’interface utilisateur**, développez le nœud pour le <xref:System.Windows.Forms.BindingSource> précédemment ajoutée et sélectionnez la propriété du type dépendant que vous souhaitez lier à la <xref:System.Windows.Forms.TextBox.Text%2A> propriété de la <xref:System.Windows.Forms.TextBox>.</span><span class="sxs-lookup"><span data-stu-id="e63b8-124">In the **DataSource UI Type Editor**, expand the node for the <xref:System.Windows.Forms.BindingSource> added previously, and select the property of the bound type you want to bind to the <xref:System.Windows.Forms.TextBox.Text%2A> property of the <xref:System.Windows.Forms.TextBox>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e63b8-125">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e63b8-125">See Also</span></span>  
 [<span data-ttu-id="e63b8-126">BindingSource, composant</span><span class="sxs-lookup"><span data-stu-id="e63b8-126">BindingSource Component</span></span>](../../../../docs/framework/winforms/controls/bindingsource-component.md)  
 [<span data-ttu-id="e63b8-127">Comment : lier un contrôle Windows Forms à un type</span><span class="sxs-lookup"><span data-stu-id="e63b8-127">How to: Bind a Windows Forms Control to a Type</span></span>](../../../../docs/framework/winforms/controls/how-to-bind-a-windows-forms-control-to-a-type.md)  
 [<span data-ttu-id="e63b8-128">Lier des contrôles à des données dans Visual Studio</span><span class="sxs-lookup"><span data-stu-id="e63b8-128">Bind controls to data in Visual Studio</span></span>](/visualstudio/data-tools/bind-controls-to-data-in-visual-studio)
