---
title: "Contrôles constitutifs"
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
- custom controls [Windows Forms], constituent controls
- constituent controls [Windows Forms]
- user controls [Windows Forms], constituent controls
ms.assetid: 5565e720-198b-4bbd-a2bd-c447ba641798
caps.latest.revision: "16"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 2d03b69c334148313b0cd495fad1b2dfd13df833
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="constituent-controls"></a><span data-ttu-id="f7f2e-102">Contrôles constitutifs</span><span class="sxs-lookup"><span data-stu-id="f7f2e-102">Constituent Controls</span></span>
<span data-ttu-id="f7f2e-103">Les contrôles qui composent un contrôle utilisateur, appelés *contrôles constitutifs*, sont relativement peu flexibles en matière de rendu graphique personnalisé.</span><span class="sxs-lookup"><span data-stu-id="f7f2e-103">The controls that make up a user control, or *constituent controls* as they are termed, are relatively inflexible when it comes to custom graphics rendering.</span></span> <span data-ttu-id="f7f2e-104">Tous les contrôles Windows Forms gèrent leur propre rendu par l’intermédiaire de leurs propres <xref:System.Windows.Forms.Control.OnPaint%2A> (méthode).</span><span class="sxs-lookup"><span data-stu-id="f7f2e-104">All Windows Forms controls handle their own rendering through their own <xref:System.Windows.Forms.Control.OnPaint%2A> method.</span></span> <span data-ttu-id="f7f2e-105">Comme cette méthode est protégée, elle n’est pas accessible au développeur et il n’est pas possible d’empêcher son exécution quand le contrôle est dessiné.</span><span class="sxs-lookup"><span data-stu-id="f7f2e-105">Because this method is protected, it is not accessible to the developer, and thus cannot be prevented from executing when the control is painted.</span></span> <span data-ttu-id="f7f2e-106">Cela ne signifie pas pour autant que vous ne pouvez pas ajouter du code pour modifier l’apparence des contrôles constitutifs.</span><span class="sxs-lookup"><span data-stu-id="f7f2e-106">This does not mean, however, that you cannot add code to affect the appearance of constituent controls.</span></span> <span data-ttu-id="f7f2e-107">Un rendu supplémentaire est possible en ajoutant un gestionnaire d’événements.</span><span class="sxs-lookup"><span data-stu-id="f7f2e-107">Additional rendering can be accomplished by adding an event handler.</span></span> <span data-ttu-id="f7f2e-108">Par exemple, supposons que vous créez un <xref:System.Windows.Forms.UserControl> avec un bouton nommé `MyButton`.</span><span class="sxs-lookup"><span data-stu-id="f7f2e-108">For example, suppose you were authoring a <xref:System.Windows.Forms.UserControl> with a button named `MyButton`.</span></span> <span data-ttu-id="f7f2e-109">Si vous souhaitiez ont rendu supplémentaires au-delà de ce qui a été fourni par le <xref:System.Web.UI.WebControls.Button>, vous devez ajouter le code à votre contrôle utilisateur semblable au suivant :</span><span class="sxs-lookup"><span data-stu-id="f7f2e-109">If you wished to have additional rendering beyond what was provided by the <xref:System.Web.UI.WebControls.Button>, you would add code to your user control similar to the following:</span></span>  
  
```vb  
Public Sub MyPaint(ByVal sender as Object, e as PaintEventArgs) Handles _  
   MyButton.Paint  
   'Additional rendering code goes here  
End Sub  
```  
  
```csharp  
// Add the event handler to the button's Paint event.  
MyButton.Paint +=   
   new System.Windows.Forms.PaintEventHandler (this.MyPaint);  
// Create the custom painting method.  
protected void MyPaint (object sender,   
System.Windows.Forms.PaintEventArgs e)  
{  
   // Additional rendering code goes here.  
}  
```  
  
