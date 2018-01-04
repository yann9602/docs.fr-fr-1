---
title: Applications d'interface multidocument (MDI, Multiple Document Interface)
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- forms [Windows Forms], MDI
- windows [Windows Forms], mDI
- Windows Forms, MDI applications
- MDI
ms.assetid: 599faf75-13cf-49cc-ad3c-255545e5cb97
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 74735afcb1d6be319ad5d497615a3b725a4d5574
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="multiple-document-interface-mdi-applications"></a><span data-ttu-id="81ac0-102">Applications d'interface multidocument (MDI, Multiple Document Interface)</span><span class="sxs-lookup"><span data-stu-id="81ac0-102">Multiple-Document Interface (MDI) Applications</span></span>
<span data-ttu-id="81ac0-103">Applications d’interface multidocument (MDI) permettent d’afficher plusieurs documents en même temps, chaque document affiché dans sa propre fenêtre.</span><span class="sxs-lookup"><span data-stu-id="81ac0-103">Multiple-document interface (MDI) applications enable you to display multiple documents at the same time, with each document displayed in its own window.</span></span> <span data-ttu-id="81ac0-104">Les applications MDI ont souvent un élément de menu Fenêtre avec les sous-menus de basculer entre les fenêtres et aux documents.</span><span class="sxs-lookup"><span data-stu-id="81ac0-104">MDI applications often have a Window menu item with submenus for switching between windows or documents.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="81ac0-105">Il existe des différences de comportement entre des formulaires MDI et les fenêtres de l’interface monodocument (SDI) dans les Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="81ac0-105">There are some behavior differences between MDI forms and single-document interface (SDI) windows in Windows Forms.</span></span> <span data-ttu-id="81ac0-106">Le `Opacity` propriété n’affecte pas l’apparence des formulaires MDI enfants.</span><span class="sxs-lookup"><span data-stu-id="81ac0-106">The `Opacity` property does not affect the appearance of MDI child forms.</span></span> <span data-ttu-id="81ac0-107">En outre, le <xref:System.Windows.Forms.Form.CenterToParent%2A> méthode n’affecte pas le comportement des formulaires MDI enfants.</span><span class="sxs-lookup"><span data-stu-id="81ac0-107">Additionally, the <xref:System.Windows.Forms.Form.CenterToParent%2A> method does not affect the behavior of MDI child forms.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="81ac0-108">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="81ac0-108">In This Section</span></span>  
 [<span data-ttu-id="81ac0-109">Guide pratique pour créer des formulaires MDI parents</span><span class="sxs-lookup"><span data-stu-id="81ac0-109">How to: Create MDI Parent Forms</span></span>](../../../../docs/framework/winforms/advanced/how-to-create-mdi-parent-forms.md)  
 <span data-ttu-id="81ac0-110">Explique comment créer le conteneur de plusieurs documents dans une application MDI.</span><span class="sxs-lookup"><span data-stu-id="81ac0-110">Gives directions for creating the container for the multiple documents within an MDI application.</span></span>  
  
 [<span data-ttu-id="81ac0-111">Guide pratique pour créer des formulaires MDI enfants</span><span class="sxs-lookup"><span data-stu-id="81ac0-111">How to: Create MDI Child Forms</span></span>](../../../../docs/framework/winforms/advanced/how-to-create-mdi-child-forms.md)  
 <span data-ttu-id="81ac0-112">Fournit des instructions pour la création d’une ou plusieurs fenêtres qui opèrent dans un formulaire MDI parent.</span><span class="sxs-lookup"><span data-stu-id="81ac0-112">Gives directions for creating one or more windows that operate within an MDI parent form.</span></span>  
  
 [<span data-ttu-id="81ac0-113">Guide pratique pour déterminer l’enfant MDI actif</span><span class="sxs-lookup"><span data-stu-id="81ac0-113">How to: Determine the Active MDI Child</span></span>](../../../../docs/framework/winforms/advanced/how-to-determine-the-active-mdi-child.md)  
 <span data-ttu-id="81ac0-114">Fournit des instructions pour la vérification de la fenêtre enfant qui a le focus (et envoyer son contenu dans le Presse-papiers).</span><span class="sxs-lookup"><span data-stu-id="81ac0-114">Gives directions for verifying the child window that has focus (and sending its contents to the Clipboard).</span></span>  
  
 [<span data-ttu-id="81ac0-115">Guide pratique pour envoyer des données à l’enfant MDI actif</span><span class="sxs-lookup"><span data-stu-id="81ac0-115">How to: Send Data to the Active MDI Child</span></span>](../../../../docs/framework/winforms/advanced/how-to-send-data-to-the-active-mdi-child.md)  
 <span data-ttu-id="81ac0-116">Explique comment transmettre des informations à la fenêtre enfant active.</span><span class="sxs-lookup"><span data-stu-id="81ac0-116">Gives directions for transporting information to the active child window.</span></span>  
  
 [<span data-ttu-id="81ac0-117">Guide pratique pour réorganiser des formulaires MDI enfants</span><span class="sxs-lookup"><span data-stu-id="81ac0-117">How to: Arrange MDI Child Forms</span></span>](../../../../docs/framework/winforms/advanced/how-to-arrange-mdi-child-forms.md)  
 <span data-ttu-id="81ac0-118">Fournit des instructions pour la disposition en mosaïque, en cascade ou réorganiser les fenêtres enfants d’une application MDI.</span><span class="sxs-lookup"><span data-stu-id="81ac0-118">Gives directions for tiling, cascading, or arranging the child windows of an MDI application.</span></span>
