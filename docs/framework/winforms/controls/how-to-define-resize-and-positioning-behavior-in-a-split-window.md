---
title: "Comment : définir le redimensionnement et le positionnement du comportement dans une fenêtre fractionnée"
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
helpviewer_keywords:
- split windows [Windows Forms], resizing
- splitter windows [Windows Forms], resizing
- SplitContainer control [Windows Forms], resizing
ms.assetid: 9bf73f36-ed2d-4a02-b15a-0770eff4fdfa
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: db4a99c7dae7783e8ea51f43ad51fcd2214997e5
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-define-resize-and-positioning-behavior-in-a-split-window"></a><span data-ttu-id="8f60c-102">Comment : définir le redimensionnement et le positionnement du comportement dans une fenêtre fractionnée</span><span class="sxs-lookup"><span data-stu-id="8f60c-102">How to: Define Resize and Positioning Behavior in a Split Window</span></span>
<span data-ttu-id="8f60c-103">Les panneaux de la <xref:System.Windows.Forms.SplitContainer> contrôle se prêtent bien au redimensionnement et manipulées par les utilisateurs.</span><span class="sxs-lookup"><span data-stu-id="8f60c-103">The panels of the <xref:System.Windows.Forms.SplitContainer> control lend themselves well to being resized and manipulated by users.</span></span> <span data-ttu-id="8f60c-104">Toutefois, il peut arriver lorsque vous souhaitez contrôler par programme le séparateur, où il est positionné, et dans quelle mesure il peut être déplacé.</span><span class="sxs-lookup"><span data-stu-id="8f60c-104">However, there will be times when you will want to programmatically control the splitter—where it is positioned and to what degree it can be moved.</span></span>  
  
 <span data-ttu-id="8f60c-105">Le <xref:System.Windows.Forms.SplitContainer.SplitterIncrement%2A> propriété et les autres propriétés sur le <xref:System.Windows.Forms.SplitContainer> contrôle vous donne un contrôle précis sur le comportement de votre interface utilisateur en fonction de vos besoins.</span><span class="sxs-lookup"><span data-stu-id="8f60c-105">The <xref:System.Windows.Forms.SplitContainer.SplitterIncrement%2A> property and the other properties on the <xref:System.Windows.Forms.SplitContainer> control give you precise control over the behavior of your user interface to suit your needs.</span></span> <span data-ttu-id="8f60c-106">Ces propriétés sont répertoriées dans le tableau suivant.</span><span class="sxs-lookup"><span data-stu-id="8f60c-106">These properties are listed in the following table.</span></span>  
  
|<span data-ttu-id="8f60c-107">Nom</span><span class="sxs-lookup"><span data-stu-id="8f60c-107">Name</span></span>|<span data-ttu-id="8f60c-108">Description</span><span class="sxs-lookup"><span data-stu-id="8f60c-108">Description</span></span>|  
|----------|-----------------|  
|<span data-ttu-id="8f60c-109">Propriété <xref:System.Windows.Forms.SplitContainer.IsSplitterFixed%2A></span><span class="sxs-lookup"><span data-stu-id="8f60c-109"><xref:System.Windows.Forms.SplitContainer.IsSplitterFixed%2A> property</span></span>|<span data-ttu-id="8f60c-110">Détermine si le séparateur est mobile au moyen de la souris ou du clavier.</span><span class="sxs-lookup"><span data-stu-id="8f60c-110">Determines if the splitter is movable by means of the keyboard or mouse.</span></span>|  
|<span data-ttu-id="8f60c-111">Propriété <xref:System.Windows.Forms.SplitContainer.SplitterDistance%2A></span><span class="sxs-lookup"><span data-stu-id="8f60c-111"><xref:System.Windows.Forms.SplitContainer.SplitterDistance%2A> property</span></span>|<span data-ttu-id="8f60c-112">Détermine la distance en pixels du bord gauche ou supérieur à la barre de fractionnement mobile.</span><span class="sxs-lookup"><span data-stu-id="8f60c-112">Determines the distance in pixels from the left or upper edge to the movable splitter bar.</span></span>|  
|<span data-ttu-id="8f60c-113">Propriété <xref:System.Windows.Forms.SplitContainer.SplitterIncrement%2A></span><span class="sxs-lookup"><span data-stu-id="8f60c-113"><xref:System.Windows.Forms.SplitContainer.SplitterIncrement%2A> property</span></span>|<span data-ttu-id="8f60c-114">Détermine la distance minimale, en pixels, que le séparateur peut être déplacé par l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="8f60c-114">Determines the minimum distance, in pixels, that the splitter can be moved by the user.</span></span>|  
  
 <span data-ttu-id="8f60c-115">L’exemple suivant modifie le <xref:System.Windows.Forms.SplitContainer.SplitterIncrement%2A> propriété pour créer un effet « séparateur d’alignement » ; lorsque l’utilisateur fait glisser le séparateur, il incrémente par unités de 10 pixels plutôt que la valeur par défaut 1.</span><span class="sxs-lookup"><span data-stu-id="8f60c-115">The example below modifies the <xref:System.Windows.Forms.SplitContainer.SplitterIncrement%2A> property to create a "snapping splitter" effect; when the user drags the splitter, it increments in units of 10 pixels rather than the default 1.</span></span>  
  
