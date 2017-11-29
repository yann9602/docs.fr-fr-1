---
title: "Meilleures pratiques pour le contrôle TableLayoutPanel"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- layout [Windows Forms]
- TableLayoutPanel control [Windows Forms], best practices
- forms [Windows Forms], best practices
- AutoSize property [Windows Forms], tableLayoutPanel control
- controls [Windows Forms], sizing
- TableLayoutPanel control [Windows Forms], AutoSize behavior
- layout [Windows Forms], AutoSize
- layout [Windows Forms], best practices
- best practices [Windows Forms], tableLayoutPanel control
- sizing [Windows Forms], automatic
- automatic sizing
ms.assetid: b6706efb-d7a4-45ec-8cf4-08fa993e3afb
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 802cc501b695f6c5cfe990bf72a4d9d2af68ba2b
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="best-practices-for-the-tablelayoutpanel-control"></a><span data-ttu-id="91c23-102">Meilleures pratiques pour le contrôle TableLayoutPanel</span><span class="sxs-lookup"><span data-stu-id="91c23-102">Best Practices for the TableLayoutPanel Control</span></span>
<span data-ttu-id="91c23-103">Le <xref:System.Windows.Forms.TableLayoutPanel> contrôle fournit des fonctionnalités de disposition puissantes que vous devez examiner soigneusement avant à l’aide de vos Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="91c23-103">The <xref:System.Windows.Forms.TableLayoutPanel> control provides powerful layout features that you should consider carefully before using on your Windows Forms.</span></span>  
  
## <a name="recommendations"></a><span data-ttu-id="91c23-104">Recommandations</span><span class="sxs-lookup"><span data-stu-id="91c23-104">Recommendations</span></span>  
 <span data-ttu-id="91c23-105">Les recommandations suivantes vous aideront à utiliser le <xref:System.Windows.Forms.TableLayoutPanel> contrôle mieux.</span><span class="sxs-lookup"><span data-stu-id="91c23-105">The following recommendations will help you use the <xref:System.Windows.Forms.TableLayoutPanel> control to its best advantage.</span></span>  
  
### <a name="targeted-use"></a><span data-ttu-id="91c23-106">Utilisez ciblé</span><span class="sxs-lookup"><span data-stu-id="91c23-106">Targeted Use</span></span>  
 <span data-ttu-id="91c23-107">Utilisez le <xref:System.Windows.Forms.TableLayoutPanel> contrôler avec parcimonie.</span><span class="sxs-lookup"><span data-stu-id="91c23-107">Use the <xref:System.Windows.Forms.TableLayoutPanel> control sparingly.</span></span> <span data-ttu-id="91c23-108">Vous ne devez pas l’utiliser dans toutes les situations qui requièrent une disposition redimensionnable.</span><span class="sxs-lookup"><span data-stu-id="91c23-108">You should not use it in all situations that require a resizable layout.</span></span> <span data-ttu-id="91c23-109">La liste suivante décrit les dispositions qui bénéficient le plus de l’utilisation de la <xref:System.Windows.Forms.TableLayoutPanel> contrôle :</span><span class="sxs-lookup"><span data-stu-id="91c23-109">The following list describes layouts that benefit most from the use of the <xref:System.Windows.Forms.TableLayoutPanel> control:</span></span>  
  
-   <span data-ttu-id="91c23-110">Mises en page dans laquelle il existe plusieurs parties du formulaire, redimensionnement proportionnellement les uns aux autres.</span><span class="sxs-lookup"><span data-stu-id="91c23-110">Layouts in which there are multiple parts of the form that resize proportionally to each other.</span></span>  
  
-   <span data-ttu-id="91c23-111">Les dispositions qui seront modifiées ou générées dynamiquement au moment de l’exécution, telles que des formulaires de saisie de données qui ont des champs personnalisables par l’utilisateur ajoutée ou soustraite en fonction des préférences.</span><span class="sxs-lookup"><span data-stu-id="91c23-111">Layouts that will be modified or generated dynamically at run time, such as data entry forms that have user-customizable fields added or subtracted based on preferences.</span></span>  
  
-   <span data-ttu-id="91c23-112">Dispositions qui doivent rester à une taille fixe totale.</span><span class="sxs-lookup"><span data-stu-id="91c23-112">Layouts that should remain at an overall fixed size.</span></span> <span data-ttu-id="91c23-113">Par exemple, vous avez peut-être une boîte de dialogue qui doit rester inférieure à 800 x 600, mais vous devez prendre en charge les chaînes localisées.</span><span class="sxs-lookup"><span data-stu-id="91c23-113">For example, you may have a dialog box that should remain smaller than 800 x 600, but you need to support localized strings.</span></span>  
  
 <span data-ttu-id="91c23-114">La liste suivante décrit les dispositions qui ne bénéficient pas beaucoup d’à l’aide de la <xref:System.Windows.Forms.TableLayoutPanel> contrôle :</span><span class="sxs-lookup"><span data-stu-id="91c23-114">The following list describes layouts that do not benefit greatly from using the <xref:System.Windows.Forms.TableLayoutPanel> control:</span></span>  
  
-   <span data-ttu-id="91c23-115">Formulaires de saisie des données simple avec une seule colonne d’étiquettes et une seule colonne de zones de saisie de texte.</span><span class="sxs-lookup"><span data-stu-id="91c23-115">Simple data entry forms with a single column of labels and a single column of text-entry areas.</span></span>  
  
