---
title: "Comment : définir le masque de saisie"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: net.ComponentModel.MaskPropertyEditor
helpviewer_keywords: MaskedTextBox control [Windows Forms]
ms.assetid: 779b3a12-cd74-4e58-b46e-04983bda5b2c
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: c136bd5bdacec04a011f728694550fb66ae6d897
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="how-to-set-the-input-mask"></a><span data-ttu-id="c7c5e-102">Comment : définir le masque de saisie</span><span class="sxs-lookup"><span data-stu-id="c7c5e-102">How to: Set the Input Mask</span></span>
<span data-ttu-id="c7c5e-103">Le contrôle de zone de texte masquée est un contrôle de zone de texte amélioré qui prend en charge une syntaxe déclarative pour accepter ou rejeter l’entrée d’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="c7c5e-103">The masked text box control is an enhanced text box control that supports a declarative syntax for accepting or rejecting user input.</span></span> <span data-ttu-id="c7c5e-104">En définissant la propriété du masque, vous pouvez spécifier l’entrée d’utilisateur autorisée sans écrire une logique de validation personnalisée dans votre application.</span><span class="sxs-lookup"><span data-stu-id="c7c5e-104">By setting the Mask property, you can specify the allowable user input without writing any custom validation logic in your application.</span></span> <span data-ttu-id="c7c5e-105">Pour plus d’informations, consultez la section Notes de la <xref:System.Windows.Forms.MaskedTextBox> classe.</span><span class="sxs-lookup"><span data-stu-id="c7c5e-105">For more information, see the Remarks section of the <xref:System.Windows.Forms.MaskedTextBox> class.</span></span>  
  
## <a name="setting-the-mask-property-manually"></a><span data-ttu-id="c7c5e-106">Définir la propriété masque manuellement</span><span class="sxs-lookup"><span data-stu-id="c7c5e-106">Setting the Mask Property Manually</span></span>  
 <span data-ttu-id="c7c5e-107">Si vous êtes familiarisé avec les caractères qui prend en charge de la propriété du masque, vous pouvez l’entrer manuellement.</span><span class="sxs-lookup"><span data-stu-id="c7c5e-107">If you are familiar with the characters that the Mask property supports, you can enter it manually.</span></span> <span data-ttu-id="c7c5e-108">Pour obtenir un résumé des caractères que la propriété Masque prend en charge, consultez la section Notes de la <xref:System.Windows.Forms.MaskedTextBox.Mask%2A> propriété.</span><span class="sxs-lookup"><span data-stu-id="c7c5e-108">For a summary of the characters that the Mask property supports, see the Remarks section of the <xref:System.Windows.Forms.MaskedTextBox.Mask%2A> property.</span></span>  
  
#### <a name="to-set-the-mask-property-manually"></a><span data-ttu-id="c7c5e-109">Pour définir la propriété masque manuellement</span><span class="sxs-lookup"><span data-stu-id="c7c5e-109">To set the Mask property manually</span></span>  
  
1.  <span data-ttu-id="c7c5e-110">Dans **conception** afficher, sélectionnez un <xref:System.Windows.Forms.MaskedTextBox>.</span><span class="sxs-lookup"><span data-stu-id="c7c5e-110">In **Design** view, select a <xref:System.Windows.Forms.MaskedTextBox>.</span></span>  
  
2.  <span data-ttu-id="c7c5e-111">Dans le **propriétés** fenêtre, recherchez le <xref:System.Windows.Forms.MaskedTextBox.Mask%2A> propriété.</span><span class="sxs-lookup"><span data-stu-id="c7c5e-111">In the **Properties** window, locate the <xref:System.Windows.Forms.MaskedTextBox.Mask%2A> property.</span></span>  
  
3.  <span data-ttu-id="c7c5e-112">Tapez le masque que vous souhaitez.</span><span class="sxs-lookup"><span data-stu-id="c7c5e-112">Type the mask that you want.</span></span> <span data-ttu-id="c7c5e-113">Par exemple, tapez `###`.</span><span class="sxs-lookup"><span data-stu-id="c7c5e-113">For example, type `###`.</span></span>  
  
## <a name="using-the-input-mask-dialog-box"></a><span data-ttu-id="c7c5e-114">À l’aide de la boîte de dialogue masque de saisie</span><span class="sxs-lookup"><span data-stu-id="c7c5e-114">Using the Input Mask Dialog Box</span></span>  
 <span data-ttu-id="c7c5e-115">La boîte de dialogue masque de saisie fournit des masques d’entrée prédéfinis.</span><span class="sxs-lookup"><span data-stu-id="c7c5e-115">The Input Mask dialog box provides some predefined input masks.</span></span> <span data-ttu-id="c7c5e-116">Vous pouvez également modifier les masques prédéfinis ou entrer votre propre masque manuellement.</span><span class="sxs-lookup"><span data-stu-id="c7c5e-116">You can also change the predefined masks or enter your own mask manually.</span></span>  
  
#### <a name="to-open-the-input-mask-dialog-box"></a><span data-ttu-id="c7c5e-117">Pour ouvrir la boîte de dialogue masque de saisie</span><span class="sxs-lookup"><span data-stu-id="c7c5e-117">To open the Input Mask dialog box</span></span>  
  
