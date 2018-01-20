---
title: "Comment : identifier la touche de modification activée"
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
- keyboard input
- shift keys
- events [Windows Forms], mouse
- Keys.ControlKey enumeration member
- keys [Windows Forms], control keys
- user input [Windows Forms], checking for keyboard
- keys [Windows Forms], determining last pressed
- keys [Windows Forms], shift keys
- keys [Windows Forms], modifier keys
- control keys
- keys [Windows Forms], alt keys
- alt keys
- Keys.Shift enumeration member
- events [Windows Forms], keyboard
- keyboards [Windows Forms], keyboard input
- Keys.Alt enumeration member
- modifier keys
ms.assetid: 1e184048-0ae3-4067-a200-d4ba31dbc2cb
caps.latest.revision: "16"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: d5f749d22c09d166e81ea08068f760f24960ec83
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/19/2018
---
# <a name="how-to-determine-which-modifier-key-was-pressed"></a><span data-ttu-id="af6e7-102">Comment : identifier la touche de modification activée</span><span class="sxs-lookup"><span data-stu-id="af6e7-102">How to: Determine Which Modifier Key Was Pressed</span></span>
<span data-ttu-id="af6e7-103">Lorsque vous créez une application qui accepte les séquences de touches de l’utilisateur, vous pouvez souhaiter également surveiller les touches de modification telles que les touches MAJ, ALT ou CTRL.</span><span class="sxs-lookup"><span data-stu-id="af6e7-103">When you create an application that accepts the user's keystrokes, you may also want to monitor for modifier keys such as the SHIFT, ALT, and CTRL keys.</span></span> <span data-ttu-id="af6e7-104">Lorsqu’une touche de modification est enfoncée en combinaison avec d’autres clés ou avec des clics de souris, votre application peut répondre de manière appropriée.</span><span class="sxs-lookup"><span data-stu-id="af6e7-104">When a modifier key is pressed in combination with other keys, or with mouse clicks, your application can respond appropriately.</span></span> <span data-ttu-id="af6e7-105">Par exemple, si l’utilisateur appuie sur la lettre S, cela peut simplement entraîner un « s » à afficher sur l’écran, mais si les touches CTRL + S sont utilisées, le document actif peut être enregistré.</span><span class="sxs-lookup"><span data-stu-id="af6e7-105">For example, if the letter S is pressed, this may simply cause an "s" to appear on the screen, but if the keys CTRL+S are pressed, the current document may be saved.</span></span> <span data-ttu-id="af6e7-106">Si vous gérez le <xref:System.Windows.Forms.Control.KeyDown> événement, le <xref:System.Windows.Forms.KeyEventArgs.Modifiers%2A> propriété de la <xref:System.Windows.Forms.KeyEventArgs> reçu par l’événement gestionnaire spécifie les touches de modification sont enfoncés.</span><span class="sxs-lookup"><span data-stu-id="af6e7-106">If you handle the <xref:System.Windows.Forms.Control.KeyDown> event, the <xref:System.Windows.Forms.KeyEventArgs.Modifiers%2A> property of the <xref:System.Windows.Forms.KeyEventArgs> received by the event handler specifies which modifier keys are pressed.</span></span> <span data-ttu-id="af6e7-107">Vous pouvez également le <xref:System.Windows.Forms.KeyEventArgs.KeyData%2A> propriété du <xref:System.Windows.Forms.KeyEventArgs> Spécifie le caractère qui a été enfoncé, ainsi que les touches de modification combinées avec une opération OR au niveau du bit.</span><span class="sxs-lookup"><span data-stu-id="af6e7-107">Alternatively, the <xref:System.Windows.Forms.KeyEventArgs.KeyData%2A> property of <xref:System.Windows.Forms.KeyEventArgs> specifies the character that was pressed as well as any modifier keys combined with a bitwise OR.</span></span> <span data-ttu-id="af6e7-108">Toutefois, si vous gérez le <xref:System.Windows.Forms.Control.KeyPress> événement ou un événement de souris, le Gestionnaire d’événements ne reçoit pas ces informations.</span><span class="sxs-lookup"><span data-stu-id="af6e7-108">However, if you are handling the <xref:System.Windows.Forms.Control.KeyPress> event or a mouse event, the event handler does not receive this information.</span></span> <span data-ttu-id="af6e7-109">Dans ce cas, vous devez utiliser le <xref:System.Windows.Forms.Control.ModifierKeys%2A> propriété de la <xref:System.Windows.Forms.Control> classe.</span><span class="sxs-lookup"><span data-stu-id="af6e7-109">In this case, you must use the <xref:System.Windows.Forms.Control.ModifierKeys%2A> property of the <xref:System.Windows.Forms.Control> class.</span></span> <span data-ttu-id="af6e7-110">Dans les deux cas, vous devez effectuer une opération AND au niveau du bit d’approprié <xref:System.Windows.Forms.Keys> valeur et la valeur que vous testez.</span><span class="sxs-lookup"><span data-stu-id="af6e7-110">In either case, you must perform a bitwise AND of the appropriate <xref:System.Windows.Forms.Keys> value and the value you are testing.</span></span> <span data-ttu-id="af6e7-111">Le <xref:System.Windows.Forms.Keys> énumération offre des variations de chaque touche de modification, il est important d’effectuer les opérations de bits et avec la valeur correcte.</span><span class="sxs-lookup"><span data-stu-id="af6e7-111">The <xref:System.Windows.Forms.Keys> enumeration offers variations of each modifier key, so it is important that you perform the bitwise AND with the correct value.</span></span> <span data-ttu-id="af6e7-112">Par exemple, la touche MAJ est représentée par <xref:System.Windows.Forms.Keys.Shift>, <xref:System.Windows.Forms.Keys.ShiftKey>, <xref:System.Windows.Forms.Keys.RShiftKey> et <xref:System.Windows.Forms.Keys.LShiftKey> la valeur correcte pour tester MAJ comme une touche de modification est <xref:System.Windows.Forms.Keys.Shift>.</span><span class="sxs-lookup"><span data-stu-id="af6e7-112">For example, the SHIFT key is represented by <xref:System.Windows.Forms.Keys.Shift>, <xref:System.Windows.Forms.Keys.ShiftKey>, <xref:System.Windows.Forms.Keys.RShiftKey> and <xref:System.Windows.Forms.Keys.LShiftKey> The correct value to test SHIFT as a modifier key is <xref:System.Windows.Forms.Keys.Shift>.</span></span> <span data-ttu-id="af6e7-113">De même, pour tester le CTLR et ALT comme modificateurs vous devez utiliser le <xref:System.Windows.Forms.Keys.Control> et <xref:System.Windows.Forms.Keys.Alt> valeurs, respectivement.</span><span class="sxs-lookup"><span data-stu-id="af6e7-113">Similarly, to test for CTLR and ALT as modifiers you should use the <xref:System.Windows.Forms.Keys.Control> and <xref:System.Windows.Forms.Keys.Alt> values, respectively.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="af6e7-114">Les programmeurs Visual Basic peuvent également accéder à des informations de clé par le biais du <xref:Microsoft.VisualBasic.Devices.Computer.Keyboard%2A> propriété</span><span class="sxs-lookup"><span data-stu-id="af6e7-114">Visual Basic programmers can also access key information through the <xref:Microsoft.VisualBasic.Devices.Computer.Keyboard%2A> property</span></span>  
  
