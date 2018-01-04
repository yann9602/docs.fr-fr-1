---
title: "Intégration de l'aide d'utilisateur dans les Windows Forms"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Help [Windows Forms], Windows Forms (using designer)
- Windows Forms, Help (using designer)
- HTML Help [Windows Forms], Windows Forms (using designer)
- Help [Windows Forms], Windows applications (using designer)
- forms. Help (using designer)
- Windows applications [Windows Forms], Help (using designer)
ms.assetid: a8563d25-8a75-4bc7-a024-f1870591b50f
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 9563ce0ca95a728cc1a9aaa219fbc9fea2cd7153
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="integrating-user-help-in-windows-forms"></a><span data-ttu-id="099b4-102">Intégration de l'aide d'utilisateur dans les Windows Forms</span><span class="sxs-lookup"><span data-stu-id="099b4-102">Integrating User Help in Windows Forms</span></span>
<span data-ttu-id="099b4-103">Un aspect essentiel mais souvent négligé, de créer des applications Windows est le système d’aide, car il s’agit où les utilisateurs ont activé pour vous aider à la fois de confusion.</span><span class="sxs-lookup"><span data-stu-id="099b4-103">An essential, but often overlooked, aspect of building Windows-based applications is the Help system, as this is where users turn for assistance in times of confusion.</span></span> <span data-ttu-id="099b4-104">Windows Forms prend en charge deux types différents d’aide, fourni par le [HelpProvider, composant](../../../../docs/framework/winforms/controls/helpprovider-component-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="099b4-104">Windows Forms support two different types of Help, each provided by the [HelpProvider Component](../../../../docs/framework/winforms/controls/helpprovider-component-windows-forms.md).</span></span> <span data-ttu-id="099b4-105">Le premier consiste à pointer vers un fichier d’aide de code HTML ou HTML Help 1 le. *x* format ou ultérieur.</span><span class="sxs-lookup"><span data-stu-id="099b4-105">The first involves pointing the user to a Help file of either HTML or HTML Help 1.*x* or greater format.</span></span> <span data-ttu-id="099b4-106">La seconde peut afficher brièvement « Qu’est-ce »-tapez Help sur chacun des contrôles. Ceci est particulièrement utile sur les boîtes de dialogue.</span><span class="sxs-lookup"><span data-stu-id="099b4-106">The second can display brief "What's This"-type Help on individual controls; this is especially useful on dialog boxes.</span></span> <span data-ttu-id="099b4-107">Les deux types d’aide peuvent être utilisés sur le même formulaire.</span><span class="sxs-lookup"><span data-stu-id="099b4-107">Both types of Help can be used on the same form.</span></span>  
  
 <span data-ttu-id="099b4-108">En outre, le [composant ToolTip](../../../../docs/framework/winforms/controls/tooltip-component-windows-forms.md) peut être utilisé pour fournir une aide individuelle pour les contrôles dans les Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="099b4-108">Additionally, the [ToolTip Component](../../../../docs/framework/winforms/controls/tooltip-component-windows-forms.md) can be used to provide individual Help for controls on Windows Forms.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="099b4-109">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="099b4-109">In This Section</span></span>  
 [<span data-ttu-id="099b4-110">Guide pratique pour fournir de l'aide dans une application Windows</span><span class="sxs-lookup"><span data-stu-id="099b4-110">How to: Provide Help in a Windows Application</span></span>](../../../../docs/framework/winforms/advanced/how-to-provide-help-in-a-windows-application.md)  
 <span data-ttu-id="099b4-111">Explique comment utiliser le `HelpProvider` composant à lier des contrôles à des fichiers dans un système d’aide.</span><span class="sxs-lookup"><span data-stu-id="099b4-111">Explains how to use the `HelpProvider` component to link controls to files in a Help system.</span></span>  
  
 [<span data-ttu-id="099b4-112">Guide pratique pour afficher l’aide contextuelle</span><span class="sxs-lookup"><span data-stu-id="099b4-112">How to: Display Pop-up Help</span></span>](../../../../docs/framework/winforms/advanced/how-to-display-pop-up-help.md)  
 <span data-ttu-id="099b4-113">Explique comment utiliser le `HelpProvider` composant pour afficher l’aide contextuelle dans les Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="099b4-113">Explains how to use the `HelpProvider` component to show pop-up Help on Windows Forms.</span></span>  
  
 [<span data-ttu-id="099b4-114">Affichage sous forme d’info-bulles de l’aide relative aux contrôles</span><span class="sxs-lookup"><span data-stu-id="099b4-114">Control Help Using ToolTips</span></span>](../../../../docs/framework/winforms/advanced/control-help-using-tooltips.md)  
 <span data-ttu-id="099b4-115">Décrit l’utilisation de la `ToolTip` composant pour afficher l’aide spécifique du contrôle.</span><span class="sxs-lookup"><span data-stu-id="099b4-115">Describes using the `ToolTip` component to show control-specific Help.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="099b4-116">Rubriques connexes</span><span class="sxs-lookup"><span data-stu-id="099b4-116">Related Sections</span></span>  
 [<span data-ttu-id="099b4-117">HelpProvider, composant</span><span class="sxs-lookup"><span data-stu-id="099b4-117">HelpProvider Component</span></span>](../../../../docs/framework/winforms/controls/helpprovider-component-windows-forms.md)  
 <span data-ttu-id="099b4-118">Explique les principes fondamentaux de la `HelpProvider` composant.</span><span class="sxs-lookup"><span data-stu-id="099b4-118">Explains the basics of the `HelpProvider` component.</span></span>  
  
 [<span data-ttu-id="099b4-119">ToolTip, composant</span><span class="sxs-lookup"><span data-stu-id="099b4-119">ToolTip Component</span></span>](../../../../docs/framework/winforms/controls/tooltip-component-windows-forms.md)  
 <span data-ttu-id="099b4-120">Explique les principes fondamentaux de la `ToolTip` composant.</span><span class="sxs-lookup"><span data-stu-id="099b4-120">Explains the basics of the `ToolTip` component.</span></span>  
  
 [<span data-ttu-id="099b4-121">Vue d'ensemble des Windows Forms</span><span class="sxs-lookup"><span data-stu-id="099b4-121">Windows Forms Overview</span></span>](../../../../docs/framework/winforms/windows-forms-overview.md)  
 <span data-ttu-id="099b4-122">Explique les notions de base des Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="099b4-122">Explains the basics of Windows Forms.</span></span>  
  
 [<span data-ttu-id="099b4-123">Windows Forms</span><span class="sxs-lookup"><span data-stu-id="099b4-123">Windows Forms</span></span>](../../../../docs/framework/winforms/index.md)  
 <span data-ttu-id="099b4-124">Fournit une vue d’ensemble des Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="099b4-124">Provides an overview of Windows Forms.</span></span>
