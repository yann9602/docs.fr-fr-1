---
title: "Comment : définir le texte affiché par un contrôle Windows Forms à l'aide du concepteur"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- controls [Windows Forms], setting caption
- Windows Forms, setting the text displayed
ms.assetid: 9d18e0e0-f17f-4074-837d-e67ceeeaa89d
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 59d66df2c6f18ad28ad4b912c00e35f786d773da
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-set-the-text-displayed-by-a-windows-forms-control-using-the-designer"></a><span data-ttu-id="d86e7-102">Comment : définir le texte affiché par un contrôle Windows Forms à l'aide du concepteur</span><span class="sxs-lookup"><span data-stu-id="d86e7-102">How to: Set the Text Displayed by a Windows Forms Control Using the Designer</span></span>
<span data-ttu-id="d86e7-103">Contrôles Windows Forms affichent généralement un texte qui est lié à la fonction principale du contrôle.</span><span class="sxs-lookup"><span data-stu-id="d86e7-103">Windows Forms controls typically display some text that is related to the primary function of the control.</span></span> <span data-ttu-id="d86e7-104">Par exemple, un <xref:System.Windows.Forms.Button> contrôle affiche habituellement une légende qui indique l’action sera effectuée lorsque le bouton est activé.</span><span class="sxs-lookup"><span data-stu-id="d86e7-104">For example, a <xref:System.Windows.Forms.Button> control typically displays a caption that indicates what action will be performed when the button is clicked.</span></span> <span data-ttu-id="d86e7-105">Pour tous les contrôles, vous pouvez définir ou retourner le texte à l'aide de la propriété <xref:System.Windows.Forms.Control.Text%2A>.</span><span class="sxs-lookup"><span data-stu-id="d86e7-105">For all controls, you can set or return the text by using the <xref:System.Windows.Forms.Control.Text%2A> property.</span></span> <span data-ttu-id="d86e7-106">Vous pouvez modifier la police en utilisant la propriété <xref:System.Windows.Forms.Control.Font%2A>.</span><span class="sxs-lookup"><span data-stu-id="d86e7-106">You can change the font by using the <xref:System.Windows.Forms.Control.Font%2A> property.</span></span>  
  
### <a name="to-set-the-text-and-font-with-the-designer"></a><span data-ttu-id="d86e7-107">Pour définir le texte et la police avec le Concepteur</span><span class="sxs-lookup"><span data-stu-id="d86e7-107">To set the text and font with the designer</span></span>  
  
1.  <span data-ttu-id="d86e7-108">Dans la fenêtre Propriétés, définissez la <xref:System.Windows.Forms.Control.Text%2A> propriété du contrôle à une chaîne appropriée.</span><span class="sxs-lookup"><span data-stu-id="d86e7-108">In the Properties window, set the <xref:System.Windows.Forms.Control.Text%2A> property of the control to an appropriate string.</span></span>  
  
     <span data-ttu-id="d86e7-109">Pour créer une touche de raccourci soulignée, incluez une esperluette (&) avant la lettre qui sera la touche de raccourci.</span><span class="sxs-lookup"><span data-stu-id="d86e7-109">To create an underlined shortcut key, includes an ampersand (&) before the letter that will be the shortcut key.</span></span>  
  
2.  <span data-ttu-id="d86e7-110">Dans la fenêtre Propriétés, cliquez sur le bouton de sélection (![capture d’écran de VisualStudioEllipsesButton](../../../../docs/framework/winforms/media/vbellipsesbutton.png "vbEllipsesButton")) à côté du <xref:System.Windows.Forms.Control.Font%2A> propriété.</span><span class="sxs-lookup"><span data-stu-id="d86e7-110">In the Properties window, click the ellipsis button (![VisualStudioEllipsesButton screenshot](../../../../docs/framework/winforms/media/vbellipsesbutton.png "vbEllipsesButton")) next to the <xref:System.Windows.Forms.Control.Font%2A> property.</span></span>  
  
     <span data-ttu-id="d86e7-111">Dans la boîte de dialogue Police standard, sélectionnez la police, style de police, taille, effets (tels que barré ou soulignement) et script que vous souhaitez.</span><span class="sxs-lookup"><span data-stu-id="d86e7-111">In the standard font dialog box, select the font, font style, size, effects (such as strikeout or underline), and script that you want.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d86e7-112">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="d86e7-112">See Also</span></span>  
 [<span data-ttu-id="d86e7-113">Guide pratique pour définir le texte affiché par un contrôle Windows Forms</span><span class="sxs-lookup"><span data-stu-id="d86e7-113">How to: Set the Text Displayed by a Windows Forms Control</span></span>](../../../../docs/framework/winforms/controls/how-to-set-the-text-displayed-by-a-windows-forms-control.md)  
 [<span data-ttu-id="d86e7-114">Utilisation de polices et de texte</span><span class="sxs-lookup"><span data-stu-id="d86e7-114">Using Fonts and Text</span></span>](../../../../docs/framework/winforms/advanced/using-fonts-and-text.md)  
 [<span data-ttu-id="d86e7-115">Création d'étiquettes et de raccourcis pour les contrôles Windows Forms</span><span class="sxs-lookup"><span data-stu-id="d86e7-115">Labeling Individual Windows Forms Controls and Providing Shortcuts to Them</span></span>](../../../../docs/framework/winforms/controls/labeling-individual-windows-forms-controls-and-providing-shortcuts-to-them.md)
