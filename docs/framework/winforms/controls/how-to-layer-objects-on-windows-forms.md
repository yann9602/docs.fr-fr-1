---
title: "Comment : superposer des objets dans les Windows Forms"
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
- cpp
helpviewer_keywords:
- Windows Forms controls, layering
- controls [Windows Forms], layering
- z order
- controls [Windows Forms], positioning
- z-order
ms.assetid: 1acc4281-2976-4715-86f4-bda68134baaf
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: d956ae8fb643d616bc0e5dc514f21ca95fa50a48
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/19/2018
---
# <a name="how-to-layer-objects-on-windows-forms"></a><span data-ttu-id="a30e3-102">Comment : superposer des objets dans les Windows Forms</span><span class="sxs-lookup"><span data-stu-id="a30e3-102">How to: Layer Objects on Windows Forms</span></span>
<span data-ttu-id="a30e3-103">Lorsque vous créez une interface utilisateur complexe, ou utilisez un formulaire d’interface (multidocument MDI) document, vous souhaitez souvent superposer les contrôles et les formulaires enfants pour créer des interfaces utilisateur (IU) plus complexes.</span><span class="sxs-lookup"><span data-stu-id="a30e3-103">When you create a complex user interface, or work with a multiple document interface (MDI) form, you will often want to layer both controls and child forms to create more complex user interfaces (UI).</span></span> <span data-ttu-id="a30e3-104">Pour déplacer et effectuer le suivi des contrôles et fenêtres dans le contexte d’un groupe, vous manipulez leur ordre de plan.</span><span class="sxs-lookup"><span data-stu-id="a30e3-104">To move and keep track of controls and windows within the context of a group, you manipulate their z-order.</span></span> <span data-ttu-id="a30e3-105">*Ordre de plan* est la superposition visuelle des contrôles d’un formulaire sur l’axe z (profondeur).</span><span class="sxs-lookup"><span data-stu-id="a30e3-105">*Z-order* is the visual layering of controls on a form along the form's z-axis (depth).</span></span> <span data-ttu-id="a30e3-106">La fenêtre en haut de l’ordre de plan superpose à toutes les autres fenêtres.</span><span class="sxs-lookup"><span data-stu-id="a30e3-106">The window at the top of the z-order overlaps all other windows.</span></span> <span data-ttu-id="a30e3-107">Toutes les autres fenêtres chevauchent la fenêtre en bas de l’ordre de plan.</span><span class="sxs-lookup"><span data-stu-id="a30e3-107">All other windows overlap the window at the bottom of the z-order.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="a30e3-108">Les boîtes de dialogue et les commandes de menu qui s'affichent peuvent être différentes de celles qui sont décrites dans l'aide, en fonction de vos paramètres actifs ou de l'édition utilisée.</span><span class="sxs-lookup"><span data-stu-id="a30e3-108">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="a30e3-109">Pour modifier vos paramètres, choisissez **Importation et exportation de paramètres** dans le menu **Outils** .</span><span class="sxs-lookup"><span data-stu-id="a30e3-109">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="a30e3-110">Pour plus d’informations, consultez [Personnalisation des paramètres de développement dans Visual Studio](http://msdn.microsoft.com/library/22c4debb-4e31-47a8-8f19-16f328d7dcd3).</span><span class="sxs-lookup"><span data-stu-id="a30e3-110">For more information, see [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/library/22c4debb-4e31-47a8-8f19-16f328d7dcd3).</span></span>  
  
### <a name="to-layer-controls-at-design-time"></a><span data-ttu-id="a30e3-111">Pour superposer des contrôles au moment du design</span><span class="sxs-lookup"><span data-stu-id="a30e3-111">To layer controls at design time</span></span>  
  
1.  <span data-ttu-id="a30e3-112">Sélectionnez un contrôle à la couche.</span><span class="sxs-lookup"><span data-stu-id="a30e3-112">Select a control that you want to layer.</span></span>  
  
2.  <span data-ttu-id="a30e3-113">Sur le **Format** menu, pointez sur **commande**, puis cliquez sur **mettre au premier plan** ou **arrière-plan**.</span><span class="sxs-lookup"><span data-stu-id="a30e3-113">On the **Format** menu, point to **Order**, and then click **Bring To Front** or **Send To Back**.</span></span>  
  
### <a name="to-layer-controls-programmatically"></a><span data-ttu-id="a30e3-114">Pour superposer les contrôles par programmation</span><span class="sxs-lookup"><span data-stu-id="a30e3-114">To layer controls programmatically</span></span>  
  
-   <span data-ttu-id="a30e3-115">Utilisez le <xref:System.Windows.Forms.Control.BringToFront%2A> et <xref:System.Windows.Forms.Control.SendToBack%2A> méthodes permettant de manipuler l’ordre de plan des contrôles.</span><span class="sxs-lookup"><span data-stu-id="a30e3-115">Use the <xref:System.Windows.Forms.Control.BringToFront%2A> and <xref:System.Windows.Forms.Control.SendToBack%2A> methods to manipulate the z-order of the controls.</span></span>  
  
     <span data-ttu-id="a30e3-116">Par exemple, si un <xref:System.Windows.Forms.TextBox> contrôle, `txtFirstName`, est sous un autre contrôle et que vous souhaitez qu’il en haut, utilisez le code suivant :</span><span class="sxs-lookup"><span data-stu-id="a30e3-116">For example, if a <xref:System.Windows.Forms.TextBox> control, `txtFirstName`, is underneath another control and you want to have it on top, use the following code:</span></span>  
  
    ```vb  
    txtFirstName.BringToFront()  
    ```  
  
    ```csharp  
    txtFirstName.BringToFront();  
    ```  
  
    ```cpp  
    txtFirstName->BringToFront();  
    ```  
  
> [!NOTE]
>  <span data-ttu-id="a30e3-117">Windows Forms prend en charge *contrôler la relation contenant-contenu*.</span><span class="sxs-lookup"><span data-stu-id="a30e3-117">Windows Forms supports *control containment*.</span></span> <span data-ttu-id="a30e3-118">Fonction consiste à placer un nombre de contrôles dans un contrôle conteneur, comme un nombre de <xref:System.Windows.Forms.RadioButton> des contrôles dans un <xref:System.Windows.Forms.GroupBox> contrôle.</span><span class="sxs-lookup"><span data-stu-id="a30e3-118">Control containment involves placing a number of controls within a containing control, such as a number of <xref:System.Windows.Forms.RadioButton> controls within a <xref:System.Windows.Forms.GroupBox> control.</span></span> <span data-ttu-id="a30e3-119">Vous pouvez ensuite superposer les contrôles dans le contrôle conteneur.</span><span class="sxs-lookup"><span data-stu-id="a30e3-119">You can then layer the controls within the containing control.</span></span> <span data-ttu-id="a30e3-120">La zone de groupe est déplacée, les contrôles, car elle contient.</span><span class="sxs-lookup"><span data-stu-id="a30e3-120">Moving the group box moves the controls as well, because they are contained inside it.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a30e3-121">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="a30e3-121">See Also</span></span>  
 [<span data-ttu-id="a30e3-122">Contrôles Windows Forms</span><span class="sxs-lookup"><span data-stu-id="a30e3-122">Windows Forms Controls</span></span>](../../../../docs/framework/winforms/controls/index.md)  
 [<span data-ttu-id="a30e3-123">Disposition des contrôles dans les Windows Forms</span><span class="sxs-lookup"><span data-stu-id="a30e3-123">Arranging Controls on Windows Forms</span></span>](../../../../docs/framework/winforms/controls/arranging-controls-on-windows-forms.md)  
 [<span data-ttu-id="a30e3-124">Création d'étiquettes et de raccourcis pour les contrôles Windows Forms</span><span class="sxs-lookup"><span data-stu-id="a30e3-124">Labeling Individual Windows Forms Controls and Providing Shortcuts to Them</span></span>](../../../../docs/framework/winforms/controls/labeling-individual-windows-forms-controls-and-providing-shortcuts-to-them.md)  
 [<span data-ttu-id="a30e3-125">Contrôles à utiliser dans les Windows Forms</span><span class="sxs-lookup"><span data-stu-id="a30e3-125">Controls to Use on Windows Forms</span></span>](../../../../docs/framework/winforms/controls/controls-to-use-on-windows-forms.md)  
 [<span data-ttu-id="a30e3-126">Classement par fonction des contrôles Windows Forms</span><span class="sxs-lookup"><span data-stu-id="a30e3-126">Windows Forms Controls by Function</span></span>](../../../../docs/framework/winforms/controls/windows-forms-controls-by-function.md)
