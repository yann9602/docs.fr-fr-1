---
title: "Comment : effacer l'encre sur un contrôle personnalisé"
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
- custom controls [WPF], erasing ink on
- ink [WPF], erasing on custom control
ms.assetid: d88c50f9-b4d8-4962-a28b-67d6a15a5fe0
caps.latest.revision: "4"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: e05163bcbafd360e0929fe784ff1111bd0663ef3
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-erase-ink-on-a-custom-control"></a><span data-ttu-id="cf945-102">Comment : effacer l'encre sur un contrôle personnalisé</span><span class="sxs-lookup"><span data-stu-id="cf945-102">How to: Erase Ink on a Custom Control</span></span>
<span data-ttu-id="cf945-103">Le <xref:System.Windows.Ink.IncrementalStrokeHitTester> détermine si le trait dessiné entre en intersection avec un autre trait.</span><span class="sxs-lookup"><span data-stu-id="cf945-103">The <xref:System.Windows.Ink.IncrementalStrokeHitTester> determines whether the currently drawn stroke intersects another stroke.</span></span>  <span data-ttu-id="cf945-104">Cela est utile pour la création d’un contrôle qui permet à un utilisateur d’effacer certaines parties d’un trait, la méthode peut d’un utilisateur sur un <xref:System.Windows.Controls.InkCanvas> lors de la <xref:System.Windows.Controls.InkCanvas.EditingMode%2A> a la valeur <xref:System.Windows.Controls.InkCanvasEditingMode.EraseByPoint>.</span><span class="sxs-lookup"><span data-stu-id="cf945-104">This is useful for creating a control that enables a user to erase parts of a stroke, the way a user can on an <xref:System.Windows.Controls.InkCanvas> when the <xref:System.Windows.Controls.InkCanvas.EditingMode%2A> is set to <xref:System.Windows.Controls.InkCanvasEditingMode.EraseByPoint>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="cf945-105">Exemple</span><span class="sxs-lookup"><span data-stu-id="cf945-105">Example</span></span>  
 <span data-ttu-id="cf945-106">L’exemple suivant crée un contrôle personnalisé qui permet à l’utilisateur d’effacer certaines parties des traits.</span><span class="sxs-lookup"><span data-stu-id="cf945-106">The following example creates a custom control that enables the user to erase parts of strokes.</span></span>  <span data-ttu-id="cf945-107">Cet exemple crée un contrôle qui contient une entrée lorsqu’il est initialisé.</span><span class="sxs-lookup"><span data-stu-id="cf945-107">This example creates a control that contains ink when it is initialized.</span></span>  <span data-ttu-id="cf945-108">Pour créer un contrôle qui collecte de l’encre, consultez [création d’un contrôle d’entrée manuscrite](../../../../docs/framework/wpf/advanced/creating-an-ink-input-control.md).</span><span class="sxs-lookup"><span data-stu-id="cf945-108">To create a control that collects ink, see [Creating an Ink Input Control](../../../../docs/framework/wpf/advanced/creating-an-ink-input-control.md).</span></span>  
  
 [!code-csharp[HowToEraseInk#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HowToEraseInk/CSharp/InkEraser.cs#1)]
 [!code-vb[HowToEraseInk#1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/HowToEraseInk/VisualBasic/InkEraser.vb#1)]
