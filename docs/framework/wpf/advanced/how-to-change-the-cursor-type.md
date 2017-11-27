---
title: "Comment : modifier le type de curseur"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- mouse pointer [WPF], cursor type
- cursor (mouse pointer)
ms.assetid: 08c945a7-8ab0-4320-acf3-0b4955a344c2
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 41cd8c9cd647c7efbc4e6cf13517ed638245e51c
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/22/2017
---
# <a name="how-to-change-the-cursor-type"></a><span data-ttu-id="07fdc-102">Comment : modifier le type de curseur</span><span class="sxs-lookup"><span data-stu-id="07fdc-102">How to: Change the Cursor Type</span></span>
<span data-ttu-id="07fdc-103">Cet exemple montre comment modifier le <xref:System.Windows.Input.Cursor> du pointeur de la souris pour un élément spécifique et pour l’application.</span><span class="sxs-lookup"><span data-stu-id="07fdc-103">This example shows how to change the <xref:System.Windows.Input.Cursor> of the mouse pointer for a specific element and for the application.</span></span>  
  
 <span data-ttu-id="07fdc-104">Cet exemple se compose d’un [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] de fichiers et un fichier code-behind.</span><span class="sxs-lookup"><span data-stu-id="07fdc-104">This example consists of a [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] file and a code behind file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="07fdc-105">Exemple</span><span class="sxs-lookup"><span data-stu-id="07fdc-105">Example</span></span>  
 <span data-ttu-id="07fdc-106">L’interface utilisateur est créé, qui se compose d’un <xref:System.Windows.Controls.ComboBox> pour sélectionner l’élément <xref:System.Windows.Input.Cursor>, une paire de <xref:System.Windows.Controls.RadioButton> objets afin de déterminer si la modification de curseur s’applique à un seul élément ou qu’elle s’applique à l’application entière et un <xref:System.Windows.Controls.Border> qui est l’élément du nouveau curseur est appliqué à.</span><span class="sxs-lookup"><span data-stu-id="07fdc-106">The user interface is created, which consists of a <xref:System.Windows.Controls.ComboBox> to select the desired <xref:System.Windows.Input.Cursor>, a pair of <xref:System.Windows.Controls.RadioButton> objects to determine if the cursor change applies to only a single element or applies to the entire application, and a <xref:System.Windows.Controls.Border> which is the element that the new cursor is applied to.</span></span>  
  
 [!code-xaml[cursors#ChangeCursorsXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/cursors/CSharp/Window1.xaml#changecursorsxaml)]  
  
 <span data-ttu-id="07fdc-107">Le code-behind suivant crée un <xref:System.Windows.Controls.Primitives.Selector.SelectionChanged> Gestionnaire d’événements qui est appelé lorsque le type de curseur a changé dans le <xref:System.Windows.Controls.ComboBox>.</span><span class="sxs-lookup"><span data-stu-id="07fdc-107">The following code behind creates a <xref:System.Windows.Controls.Primitives.Selector.SelectionChanged> event handler which is called when the cursor type is changed in the <xref:System.Windows.Controls.ComboBox>.</span></span>  <span data-ttu-id="07fdc-108">Une instruction switch filtre sur le nom de curseur et définit la <xref:System.Windows.FrameworkElement.Cursor%2A> propriété sur le <xref:System.Windows.Controls.Border> nommé *DisplayArea*.</span><span class="sxs-lookup"><span data-stu-id="07fdc-108">A switch statement filters on the cursor name and sets the <xref:System.Windows.FrameworkElement.Cursor%2A> property on the <xref:System.Windows.Controls.Border> which is named *DisplayArea*.</span></span>  
  
 <span data-ttu-id="07fdc-109">Si la modification de curseur est définie sur « Application entière », le <xref:System.Windows.Input.Mouse.OverrideCursor%2A> est définie sur le <xref:System.Windows.FrameworkElement.Cursor%2A> propriété de la <xref:System.Windows.Controls.Border> contrôle.</span><span class="sxs-lookup"><span data-stu-id="07fdc-109">If the cursor change is set to "Entire Application", the <xref:System.Windows.Input.Mouse.OverrideCursor%2A> property is set to the <xref:System.Windows.FrameworkElement.Cursor%2A> property of the <xref:System.Windows.Controls.Border> control.</span></span>  <span data-ttu-id="07fdc-110">Cela force le curseur à modifier pour toute l’application.</span><span class="sxs-lookup"><span data-stu-id="07fdc-110">This forces the cursor to change for the whole application.</span></span>  
  
 [!code-csharp[cursors#ChangeCursorsSample](../../../../samples/snippets/csharp/VS_Snippets_Wpf/cursors/CSharp/Window1.xaml.cs#changecursorssample)]
 [!code-vb[cursors#ChangeCursorsSample](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/cursors/VisualBasic/Window1.xaml.vb#changecursorssample)]  
  
## <a name="see-also"></a><span data-ttu-id="07fdc-111">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="07fdc-111">See Also</span></span>  
 [<span data-ttu-id="07fdc-112">Vue d’ensemble des entrées</span><span class="sxs-lookup"><span data-stu-id="07fdc-112">Input Overview</span></span>](../../../../docs/framework/wpf/advanced/input-overview.md)
