---
title: "Comment : s’assurer que plusieurs contrôles liés à la même source de données restent synchronisés"
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
- controls [Windows Forms], binding multiple
- controls [Windows Forms], synchronizing with data source
ms.assetid: c2f0ecc6-11e6-4c2c-a1ca-0759630c451e
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 2573f342530e59fa05e7f24342f251990b2ce47d
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-ensure-multiple-controls-bound-to-the-same-data-source-remain-synchronized"></a><span data-ttu-id="230b2-102">Comment : s’assurer que plusieurs contrôles liés à la même source de données restent synchronisés</span><span class="sxs-lookup"><span data-stu-id="230b2-102">How to: Ensure Multiple Controls Bound to the Same Data Source Remain Synchronized</span></span>
<span data-ttu-id="230b2-103">Souvent, lorsque vous travaillez avec la liaison de données dans les Windows Forms, plusieurs contrôles sont liés à la même source de données.</span><span class="sxs-lookup"><span data-stu-id="230b2-103">Oftentimes when working with data binding in Windows Forms, multiple controls are bound to the same data source.</span></span> <span data-ttu-id="230b2-104">Dans certains cas, il peut être nécessaire de prendre des mesures supplémentaires pour garantir que les propriétés liées des contrôles restent synchronisées avec eux et à la source de données.</span><span class="sxs-lookup"><span data-stu-id="230b2-104">In some cases, it may be necessary to take extra steps to ensure that the bound properties of the controls remain synchronized with each other and the data source.</span></span> <span data-ttu-id="230b2-105">Ces étapes sont nécessaires dans deux situations :</span><span class="sxs-lookup"><span data-stu-id="230b2-105">These steps are necessary in two situations:</span></span>  
  
-   <span data-ttu-id="230b2-106">Si la source de données n’implémente pas <xref:System.ComponentModel.IBindingList>et ainsi générer <xref:System.ComponentModel.IBindingList.ListChanged> événements de type <xref:System.ComponentModel.ListChangedType.ItemChanged>.</span><span class="sxs-lookup"><span data-stu-id="230b2-106">If the data source does not implement <xref:System.ComponentModel.IBindingList>, and therefore generate <xref:System.ComponentModel.IBindingList.ListChanged> events of type <xref:System.ComponentModel.ListChangedType.ItemChanged>.</span></span>  
  