-   <span data-ttu-id="91c23-116">Formulaires avec une seule grande zone d’affichage qui doit remplir tout l’espace disponible lorsqu’un redimensionnement se produit.</span><span class="sxs-lookup"><span data-stu-id="91c23-116">Forms with a single large display area that should fill all the available space when a resize occurs.</span></span> <span data-ttu-id="91c23-117">Un exemple est un formulaire qui affiche un seul <xref:System.Windows.Forms.PropertyGrid> contrôle.</span><span class="sxs-lookup"><span data-stu-id="91c23-117">An example of this is a form that displays a single <xref:System.Windows.Forms.PropertyGrid> control.</span></span> <span data-ttu-id="91c23-118">Dans ce cas, utilisez l’ancrage, étant donné que rien d’autre ne doit se développer lorsque le formulaire est redimensionné.</span><span class="sxs-lookup"><span data-stu-id="91c23-118">In this case, use anchoring, because nothing else should expand when the form is resized.</span></span>  
  
 <span data-ttu-id="91c23-119">Choisissez avec soin les contrôles qui doivent se trouver dans un <xref:System.Windows.Forms.TableLayoutPanel> contrôle.</span><span class="sxs-lookup"><span data-stu-id="91c23-119">Choose carefully which controls need to be in a <xref:System.Windows.Forms.TableLayoutPanel> control.</span></span> <span data-ttu-id="91c23-120">Si vous disposez d’espace pour votre texte augmente de 30 % à l’aide d’ancrage, envisagez d’utiliser le <xref:System.Windows.Forms.Control.Anchor%2A> propriété uniquement.</span><span class="sxs-lookup"><span data-stu-id="91c23-120">If you have room for your text to grow by 30% using anchoring, consider using the <xref:System.Windows.Forms.Control.Anchor%2A> property only.</span></span> <span data-ttu-id="91c23-121">Si vous pouvez estimer l’espace requis par votre disposition, l’utilisation du <xref:System.Windows.Forms.Control.Dock%2A> et <xref:System.Windows.Forms.Control.Anchor%2A> est plus facile que d’estimer les détails de l’espace restant et <xref:System.Windows.Forms.Control.AutoSize%2A> comportement.</span><span class="sxs-lookup"><span data-stu-id="91c23-121">If you can estimate the space required by your layout, use of <xref:System.Windows.Forms.Control.Dock%2A> and <xref:System.Windows.Forms.Control.Anchor%2A> is easier than estimating the details of remaining space and <xref:System.Windows.Forms.Control.AutoSize%2A> behavior.</span></span>  
  
 <span data-ttu-id="91c23-122">En général, lorsque vous concevez votre disposition avec la <xref:System.Windows.Forms.TableLayoutPanel> contrôler, de simplifier la conception.</span><span class="sxs-lookup"><span data-stu-id="91c23-122">In general, when designing your layout with the <xref:System.Windows.Forms.TableLayoutPanel> control, keep the design as simple as possible.</span></span>  
  
### <a name="use-the-document-outline-window"></a><span data-ttu-id="91c23-123">Utilisez la fenêtre Structure du Document</span><span class="sxs-lookup"><span data-stu-id="91c23-123">Use the Document Outline Window</span></span>  
 <span data-ttu-id="91c23-124">La fenêtre Structure du Document vous donne une vue d’arborescence de votre disposition, vous pouvez utiliser pour manipuler les relations parent-enfant et de z de vos contrôles.</span><span class="sxs-lookup"><span data-stu-id="91c23-124">The Document Outline window gives you a tree view of your layout, which you can use to manipulate the z-order and parent-child relationships of your controls.</span></span> <span data-ttu-id="91c23-125">À partir de la **menu Affichage**, sélectionnez **autres fenêtres**, puis sélectionnez **structure du Document**.</span><span class="sxs-lookup"><span data-stu-id="91c23-125">From the **View menu**, select **Other Windows**, then select **Document Outline**.</span></span>  
  
### <a name="avoid-nesting"></a><span data-ttu-id="91c23-126">Évitez l’imbrication</span><span class="sxs-lookup"><span data-stu-id="91c23-126">Avoid Nesting</span></span>  
 <span data-ttu-id="91c23-127">Évitez d’imbriquer d’autres <xref:System.Windows.Forms.TableLayoutPanel> des contrôles dans un <xref:System.Windows.Forms.TableLayoutPanel> contrôle.</span><span class="sxs-lookup"><span data-stu-id="91c23-127">Avoid nesting other <xref:System.Windows.Forms.TableLayoutPanel> controls within a <xref:System.Windows.Forms.TableLayoutPanel> control.</span></span> <span data-ttu-id="91c23-128">Débogage des dispositions imbriquées peut être difficile.</span><span class="sxs-lookup"><span data-stu-id="91c23-128">Debugging nested layouts can be difficult.</span></span>  
  
### <a name="avoid-visual-inheritance"></a><span data-ttu-id="91c23-129">Évitez l’héritage visuel</span><span class="sxs-lookup"><span data-stu-id="91c23-129">Avoid Visual Inheritance</span></span>  
 <span data-ttu-id="91c23-130">Le <xref:System.Windows.Forms.TableLayoutPanel> contrôle ne prend pas en charge l’héritage visuel dans le Concepteur Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="91c23-130">The <xref:System.Windows.Forms.TableLayoutPanel> control does not support visual inheritance in the Windows Forms Designer.</span></span> <span data-ttu-id="91c23-131">A <xref:System.Windows.Forms.TableLayoutPanel> contrôle dans une classe dérivée apparaît comme « verrouillé » au moment du design.</span><span class="sxs-lookup"><span data-stu-id="91c23-131">A <xref:System.Windows.Forms.TableLayoutPanel> control in a derived class appears as "locked" at design time.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="91c23-132">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="91c23-132">See Also</span></span>  
 <xref:System.Windows.Forms.TableLayoutPanel>  
 <xref:System.Windows.Forms.FlowLayoutPanel>