1.  <span data-ttu-id="c7c5e-118">Dans **conception** afficher, sélectionnez un <xref:System.Windows.Forms.MaskedTextBox>.</span><span class="sxs-lookup"><span data-stu-id="c7c5e-118">In **Design** view, select a <xref:System.Windows.Forms.MaskedTextBox>.</span></span>  
  
    1.  <span data-ttu-id="c7c5e-119">Cliquez sur la balise active pour ouvrir le **tâches MaskedTextBox** Panneau de configuration.</span><span class="sxs-lookup"><span data-stu-id="c7c5e-119">Click the smart tag to open the **MaskedTextBox Tasks** panel.</span></span>  
  
    2.  <span data-ttu-id="c7c5e-120">Cliquez sur **définir le masque**.</span><span class="sxs-lookup"><span data-stu-id="c7c5e-120">Click **Set Mask**.</span></span>  
  
     <span data-ttu-id="c7c5e-121">\- ou -</span><span class="sxs-lookup"><span data-stu-id="c7c5e-121">\- or -</span></span>  
  
    1.  <span data-ttu-id="c7c5e-122">Dans le **propriétés** fenêtre, sélectionnez le <xref:System.Windows.Forms.MaskedTextBox.Mask%2A> propriété.</span><span class="sxs-lookup"><span data-stu-id="c7c5e-122">In the **Properties** window, select the <xref:System.Windows.Forms.MaskedTextBox.Mask%2A> property.</span></span>  
  
    2.  <span data-ttu-id="c7c5e-123">Cliquez sur le bouton de sélection dans la colonne de valeur de propriété.</span><span class="sxs-lookup"><span data-stu-id="c7c5e-123">Click the ellipsis button in the property value column.</span></span>  
  
     <span data-ttu-id="c7c5e-124">Le **masque de saisie** boîte de dialogue s’affiche.</span><span class="sxs-lookup"><span data-stu-id="c7c5e-124">The **Input Mask** dialog box appears.</span></span>  
  
#### <a name="to-use-the-input-mask-dialog-box"></a><span data-ttu-id="c7c5e-125">Pour utiliser la boîte de dialogue masque de saisie</span><span class="sxs-lookup"><span data-stu-id="c7c5e-125">To use the Input Mask dialog box</span></span>  
  
1.  <span data-ttu-id="c7c5e-126">(Facultatif) Cliquez sur un des masques prédéfinis dans la liste.</span><span class="sxs-lookup"><span data-stu-id="c7c5e-126">(Optional) Click one of the predefined masks in the list.</span></span>  
  
2.  <span data-ttu-id="c7c5e-127">(Facultatif) Modifiez le masque prédéfini dans le **masque** boîte.</span><span class="sxs-lookup"><span data-stu-id="c7c5e-127">(Optional) Edit the predefined mask in the **Mask** box.</span></span>  
  
3.  <span data-ttu-id="c7c5e-128">(Facultatif) Tapez un nouveau masque dans le **masque** boîte.</span><span class="sxs-lookup"><span data-stu-id="c7c5e-128">(Optional) Type a new mask in the **Mask** box.</span></span> <span data-ttu-id="c7c5e-129">Autrement dit, il est inutile d’utiliser un des masques prédéfinis.</span><span class="sxs-lookup"><span data-stu-id="c7c5e-129">That is, you do not have to use one of the predefined masks.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="c7c5e-130">La zone Aperçu affiche les caractères que l’utilisateur voit dans le <xref:System.Windows.Forms.MaskedTextBox>.</span><span class="sxs-lookup"><span data-stu-id="c7c5e-130">The Preview box displays the characters that the user sees in the <xref:System.Windows.Forms.MaskedTextBox>.</span></span> <span data-ttu-id="c7c5e-131">Ces caractères sont un guide pour aider l’utilisateur à entrer les données correctement.</span><span class="sxs-lookup"><span data-stu-id="c7c5e-131">These characters are a guide to help the user enter the data correctly.</span></span>  
  
4.  <span data-ttu-id="c7c5e-132">Activez ou désactivez le **Utiliser ValidatingType** case à cocher.</span><span class="sxs-lookup"><span data-stu-id="c7c5e-132">Select or clear the **Use ValidatingType** check box.</span></span> <span data-ttu-id="c7c5e-133">Le **Utiliser ValidatingType** case à cocher spécifie si un type de données est utilisé pour vérifier les données entrées par l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="c7c5e-133">The **Use ValidatingType** check box specifies whether a data type is used to verify the data input by the user.</span></span> <span data-ttu-id="c7c5e-134">Pour plus d'informations, consultez la propriété <xref:System.Windows.Forms.MaskedTextBox.ValidatingType%2A>.</span><span class="sxs-lookup"><span data-stu-id="c7c5e-134">For more information, see the <xref:System.Windows.Forms.MaskedTextBox.ValidatingType%2A> property.</span></span>  
  
5.  <span data-ttu-id="c7c5e-135">Cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="c7c5e-135">Click **OK**.</span></span>  
  
     <span data-ttu-id="c7c5e-136">Le masque est entré dans le **masque** propriété dans le **propriétés** fenêtre.</span><span class="sxs-lookup"><span data-stu-id="c7c5e-136">The mask is entered in the **Mask** property in the **Properties** window.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c7c5e-137">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="c7c5e-137">See Also</span></span>  
 [<span data-ttu-id="c7c5e-138">Procédure pas à pas : utilisation du contrôle MaskedTextBox</span><span class="sxs-lookup"><span data-stu-id="c7c5e-138">Walkthrough: Working with the MaskedTextBox Control</span></span>](../../../../docs/framework/winforms/controls/walkthrough-working-with-the-maskedtextbox-control.md)