-   <span data-ttu-id="230b2-107">Si la source de données implémente <xref:System.ComponentModel.IEditableObject>.</span><span class="sxs-lookup"><span data-stu-id="230b2-107">If the data source implements <xref:System.ComponentModel.IEditableObject>.</span></span>  
  
 <span data-ttu-id="230b2-108">Dans le premier cas, vous pouvez utiliser un <xref:System.Windows.Forms.BindingSource> pour lier la source de données aux contrôles.</span><span class="sxs-lookup"><span data-stu-id="230b2-108">In the former case, you can use a <xref:System.Windows.Forms.BindingSource> to bind the data source to the controls.</span></span> <span data-ttu-id="230b2-109">Dans ce cas, vous utilisez un <xref:System.Windows.Forms.BindingSource> et gérer le <xref:System.Windows.Forms.BindingSource.BindingComplete> événements et les appels <xref:System.Windows.Forms.BindingManagerBase.EndCurrentEdit%2A> sur associé <xref:System.Windows.Forms.BindingManagerBase>.</span><span class="sxs-lookup"><span data-stu-id="230b2-109">In the latter case, you use a <xref:System.Windows.Forms.BindingSource> and handle the <xref:System.Windows.Forms.BindingSource.BindingComplete> event and call <xref:System.Windows.Forms.BindingManagerBase.EndCurrentEdit%2A> on the associated <xref:System.Windows.Forms.BindingManagerBase>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="230b2-110">Exemple</span><span class="sxs-lookup"><span data-stu-id="230b2-110">Example</span></span>  
 <span data-ttu-id="230b2-111">L’exemple de code suivant montre comment lier des contrôles de trois : deux contrôles de zone de texte et un <xref:System.Windows.Forms.DataGridView> contrôle, à la même colonne dans un <xref:System.Data.DataSet> à l’aide un <xref:System.Windows.Forms.BindingSource> composant.</span><span class="sxs-lookup"><span data-stu-id="230b2-111">The following code example demonstrates how to bind three controls—two text-box controls and a <xref:System.Windows.Forms.DataGridView> control—to the same column in a <xref:System.Data.DataSet> using a <xref:System.Windows.Forms.BindingSource> component.</span></span> <span data-ttu-id="230b2-112">Cet exemple montre comment gérer les <xref:System.Windows.Forms.BindingSource.BindingComplete> événements et vérifiez que, quand la valeur de texte d’une zone de texte est modifiée, la zone de texte supplémentaires et <xref:System.Windows.Forms.DataGridView> contrôle sont mis à jour avec la valeur correcte.</span><span class="sxs-lookup"><span data-stu-id="230b2-112">This example demonstrates how to handle the <xref:System.Windows.Forms.BindingSource.BindingComplete> event and ensure that when the text value of one text box is changed, the additional text box and the <xref:System.Windows.Forms.DataGridView> control are updated with the correct value.</span></span>  
  
 <span data-ttu-id="230b2-113">L’exemple utilise un <xref:System.Windows.Forms.BindingSource> pour lier la source de données et les contrôles.</span><span class="sxs-lookup"><span data-stu-id="230b2-113">The example uses a <xref:System.Windows.Forms.BindingSource> to bind the data source and the controls.</span></span> <span data-ttu-id="230b2-114">Ou bien, vous pouvez lier les contrôles directement à la source de données et récupérer le <xref:System.Windows.Forms.BindingManagerBase> pour la liaison à partir du formulaire <xref:System.Windows.Forms.Control.BindingContext%2A> , puis gérer la <xref:System.Windows.Forms.BindingManagerBase.BindingComplete> événement pour le <xref:System.Windows.Forms.BindingManagerBase>.</span><span class="sxs-lookup"><span data-stu-id="230b2-114">Alternatively, you can bind the controls directly to the data source and retrieve the <xref:System.Windows.Forms.BindingManagerBase> for the binding from the form's <xref:System.Windows.Forms.Control.BindingContext%2A> and then handle the <xref:System.Windows.Forms.BindingManagerBase.BindingComplete> event for the <xref:System.Windows.Forms.BindingManagerBase>.</span></span> <span data-ttu-id="230b2-115">Pour obtenir un exemple de procédure à suivre, consultez la page d’aide la <xref:System.Windows.Forms.BindingManagerBase.BindingComplete> l’événement de <xref:System.Windows.Forms.BindingManagerBase>.</span><span class="sxs-lookup"><span data-stu-id="230b2-115">For an example of how to do this, see the Help page about the <xref:System.Windows.Forms.BindingManagerBase.BindingComplete> event of <xref:System.Windows.Forms.BindingManagerBase>.</span></span>  
  
 [!code-csharp[System.Windows.Forms.BindingSourceMultipleControls#1](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.BindingSourceMultipleControls/CS/Form1.cs#1)]
 [!code-vb[System.Windows.Forms.BindingSourceMultipleControls#1](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.BindingSourceMultipleControls/VB/Form1.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="230b2-116">Compilation du code</span><span class="sxs-lookup"><span data-stu-id="230b2-116">Compiling the Code</span></span>  
  
-   <span data-ttu-id="230b2-117">Cet exemple de code nécessite</span><span class="sxs-lookup"><span data-stu-id="230b2-117">This code example requires</span></span>  
  
-   <span data-ttu-id="230b2-118">des références aux assemblys <xref:System>, <xref:System.Windows.Forms> et <xref:System.Drawing>.</span><span class="sxs-lookup"><span data-stu-id="230b2-118">References to the <xref:System>, <xref:System.Windows.Forms>, and <xref:System.Drawing> assemblies.</span></span>  
  
-   <span data-ttu-id="230b2-119">Un formulaire avec le <xref:System.Windows.Forms.Form.Load> événement géré et un appel à la `InitializeControlsAndDataSource` méthode dans l’exemple à partir du formulaire <xref:System.Windows.Forms.Form.Load> Gestionnaire d’événements.</span><span class="sxs-lookup"><span data-stu-id="230b2-119">A form with the <xref:System.Windows.Forms.Form.Load> event handled and a call to the `InitializeControlsAndDataSource` method in the example from the form's <xref:System.Windows.Forms.Form.Load> event handler.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="230b2-120">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="230b2-120">See Also</span></span>  
 [<span data-ttu-id="230b2-121">Comment : partager des données liées entre des formulaires à l'aide du composant BindingSource</span><span class="sxs-lookup"><span data-stu-id="230b2-121">How to: Share Bound Data Across Forms Using the BindingSource Component</span></span>](../../../docs/framework/winforms/controls/how-to-share-bound-data-across-forms-using-the-bindingsource-component.md)  
 [<span data-ttu-id="230b2-122">Notification de modifications dans la liaison de données Windows Forms</span><span class="sxs-lookup"><span data-stu-id="230b2-122">Change Notification in Windows Forms Data Binding</span></span>](../../../docs/framework/winforms/change-notification-in-windows-forms-data-binding.md)  
 [<span data-ttu-id="230b2-123">Interfaces participant à la liaison de données</span><span class="sxs-lookup"><span data-stu-id="230b2-123">Interfaces Related to Data Binding</span></span>](../../../docs/framework/winforms/interfaces-related-to-data-binding.md)  
 [<span data-ttu-id="230b2-124">Liaison de données Windows Forms</span><span class="sxs-lookup"><span data-stu-id="230b2-124">Windows Forms Data Binding</span></span>](../../../docs/framework/winforms/windows-forms-data-binding.md)
