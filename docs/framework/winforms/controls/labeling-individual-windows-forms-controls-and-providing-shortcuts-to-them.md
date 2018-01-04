---
title: "Création d'étiquettes et de raccourcis pour les contrôles Windows Forms"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- controls [Windows Forms], access keys
- shortcuts [Windows Forms], controls
- keyboard shortcuts [Windows Forms], controls
- Windows Forms controls, labels
ms.assetid: 6eaf868c-819f-4131-8f59-048e20c286f7
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 5e64a2a858b9506ec08beff728e23da0f817f170
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="labeling-individual-windows-forms-controls-and-providing-shortcuts-to-them"></a><span data-ttu-id="0b38a-102">Création d'étiquettes et de raccourcis pour les contrôles Windows Forms</span><span class="sxs-lookup"><span data-stu-id="0b38a-102">Labeling Individual Windows Forms Controls and Providing Shortcuts to Them</span></span>
<span data-ttu-id="0b38a-103">Les contrôles ajoutés aux Windows Forms ont des propriétés et des méthodes qui permettent de spécialiser davantage l'expérience utilisateur.</span><span class="sxs-lookup"><span data-stu-id="0b38a-103">Controls added to Windows Forms have properties and methods that are used to further specialize the user experience.</span></span> <span data-ttu-id="0b38a-104">La personnalisation de l'interface utilisateur en fonction des besoins de l'utilisateur est extrêmement importante pour les applications Windows bien conçues.</span><span class="sxs-lookup"><span data-stu-id="0b38a-104">Customizing your user interface to suit the needs of the user is extremely important for well-designed Windows applications.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="0b38a-105">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="0b38a-105">In This Section</span></span>  
 [<span data-ttu-id="0b38a-106">Guide pratique pour définir le texte affiché par un contrôle Windows Forms</span><span class="sxs-lookup"><span data-stu-id="0b38a-106">How to: Set the Text Displayed by a Windows Forms Control</span></span>](../../../../docs/framework/winforms/controls/how-to-set-the-text-displayed-by-a-windows-forms-control.md)  
 <span data-ttu-id="0b38a-107">Décrit comment attribuer une étiquette de texte à un contrôle.</span><span class="sxs-lookup"><span data-stu-id="0b38a-107">Describes how to assign a text label to a control.</span></span>  
  
 [<span data-ttu-id="0b38a-108">Guide pratique pour définir l'image affichée par un contrôle Windows Forms</span><span class="sxs-lookup"><span data-stu-id="0b38a-108">How to: Set the Image Displayed by a Windows Forms Control</span></span>](../../../../docs/framework/winforms/controls/how-to-set-the-image-displayed-by-a-windows-forms-control.md)  
 <span data-ttu-id="0b38a-109">Explique comment configurer un contrôle pour afficher des images.</span><span class="sxs-lookup"><span data-stu-id="0b38a-109">Explains how to configure a control to display images.</span></span>  
  
 [<span data-ttu-id="0b38a-110">Guide pratique pour créer des touches d'accès rapide pour des contrôles Windows Forms</span><span class="sxs-lookup"><span data-stu-id="0b38a-110">How to: Create Access Keys for Windows Forms Controls</span></span>](../../../../docs/framework/winforms/controls/how-to-create-access-keys-for-windows-forms-controls.md)  
 <span data-ttu-id="0b38a-111">Fournit des informations sur la création de raccourcis clavier prédéfinis.</span><span class="sxs-lookup"><span data-stu-id="0b38a-111">Gives information about creating predefined keyboard shortcuts.</span></span>  
  
 [<span data-ttu-id="0b38a-112">Informations d'accessibilité sur les contrôles d'un Windows Form</span><span class="sxs-lookup"><span data-stu-id="0b38a-112">Providing Accessibility Information for Controls on a Windows Form</span></span>](../../../../docs/framework/winforms/controls/providing-accessibility-information-for-controls-on-a-windows-form.md)  
 <span data-ttu-id="0b38a-113">Fournit des informations sur la façon de configurer des contrôles pour qu'ils fonctionnent avec les options d'accessibilité.</span><span class="sxs-lookup"><span data-stu-id="0b38a-113">Gives information about enabling your controls to work with accessibility aids.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="0b38a-114">Rubriques connexes</span><span class="sxs-lookup"><span data-stu-id="0b38a-114">Related Sections</span></span>  
 [<span data-ttu-id="0b38a-115">Contrôles Windows Forms</span><span class="sxs-lookup"><span data-stu-id="0b38a-115">Windows Forms Controls</span></span>](../../../../docs/framework/winforms/controls/index.md)  
 <span data-ttu-id="0b38a-116">Fournit des liens vers d'autres tâches de base que vous pouvez effectuer avec des contrôles.</span><span class="sxs-lookup"><span data-stu-id="0b38a-116">Links to other basic things you can do with controls.</span></span>  
  
 <span data-ttu-id="0b38a-117">Consultez également [Comment : créer accès clés pour Windows Forms contrôles à l’aide du concepteur](http://msdn.microsoft.com/library/ms233673\(v=vs.110\)), [Comment : définir le texte affiché par un contrôle Windows Forms à l’aide du concepteur](http://msdn.microsoft.com/library/ms233665\(v=vs.110\)), [Comment : définir l’Image Affiché par un contrôle à l’aide du Concepteur Windows Forms](http://msdn.microsoft.com/library/ms233656\(v=vs.110\)).</span><span class="sxs-lookup"><span data-stu-id="0b38a-117">Also see [How to: Create Access Keys for Windows Forms Controls Using the Designer](http://msdn.microsoft.com/library/ms233673\(v=vs.110\)), [How to: Set the Text Displayed by a Windows Forms Control Using the Designer](http://msdn.microsoft.com/library/ms233665\(v=vs.110\)), [How to: Set the Image Displayed by a Windows Forms Control Using the Designer](http://msdn.microsoft.com/library/ms233656\(v=vs.110\)).</span></span>
