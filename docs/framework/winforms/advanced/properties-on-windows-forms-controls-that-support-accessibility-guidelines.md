---
title: "Propriétés des contrôles Windows Forms que prennent en charge les instructions relatives à l'accessibilité"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Windows Forms, accessibility properties of controls
- accessibility [Windows Forms], Windows Forms control properties
ms.assetid: ad3567a6-313b-4708-9e15-f487a831f049
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 967b4a0e883338c756aceef37d11edecfb978527
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="properties-on-windows-forms-controls-that-support-accessibility-guidelines"></a><span data-ttu-id="edd78-102">Propriétés des contrôles Windows Forms que prennent en charge les instructions relatives à l'accessibilité</span><span class="sxs-lookup"><span data-stu-id="edd78-102">Properties on Windows Forms Controls That Support Accessibility Guidelines</span></span>
<span data-ttu-id="edd78-103">Dans la boîte à outils standard pour les Windows Forms prennent en charge plusieurs règles d’accessibilité, y compris l’exposition du focus clavier et d’exposer les éléments de l’écran.</span><span class="sxs-lookup"><span data-stu-id="edd78-103">Controls on the standard toolbox for Windows Forms support many of the accessibility guidelines, including exposing the keyboard focus and exposing the screen elements.</span></span>  
  
## <a name="planning-ahead-for-accessibility"></a><span data-ttu-id="edd78-104">Planification de l’accessibilité</span><span class="sxs-lookup"><span data-stu-id="edd78-104">Planning Ahead for Accessibility</span></span>  
 <span data-ttu-id="edd78-105">Les propriétés des contrôles peuvent être utilisées pour prendre en charge d’autres règles d’accessibilité comme indiqué dans le tableau suivant.</span><span class="sxs-lookup"><span data-stu-id="edd78-105">The controls' properties can be used to support other accessibility guidelines as shown in the following table.</span></span> <span data-ttu-id="edd78-106">En outre, vous devez utiliser des menus pour accéder aux fonctionnalités du programme.</span><span class="sxs-lookup"><span data-stu-id="edd78-106">Additionally, you should use menus to provide access to program features.</span></span>  
  
