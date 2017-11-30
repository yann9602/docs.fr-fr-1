---
title: "Comment : créer des touches d'accès rapide pour les contrôles Windows Forms à l'aide du concepteur"
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
- Button control [Windows Forms], access keys
- dialog box controls [Windows Forms], mnemonics
- access keys [Windows Forms], creating for controls
- mnemonics [Windows Forms], adding to dialog box controls
- ampersand character in shortcut key
- Windows Forms controls, access keys
- examples [Windows Forms], controls
- Text property [Windows Forms], specifying access keys for controls
- keyboard shortcuts [Windows Forms], creating for controls
- access keys [Windows Forms], Windows Forms
- ALT key
ms.assetid: 4c374c4c-4ca9-4a68-ac96-9dc3ab0f518a
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 19c47c21526ca6e7aa4046a1853f3d1743438d17
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-create-access-keys-for-windows-forms-controls-using-the-designer"></a><span data-ttu-id="9d5ea-102">Comment : créer des touches d'accès rapide pour les contrôles Windows Forms à l'aide du concepteur</span><span class="sxs-lookup"><span data-stu-id="9d5ea-102">How to: Create Access Keys for Windows Forms Controls Using the Designer</span></span>
<span data-ttu-id="9d5ea-103">Un *clé d’accès* est un caractère souligné dans le texte d’un menu, un élément de menu ou l’étiquette d’un contrôle tel qu’un bouton.</span><span class="sxs-lookup"><span data-stu-id="9d5ea-103">An *access key* is an underlined character in the text of a menu, menu item, or the label of a control such as a button.</span></span> <span data-ttu-id="9d5ea-104">Il permet à l’utilisateur « cliquer » sur un bouton en appuyant sur la touche ALT conjointement avec la clé d’accès prédéfinies.</span><span class="sxs-lookup"><span data-stu-id="9d5ea-104">It enables the user to "click" a button by pressing the ALT key in combination with the predefined access key.</span></span> <span data-ttu-id="9d5ea-105">Par exemple, si un bouton exécute une procédure pour imprimer un formulaire et par conséquent son `Text` propriété a la valeur « Print », ajoutant une esperluette (&) devant la lettre « P » a « P » soit souligné dans le texte du bouton au moment de l’exécution.</span><span class="sxs-lookup"><span data-stu-id="9d5ea-105">For example, if a button runs a procedure to print a form, and therefore its `Text` property is set to "Print," adding an ampersand (&) before the letter "P" causes the letter "P" to be underlined in the button text at run time.</span></span> <span data-ttu-id="9d5ea-106">L’utilisateur peut exécuter la commande associée au bouton en appuyant sur ALT + P.</span><span class="sxs-lookup"><span data-stu-id="9d5ea-106">The user can run the command associated with the button by pressing ALT+P.</span></span> <span data-ttu-id="9d5ea-107">Vous ne pouvez avoir une clé d’accès pour un contrôle qui ne peut pas recevoir le focus.</span><span class="sxs-lookup"><span data-stu-id="9d5ea-107">You cannot have an access key for a control that cannot receive focus.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="9d5ea-108">Les boîtes de dialogue et les commandes de menu qui s'affichent peuvent être différentes de celles qui sont décrites dans l'aide, en fonction de vos paramètres actifs ou de l'édition utilisée.</span><span class="sxs-lookup"><span data-stu-id="9d5ea-108">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="9d5ea-109">Pour modifier vos paramètres, choisissez **Importation et exportation de paramètres** dans le menu **Outils** .</span><span class="sxs-lookup"><span data-stu-id="9d5ea-109">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="9d5ea-110">Pour plus d’informations, consultez [Personnalisation des paramètres de développement dans Visual Studio](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).</span><span class="sxs-lookup"><span data-stu-id="9d5ea-110">For more information, see [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).</span></span>  
  
### <a name="to-create-an-access-key-for-a-control"></a><span data-ttu-id="9d5ea-111">Pour créer une clé d’accès pour un contrôle</span><span class="sxs-lookup"><span data-stu-id="9d5ea-111">To create an access key for a control</span></span>  
  
1.  <span data-ttu-id="9d5ea-112">Dans le **propriétés** , configurez le `Text` propriété à une chaîne qui inclut une esperluette (&) avant la lettre qui sera la clé d’accès.</span><span class="sxs-lookup"><span data-stu-id="9d5ea-112">In the **Properties** window, set the `Text` property to a string that includes an ampersand (&) before the letter that will be the access key.</span></span> <span data-ttu-id="9d5ea-113">Par exemple, pour définir la lettre « P » en tant que la clé d’accès, tapez **& Imprimer** dans la grille.</span><span class="sxs-lookup"><span data-stu-id="9d5ea-113">For example, to set the letter "P" as the access key, type **&Print** into the grid.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9d5ea-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="9d5ea-114">See Also</span></span>  
 <xref:System.Windows.Forms.Button>  
 [<span data-ttu-id="9d5ea-115">Guide pratique pour répondre à un clic du contrôle Button Windows Forms</span><span class="sxs-lookup"><span data-stu-id="9d5ea-115">How to: Respond to Windows Forms Button Clicks</span></span>](../../../../docs/framework/winforms/controls/how-to-respond-to-windows-forms-button-clicks.md)  
 [<span data-ttu-id="9d5ea-116">Guide pratique pour définir le texte affiché par un contrôle Windows Forms</span><span class="sxs-lookup"><span data-stu-id="9d5ea-116">How to: Set the Text Displayed by a Windows Forms Control</span></span>](../../../../docs/framework/winforms/controls/how-to-set-the-text-displayed-by-a-windows-forms-control.md)  
 [<span data-ttu-id="9d5ea-117">Création d'étiquettes et de raccourcis pour les contrôles Windows Forms</span><span class="sxs-lookup"><span data-stu-id="9d5ea-117">Labeling Individual Windows Forms Controls and Providing Shortcuts to Them</span></span>](../../../../docs/framework/winforms/controls/labeling-individual-windows-forms-controls-and-providing-shortcuts-to-them.md)