### <a name="to-define-splitcontainer-resize-behavior"></a><span data-ttu-id="8f60c-116">Pour définir le comportement de redimensionnement SplitContainer</span><span class="sxs-lookup"><span data-stu-id="8f60c-116">To define SplitContainer resize behavior</span></span>  
  
1.  <span data-ttu-id="8f60c-117">Dans une procédure, vous devez définir le <xref:System.Windows.Forms.SplitContainer.SplitterIncrement%2A> propriété à la taille de votre choix, afin que le comportement « d’alignement » du séparateur s’exécute.</span><span class="sxs-lookup"><span data-stu-id="8f60c-117">In a procedure, set the <xref:System.Windows.Forms.SplitContainer.SplitterIncrement%2A> property to the desired size, so that the 'snapping' behavior of the splitter is achieved.</span></span>  
  
     <span data-ttu-id="8f60c-118">Dans l’exemple de code suivant, au sein du formulaire <xref:System.Windows.Forms.Form.Load> événement, le séparateur dans le <xref:System.Windows.Forms.SplitContainer> contrôle est défini sur le saut de 10 pixels lorsque vous faites glisser.</span><span class="sxs-lookup"><span data-stu-id="8f60c-118">In the following code example, within the form's <xref:System.Windows.Forms.Form.Load> event, the splitter within the <xref:System.Windows.Forms.SplitContainer> control is set to jump 10 pixels when dragged.</span></span>  
  
    ```vb  
    Private Sub Form1_Load(ByVal sender As System.Object, _  
        ByVal e As System.EventArgs) Handles MyBase.Load  
        Dim splitSnapper as new SplitContainer()  
        splitSnapper.SplitterIncrement = 10  
        splitSnapper.Dock = DockStyle.Fill  
        splitSnapper.Parent = me  
    End Sub  
    ```  
  
    ```csharp  
    private void Form1_Load(System.Object sender, System.EventArgs e)  
    {  
        SplitContainer splitSnapper = new SplitContainer();  
        splitSnapper.SplitterIncrement = 10;  
        splitSnapper.Dock = DockStyle.Fill;  
        splitSnapper.Parent = this;  
    }  
    ```  
  
     <span data-ttu-id="8f60c-119">([!INCLUDE[csprcs](../../../../includes/csprcs-md.md)]) Placez le code suivant dans le constructeur du formulaire pour inscrire le Gestionnaire d’événements.</span><span class="sxs-lookup"><span data-stu-id="8f60c-119">([!INCLUDE[csprcs](../../../../includes/csprcs-md.md)]) Place the following code in the form's constructor to register the event handler.</span></span>  
  
    ```csharp  
    this.Load += new System.EventHandler(this.Form1_Load);  
    ```  
  
     <span data-ttu-id="8f60c-120">Déplacer le séparateur légèrement vers la droite ou gauche n’a aucun effet visible ; Toutefois, lorsque le pointeur de souris passe 10 pixels dans les deux sens, le séparateur s’alignera à la nouvelle position.</span><span class="sxs-lookup"><span data-stu-id="8f60c-120">Moving the splitter slightly to the left or right will have no discernible effect; however, when the mouse pointer goes 10 pixels in either direction, the splitter will snap to the new position.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8f60c-121">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="8f60c-121">See Also</span></span>  
 <xref:System.Windows.Forms.SplitContainer>  
 <xref:System.Windows.Forms.SplitContainer.SplitterIncrement%2A>