|<span data-ttu-id="edd78-107">Propriété de contrôle</span><span class="sxs-lookup"><span data-stu-id="edd78-107">Control Property</span></span>|<span data-ttu-id="edd78-108">Considérations d’accessibilité</span><span class="sxs-lookup"><span data-stu-id="edd78-108">Considerations for Accessibility</span></span>|  
|----------------------|--------------------------------------|  
|<span data-ttu-id="edd78-109">AccessibleDescription</span><span class="sxs-lookup"><span data-stu-id="edd78-109">AccessibleDescription</span></span>|<span data-ttu-id="edd78-110">La description est signalée à l’accessibilité, notamment des lecteurs d’écran.</span><span class="sxs-lookup"><span data-stu-id="edd78-110">The description is reported to accessibility aids such as screen readers.</span></span> <span data-ttu-id="edd78-111">Les aides à l’accessibilité sont des programmes et des dispositifs spécialisés qui aident les personnes handicapées à utiliser plus efficacement les ordinateurs.</span><span class="sxs-lookup"><span data-stu-id="edd78-111">Accessibility aids are specialized programs and devices that help people with disabilities use computers more effectively.</span></span>|  
|<span data-ttu-id="edd78-112">AccessibleName</span><span class="sxs-lookup"><span data-stu-id="edd78-112">AccessibleName</span></span>|<span data-ttu-id="edd78-113">Le nom qui sera indiqué aux outils d’accessibilité.</span><span class="sxs-lookup"><span data-stu-id="edd78-113">The name that will be reported to the accessibility aids.</span></span>|  
|<span data-ttu-id="edd78-114">AccessibleRole</span><span class="sxs-lookup"><span data-stu-id="edd78-114">AccessibleRole</span></span>|<span data-ttu-id="edd78-115">Décrit l’utilisation de l’élément dans l’interface utilisateur.</span><span class="sxs-lookup"><span data-stu-id="edd78-115">Describes the use of the element in the user interface.</span></span>|  
|<span data-ttu-id="edd78-116">TabIndex</span><span class="sxs-lookup"><span data-stu-id="edd78-116">TabIndex</span></span>|<span data-ttu-id="edd78-117">Crée un chemin de navigation cohérent dans le formulaire.</span><span class="sxs-lookup"><span data-stu-id="edd78-117">Creates a sensible navigational path through the form.</span></span> <span data-ttu-id="edd78-118">Il est important pour les contrôles sans étiquette intrinsèque, tels que des zones de texte, pour que leur étiquette associée les précède immédiatement dans l’ordre de tabulation.</span><span class="sxs-lookup"><span data-stu-id="edd78-118">It is important for controls without intrinsic labels, such as text boxes, to have their associated label immediately precede them in the tab order.</span></span>|  
|<span data-ttu-id="edd78-119">Texte</span><span class="sxs-lookup"><span data-stu-id="edd78-119">Text</span></span>|<span data-ttu-id="edd78-120">Utilisez le caractère « & » pour créer des clés d’accès.</span><span class="sxs-lookup"><span data-stu-id="edd78-120">Use the "&" character to create access keys.</span></span> <span data-ttu-id="edd78-121">À l’aide des touches d’accès est la partie de fournir un accès clavier documenté aux fonctionnalités.</span><span class="sxs-lookup"><span data-stu-id="edd78-121">Using access keys is part of providing documented keyboard access to features.</span></span>|  
|<span data-ttu-id="edd78-122">Taille de police</span><span class="sxs-lookup"><span data-stu-id="edd78-122">Font Size</span></span>|<span data-ttu-id="edd78-123">Si la taille de police n’est pas réglable, elle doit être la valeur 10 points ou plus.</span><span class="sxs-lookup"><span data-stu-id="edd78-123">If the font size is not adjustable, then it should be set to 10 points or larger.</span></span> <span data-ttu-id="edd78-124">Une fois que la taille de police du formulaire est définie, tous les contrôles ajoutés au formulaire par la suite aura la même taille.</span><span class="sxs-lookup"><span data-stu-id="edd78-124">Once the form's font size is set, all the controls added to the form thereafter will have the same size.</span></span>|  
|<span data-ttu-id="edd78-125">ForeColor</span><span class="sxs-lookup"><span data-stu-id="edd78-125">Forecolor</span></span>|<span data-ttu-id="edd78-126">Si cette propriété est définie à la valeur par défaut, les préférences de couleur de l’utilisateur seront être utilisées dans le formulaire.</span><span class="sxs-lookup"><span data-stu-id="edd78-126">If this property is set to the default, then the user's color preferences will be used on the form.</span></span>|  
|<span data-ttu-id="edd78-127">BackColor</span><span class="sxs-lookup"><span data-stu-id="edd78-127">Backcolor</span></span>|<span data-ttu-id="edd78-128">Si cette propriété est définie à la valeur par défaut, les préférences de couleur de l’utilisateur seront être utilisées dans le formulaire.</span><span class="sxs-lookup"><span data-stu-id="edd78-128">If this property is set to the default, then the user's color preferences will be used on the form.</span></span>|  
|<span data-ttu-id="edd78-129">BackgroundImage</span><span class="sxs-lookup"><span data-stu-id="edd78-129">BackgroundImage</span></span>|<span data-ttu-id="edd78-130">Laissez cette propriété vide pour rendre le texte plus lisible.</span><span class="sxs-lookup"><span data-stu-id="edd78-130">Leave this property blank to make text more readable.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="edd78-131">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="edd78-131">See Also</span></span>  
 [<span data-ttu-id="edd78-132">Procédure pas à pas : création d'une application Windows accessible</span><span class="sxs-lookup"><span data-stu-id="edd78-132">Walkthrough: Creating an Accessible Windows-based Application</span></span>](../../../../docs/framework/winforms/advanced/walkthrough-creating-an-accessible-windows-based-application.md)
