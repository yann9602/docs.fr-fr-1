---
title: "Comment : exposer les propriétés des contrôles constitutifs"
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
- user controls [Windows Forms], exposing constituent controls
- controls [Windows Forms], constituent
- custom controls [Windows Forms], exposing properties
- constituent controls
ms.assetid: 5c1ec98b-aa48-4823-986e-4712551cfdf1
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: a970864a406f98477fa3e09bdefcf959d2078fe6
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-expose-properties-of-constituent-controls"></a><span data-ttu-id="60ad1-102">Comment : exposer les propriétés des contrôles constitutifs</span><span class="sxs-lookup"><span data-stu-id="60ad1-102">How to: Expose Properties of Constituent Controls</span></span>
<span data-ttu-id="60ad1-103">Les contrôles qui composent un contrôle composite sont appelés *contrôles constitutifs*.</span><span class="sxs-lookup"><span data-stu-id="60ad1-103">The controls that make up a composite control are called *constituent controls*.</span></span> <span data-ttu-id="60ad1-104">Ces contrôles sont normalement déclarés privés et donc ne peut pas être accessible par le développeur.</span><span class="sxs-lookup"><span data-stu-id="60ad1-104">These controls are normally declared private, and thus cannot be accessed by the developer.</span></span> <span data-ttu-id="60ad1-105">Si vous souhaitez rendre les propriétés de ces contrôles accessibles aux utilisateurs de futures, vous devez les exposer à l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="60ad1-105">If you want to make properties of these controls available to future users, you must expose them to the user.</span></span> <span data-ttu-id="60ad1-106">Une propriété d’un contrôle qui le composent est exposée par la création d’une propriété dans le contrôle utilisateur et à l’aide de la `get` et `set` accesseurs pour répercuter la modification dans la propriété privée du contrôle constitutif.</span><span class="sxs-lookup"><span data-stu-id="60ad1-106">A property of a constituent control is exposed by creating a property in the user control, and using the `get` and `set` accessors of that property to effect the change in the private property of the constituent control.</span></span>  
  
 <span data-ttu-id="60ad1-107">Considérez un contrôle utilisateur hypothétique avec un bouton constitutif appelé `MyButton`.</span><span class="sxs-lookup"><span data-stu-id="60ad1-107">Consider a hypothetical user control with a constituent button named `MyButton`.</span></span> <span data-ttu-id="60ad1-108">Dans cet exemple, lorsque l’utilisateur demande la `ConstituentButtonBackColor` propriété, la valeur stockée dans le <xref:System.Windows.Forms.Control.BackColor%2A> propriété du `MyButton` est remis.</span><span class="sxs-lookup"><span data-stu-id="60ad1-108">In this example, when the user requests the `ConstituentButtonBackColor` property, the value stored in the <xref:System.Windows.Forms.Control.BackColor%2A> property of `MyButton` is delivered.</span></span> <span data-ttu-id="60ad1-109">Lorsque l’utilisateur assigne une valeur à cette propriété, cette valeur est automatiquement passée à la <xref:System.Windows.Forms.Control.BackColor%2A> propriété du `MyButton` et `set` code s’exécutera, changez la couleur du `MyButton`.</span><span class="sxs-lookup"><span data-stu-id="60ad1-109">When the user assigns a value to this property, that value is automatically passed to the <xref:System.Windows.Forms.Control.BackColor%2A> property of `MyButton` and the `set` code will execute, changing the color of `MyButton`.</span></span>  
  
 <span data-ttu-id="60ad1-110">L’exemple suivant montre comment exposer le <xref:System.Windows.Forms.Control.BackColor%2A> propriété du bouton constitutif :</span><span class="sxs-lookup"><span data-stu-id="60ad1-110">The following example shows how to expose the <xref:System.Windows.Forms.Control.BackColor%2A> property of the constituent button:</span></span>  
  
```vb  
Public Property ButtonColor() as System.Drawing.Color  
   Get  
      Return MyButton.BackColor  
   End Get  
   Set(Value as System.Drawing.Color)  
      MyButton.BackColor = Value  
   End Set  
End Property  
```  
  
```csharp  
public Color ButtonColor  
{  
   get  
   {  
      return(myButton.BackColor);  
   }  
   set  
   {  
      myButton.BackColor = value;  
   }  
}  
```  
  
### <a name="to-expose-a-property-of-a-constituent-control"></a><span data-ttu-id="60ad1-111">Pour exposer une propriété d’un contrôle qui le composent</span><span class="sxs-lookup"><span data-stu-id="60ad1-111">To expose a property of a constituent control</span></span>  
  
1.  <span data-ttu-id="60ad1-112">Créez une propriété publique pour votre contrôle utilisateur.</span><span class="sxs-lookup"><span data-stu-id="60ad1-112">Create a public property for your user control.</span></span>  
  
2.  <span data-ttu-id="60ad1-113">Dans la `get` section de la propriété, écrire du code qui Récupère la valeur de la propriété que vous souhaitez exposer.</span><span class="sxs-lookup"><span data-stu-id="60ad1-113">In the `get` section of the property, write code that retrieves the value of the property you want to expose.</span></span>  
  
3.  <span data-ttu-id="60ad1-114">Dans la `set` section de la propriété, écrire du code qui transmet la valeur de la propriété à la propriété exposée du contrôle constitutif.</span><span class="sxs-lookup"><span data-stu-id="60ad1-114">In the `set` section of the property, write code that passes the value of the property to the exposed property of the constituent control.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="60ad1-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="60ad1-115">See Also</span></span>  
 <xref:System.Windows.Forms.UserControl>  
 [<span data-ttu-id="60ad1-116">Propriétés dans les contrôles Windows Forms</span><span class="sxs-lookup"><span data-stu-id="60ad1-116">Properties in Windows Forms Controls</span></span>](../../../../docs/framework/winforms/controls/properties-in-windows-forms-controls.md)  
 [<span data-ttu-id="60ad1-117">Variétés de contrôles personnalisés</span><span class="sxs-lookup"><span data-stu-id="60ad1-117">Varieties of Custom Controls</span></span>](../../../../docs/framework/winforms/controls/varieties-of-custom-controls.md)