### <a name="to-determine-which-modifier-key-was-pressed"></a><span data-ttu-id="af6e7-115">Pour déterminer quelle touche de modification activée</span><span class="sxs-lookup"><span data-stu-id="af6e7-115">To determine which modifier key was pressed</span></span>  
  
-   <span data-ttu-id="af6e7-116">Utilisez l’opérateur de bits `AND` opérateur avec la <xref:System.Windows.Forms.Control.ModifierKeys%2A> propriété et une valeur de la <xref:System.Windows.Forms.Keys> énumération pour déterminer si une touche de modification spécifique est utilisée.</span><span class="sxs-lookup"><span data-stu-id="af6e7-116">Use the bitwise `AND` operator with the <xref:System.Windows.Forms.Control.ModifierKeys%2A> property and a value of the <xref:System.Windows.Forms.Keys> enumeration to determine whether a particular modifier key is pressed.</span></span> <span data-ttu-id="af6e7-117">L’exemple de code suivant montre comment déterminer si la touche MAJ est activée dans un <xref:System.Windows.Forms.Control.KeyPress> Gestionnaire d’événements.</span><span class="sxs-lookup"><span data-stu-id="af6e7-117">The following code example shows how to determine whether the SHIFT key is pressed within a <xref:System.Windows.Forms.Control.KeyPress> event handler.</span></span>  
  
     [!code-cpp[System.Windows.Forms.DetermineModifierKey#5](../../../samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DetermineModifierKey/cpp/form1.cpp#5)]
     [!code-csharp[System.Windows.Forms.DetermineModifierKey#5](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DetermineModifierKey/CS/form1.cs#5)]
     [!code-vb[System.Windows.Forms.DetermineModifierKey#5](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DetermineModifierKey/VB/form1.vb#5)]  
  
## <a name="see-also"></a><span data-ttu-id="af6e7-118">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="af6e7-118">See Also</span></span>  
 <xref:System.Windows.Forms.Keys>  
 <xref:System.Windows.Forms.Control.ModifierKeys%2A>  
 [<span data-ttu-id="af6e7-119">Entrée au clavier dans une application Windows Forms</span><span class="sxs-lookup"><span data-stu-id="af6e7-119">Keyboard Input in a Windows Forms Application</span></span>](../../../docs/framework/winforms/keyboard-input-in-a-windows-forms-application.md)  
 [<span data-ttu-id="af6e7-120">Comment : déterminer si la touche VERR. MAJ. est activée dans Visual Basic</span><span class="sxs-lookup"><span data-stu-id="af6e7-120">How to: Determine If CapsLock is On in Visual Basic</span></span>](http://msdn.microsoft.com/library/91e60f5c-dd61-4222-ba5f-39af803afd8c)