> [!NOTE]
>  <span data-ttu-id="f7f2e-110">Certains contrôles Windows Forms, telles que <xref:System.Windows.Forms.TextBox>, sont directement peints par Windows.</span><span class="sxs-lookup"><span data-stu-id="f7f2e-110">Some Windows Forms controls, such as <xref:System.Windows.Forms.TextBox>, are painted directly by Windows.</span></span> <span data-ttu-id="f7f2e-111">Dans ce cas, le <xref:System.Windows.Forms.Control.OnPaint%2A> méthode n’est jamais appelée, et par conséquent, l’exemple ci-dessus ne sera jamais appelée.</span><span class="sxs-lookup"><span data-stu-id="f7f2e-111">In these instances, the <xref:System.Windows.Forms.Control.OnPaint%2A> method is never called, and thus the above example will never be called.</span></span>  
  
 <span data-ttu-id="f7f2e-112">Ceci crée une méthode qui s’exécute chaque fois que l’événement `MyButton.Paint` s’exécute, ce qui ajoute une représentation graphique supplémentaire à votre contrôle.</span><span class="sxs-lookup"><span data-stu-id="f7f2e-112">This creates a method that executes every time the `MyButton.Paint` event executes, thereby adding additional graphical representation to your control.</span></span> <span data-ttu-id="f7f2e-113">Notez que ceci n’empêche pas l’exécution de `MyButton.OnPaint`, et tout le dessin généralement effectué par un bouton est donc exécuté en plus de votre dessin personnalisé.</span><span class="sxs-lookup"><span data-stu-id="f7f2e-113">Note that this does not prevent the execution of `MyButton.OnPaint`, and thus all of the painting usually performed by a button will still be performed in addition to your custom painting.</span></span> <span data-ttu-id="f7f2e-114">Pour plus d’informations sur la technologie GDI+ et le rendu personnalisé, consultez [Création d’images graphiques avec GDI+](../../../../docs/framework/winforms/advanced/how-to-create-graphics-objects-for-drawing.md).</span><span class="sxs-lookup"><span data-stu-id="f7f2e-114">For details about GDI+ technology and custom rendering, see the [Creating Graphical Images with GDI+](../../../../docs/framework/winforms/advanced/how-to-create-graphics-objects-for-drawing.md).</span></span> <span data-ttu-id="f7f2e-115">Si vous voulez avoir une représentation unique de votre contrôle, le mieux est de créer un contrôle hérité et d’écrire pour celui-ci du code de rendu personnalisé.</span><span class="sxs-lookup"><span data-stu-id="f7f2e-115">If you wish to have a unique representation of your control, your best course of action is to create an inherited control, and to write custom rendering code for it.</span></span> <span data-ttu-id="f7f2e-116">Pour plus d’informations, consultez [Contrôles dessinés par l’utilisateur](../../../../docs/framework/winforms/controls/user-drawn-controls.md).</span><span class="sxs-lookup"><span data-stu-id="f7f2e-116">For details, see [User-Drawn Controls](../../../../docs/framework/winforms/controls/user-drawn-controls.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f7f2e-117">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="f7f2e-117">See Also</span></span>  
 <xref:System.Windows.Forms.UserControl>  
 <xref:System.Windows.Forms.Control.OnPaint%2A>  
 [<span data-ttu-id="f7f2e-118">Contrôles dessinés par l’utilisateur</span><span class="sxs-lookup"><span data-stu-id="f7f2e-118">User-Drawn Controls</span></span>](../../../../docs/framework/winforms/controls/user-drawn-controls.md)  
 [<span data-ttu-id="f7f2e-119">Guide pratique pour créer des objets graphiques pour le dessin</span><span class="sxs-lookup"><span data-stu-id="f7f2e-119">How to: Create Graphics Objects for Drawing</span></span>](../../../../docs/framework/winforms/advanced/how-to-create-graphics-objects-for-drawing.md)  
 [<span data-ttu-id="f7f2e-120">Variétés de contrôles personnalisés</span><span class="sxs-lookup"><span data-stu-id="f7f2e-120">Varieties of Custom Controls</span></span>](../../../../docs/framework/winforms/controls/varieties-of-custom-controls.md)
