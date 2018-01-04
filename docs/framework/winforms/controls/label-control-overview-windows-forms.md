---
title: "Vue d'ensemble du contrôle Label (Windows Forms)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: Label
helpviewer_keywords:
- images [Windows Forms], displaying in labels
- labels
- Label control [Windows Forms], about Label control
ms.assetid: dcad7f44-11b7-4c55-b0c0-d984ade43d7d
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: f68642eb5f996722097976e042006afbf366ae39
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="label-control-overview-windows-forms"></a><span data-ttu-id="96c43-102">Vue d'ensemble du contrôle Label (Windows Forms)</span><span class="sxs-lookup"><span data-stu-id="96c43-102">Label Control Overview (Windows Forms)</span></span>
<span data-ttu-id="96c43-103">Windows Forms <xref:System.Windows.Forms.Label> contrôles sont utilisés pour afficher du texte ou des images qui ne sont pas modifiables par l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="96c43-103">Windows Forms <xref:System.Windows.Forms.Label> controls are used to display text or images that cannot be edited by the user.</span></span> <span data-ttu-id="96c43-104">Ils sont utilisés pour identifier des objets sur un formulaire — pour décrire ce que fait un contrôle lorsque vous cliquez dessus, par exemple, ou pour afficher des informations en réponse à un événement d’exécution ou dans votre application.</span><span class="sxs-lookup"><span data-stu-id="96c43-104">They are used to identify objects on a form — to provide a description of what a certain control will do if clicked, for example, or to display information in response to a run-time event or process in your application.</span></span> <span data-ttu-id="96c43-105">Par exemple, vous pouvez utiliser des étiquettes pour ajouter des légendes pour les zones de texte, zones de liste, zones de liste déroulante et ainsi de suite.</span><span class="sxs-lookup"><span data-stu-id="96c43-105">For example, you can use labels to add descriptive captions to text boxes, list boxes, combo boxes, and so on.</span></span> <span data-ttu-id="96c43-106">Vous pouvez également écrire du code qui modifie le texte affiché par une étiquette en réponse aux événements au moment de l’exécution.</span><span class="sxs-lookup"><span data-stu-id="96c43-106">You can also write code that changes the text displayed by a label in response to events at run time.</span></span> <span data-ttu-id="96c43-107">Par exemple, si votre application prend quelques minutes pour traiter une modification, vous pouvez afficher un message d’état de traitement dans une étiquette.</span><span class="sxs-lookup"><span data-stu-id="96c43-107">For example, if your application takes a few minutes to process a change, you can display a processing-status message in a label.</span></span>  
  
## <a name="working-with-the-label-control"></a><span data-ttu-id="96c43-108">Utilisation du contrôle Label</span><span class="sxs-lookup"><span data-stu-id="96c43-108">Working with the Label Control</span></span>  
 <span data-ttu-id="96c43-109">Étant donné que le <xref:System.Windows.Forms.Label> contrôle ne peut pas recevoir le focus, il peut également être utilisé pour créer des touches d’accès rapide pour d’autres contrôles.</span><span class="sxs-lookup"><span data-stu-id="96c43-109">Because the <xref:System.Windows.Forms.Label> control cannot receive the focus, it can also be used to create access keys for other controls.</span></span> <span data-ttu-id="96c43-110">Une clé d’accès permet à un utilisateur de sélectionner l’autre contrôle en appuyant sur la touche ALT et la clé d’accès.</span><span class="sxs-lookup"><span data-stu-id="96c43-110">An access key allows a user to select the other control by pressing the ALT key with the access key.</span></span> <span data-ttu-id="96c43-111">Pour plus d’informations, consultez [création de clés d’accès rapide pour les contrôles Windows Forms](../../../../docs/framework/winforms/controls/how-to-create-access-keys-for-windows-forms-controls.md) et [Comment : créer des touches d’accès rapide avec le contrôle Label Windows Forms](../../../../docs/framework/winforms/controls/how-to-create-access-keys-with-windows-forms-label-controls.md).</span><span class="sxs-lookup"><span data-stu-id="96c43-111">For more information, see [Creating Access Keys for Windows Forms Controls](../../../../docs/framework/winforms/controls/how-to-create-access-keys-for-windows-forms-controls.md) and [How to: Create Access Keys with Windows Forms Label Controls](../../../../docs/framework/winforms/controls/how-to-create-access-keys-with-windows-forms-label-controls.md).</span></span>  
  
 <span data-ttu-id="96c43-112">La légende affichée dans l’étiquette est contenue dans le <xref:System.Windows.Forms.Label.Text%2A> propriété.</span><span class="sxs-lookup"><span data-stu-id="96c43-112">The caption displayed in the label is contained in the <xref:System.Windows.Forms.Label.Text%2A> property.</span></span> <span data-ttu-id="96c43-113">Le <xref:System.Windows.Forms.Label.TextAlign%2A> propriété vous permet de définir l’alignement du texte dans l’étiquette.</span><span class="sxs-lookup"><span data-stu-id="96c43-113">The <xref:System.Windows.Forms.Label.TextAlign%2A> property allows you to set the alignment of the text within the label.</span></span> <span data-ttu-id="96c43-114">Pour plus d’informations, consultez [Comment : définir le texte affiché par un contrôle Windows Forms](../../../../docs/framework/winforms/controls/how-to-set-the-text-displayed-by-a-windows-forms-control.md).</span><span class="sxs-lookup"><span data-stu-id="96c43-114">For more information, see [How to: Set the Text Displayed by a Windows Forms Control](../../../../docs/framework/winforms/controls/how-to-set-the-text-displayed-by-a-windows-forms-control.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="96c43-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="96c43-115">See Also</span></span>  
 <xref:System.Windows.Forms.Label>  
 [<span data-ttu-id="96c43-116">Guide pratique pour dimensionner un contrôle Label Windows Forms en fonction de son contenu</span><span class="sxs-lookup"><span data-stu-id="96c43-116">How to: Size a Windows Forms Label Control to Fit Its Contents</span></span>](../../../../docs/framework/winforms/controls/how-to-size-a-windows-forms-label-control-to-fit-its-contents.md)  
 [<span data-ttu-id="96c43-117">Guide pratique pour créer des touches d'accès rapide à l'aide des contrôles Label Windows Forms</span><span class="sxs-lookup"><span data-stu-id="96c43-117">How to: Create Access Keys with Windows Forms Label Controls</span></span>](../../../../docs/framework/winforms/controls/how-to-create-access-keys-with-windows-forms-label-controls.md)
