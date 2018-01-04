---
title: "Comment : définir des taquets de tabulation dans du texte dessiné"
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
- text [Windows Forms], drawing with tab stops
- tabs [Windows Forms], drawn text
ms.assetid: 64878f98-39ba-4303-b63f-0859ab682eeb
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 2acc46a9a3fa2c84138cd9a168113f88ab08e4a6
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-set-tab-stops-in-drawn-text"></a><span data-ttu-id="0b223-102">Comment : définir des taquets de tabulation dans du texte dessiné</span><span class="sxs-lookup"><span data-stu-id="0b223-102">How to: Set Tab Stops in Drawn Text</span></span>
<span data-ttu-id="0b223-103">Vous pouvez définir des taquets de tabulation pour le texte en appelant le <xref:System.Drawing.StringFormat.SetTabStops%2A> méthode d’un <xref:System.Drawing.StringFormat> objet et en passant ensuite cet <xref:System.Drawing.StringFormat> de l’objet à la <xref:System.Drawing.Graphics.DrawString%2A> méthode de la <xref:System.Drawing.Graphics> classe.</span><span class="sxs-lookup"><span data-stu-id="0b223-103">You can set tab stops for text by calling the <xref:System.Drawing.StringFormat.SetTabStops%2A> method of a <xref:System.Drawing.StringFormat> object and then passing that <xref:System.Drawing.StringFormat> object to the <xref:System.Drawing.Graphics.DrawString%2A> method of the <xref:System.Drawing.Graphics> class.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="0b223-104">Le <xref:System.Windows.Forms.TextRenderer?displayProperty=nameWithType> fait pas en charge l’ajout des taquets de tabulation au texte dessiné, bien que vous pouvez développer onglet existant s’arrête à l’aide de la <xref:System.Windows.Forms.TextFormatFlags.ExpandTabs?displayProperty=nameWithType> indicateur.</span><span class="sxs-lookup"><span data-stu-id="0b223-104">The <xref:System.Windows.Forms.TextRenderer?displayProperty=nameWithType> does not support adding tab stops to drawn text, although you can expand existing tab stops using the <xref:System.Windows.Forms.TextFormatFlags.ExpandTabs?displayProperty=nameWithType> flag.</span></span>  
  
## <a name="example"></a><span data-ttu-id="0b223-105">Exemple</span><span class="sxs-lookup"><span data-stu-id="0b223-105">Example</span></span>  
 <span data-ttu-id="0b223-106">L’exemple suivant définit des taquets de tabulation à 150, 250 et 350.</span><span class="sxs-lookup"><span data-stu-id="0b223-106">The following example sets tab stops at 150, 250, and 350.</span></span> <span data-ttu-id="0b223-107">Ensuite, le code affiche une liste avec onglets des noms et des scores de test.</span><span class="sxs-lookup"><span data-stu-id="0b223-107">Then, the code displays a tabbed list of names and test scores.</span></span>  
  
 <span data-ttu-id="0b223-108">L’illustration suivante montre le texte à onglets.</span><span class="sxs-lookup"><span data-stu-id="0b223-108">The following illustration shows the tabbed text.</span></span>  
  
 <span data-ttu-id="0b223-109">![Polices du texte](../../../../docs/framework/winforms/advanced/media/fontstext4.png "fontstext4")</span><span class="sxs-lookup"><span data-stu-id="0b223-109">![Fonts Text](../../../../docs/framework/winforms/advanced/media/fontstext4.png "fontstext4")</span></span>  
  
 <span data-ttu-id="0b223-110">Le code suivant passe deux arguments à la <xref:System.Drawing.StringFormat.SetTabStops%2A> (méthode).</span><span class="sxs-lookup"><span data-stu-id="0b223-110">The following code passes two arguments to the <xref:System.Drawing.StringFormat.SetTabStops%2A> method.</span></span> <span data-ttu-id="0b223-111">Le deuxième argument est un tableau qui contient les offsets de tabulation.</span><span class="sxs-lookup"><span data-stu-id="0b223-111">The second argument is an array that contains tab offsets.</span></span> <span data-ttu-id="0b223-112">Le premier argument passé à <xref:System.Drawing.StringFormat.SetTabStops%2A> est 0, ce qui indique que le premier offset dans le tableau est mesuré à partir de la position 0, le bord gauche du rectangle englobant.</span><span class="sxs-lookup"><span data-stu-id="0b223-112">The first argument passed to <xref:System.Drawing.StringFormat.SetTabStops%2A> is 0, which indicates that the first offset in the array is measured from position 0, the left edge of the bounding rectangle.</span></span>  
  
 [!code-csharp[System.Drawing.FontsAndText#41](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.FontsAndText/CS/Class1.cs#41)]
 [!code-vb[System.Drawing.FontsAndText#41](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.FontsAndText/VB/Class1.vb#41)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="0b223-113">Compilation du code</span><span class="sxs-lookup"><span data-stu-id="0b223-113">Compiling the Code</span></span>  
  
-   <span data-ttu-id="0b223-114">L'exemple précédent est conçu pour une utilisation avec Windows Forms et nécessite <xref:System.Windows.Forms.PaintEventArgs> `e`, qui est un paramètre de <xref:System.Windows.Forms.PaintEventHandler>.</span><span class="sxs-lookup"><span data-stu-id="0b223-114">The preceding example is designed for use with Windows Forms, and it requires <xref:System.Windows.Forms.PaintEventArgs> `e`, which is a parameter of <xref:System.Windows.Forms.PaintEventHandler>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0b223-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="0b223-115">See Also</span></span>  
 [<span data-ttu-id="0b223-116">Utilisation de polices et de texte</span><span class="sxs-lookup"><span data-stu-id="0b223-116">Using Fonts and Text</span></span>](../../../../docs/framework/winforms/advanced/using-fonts-and-text.md)  
 [<span data-ttu-id="0b223-117">Guide pratique pour écrire du texte avec GDI</span><span class="sxs-lookup"><span data-stu-id="0b223-117">How to: Draw Text with GDI</span></span>](../../../../docs/framework/winforms/advanced/how-to-draw-text-with-gdi.md)
