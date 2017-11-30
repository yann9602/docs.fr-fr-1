---
title: "Comment : détecter la modification du texte figurant dans un TextBox"
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
- TextBox control [WPF], detecting text change
- text change [WPF], detecting
- detecting text change [WPF]
ms.assetid: 1c39ee14-e37f-49fb-a0d1-a9824ca13584
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 92fc8995ab75cc25bac3bb21b1646052822c3721
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-detect-when-text-in-a-textbox-has-changed"></a><span data-ttu-id="b2d12-102">Comment : détecter la modification du texte figurant dans un TextBox</span><span class="sxs-lookup"><span data-stu-id="b2d12-102">How to: Detect When Text in a TextBox Has Changed</span></span>
<span data-ttu-id="b2d12-103">Cet exemple montre une manière d’utiliser la <xref:System.Windows.Controls.Primitives.TextBoxBase.TextChanged> événement pour exécuter une méthode chaque fois que le texte dans un <xref:System.Windows.Controls.TextBox> contrôle a changé.</span><span class="sxs-lookup"><span data-stu-id="b2d12-103">This example shows one way to use the <xref:System.Windows.Controls.Primitives.TextBoxBase.TextChanged> event to execute a method whenever the text in a <xref:System.Windows.Controls.TextBox> control has changed.</span></span>  
  
 <span data-ttu-id="b2d12-104">Dans la classe code-behind pour la [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] qui contient le <xref:System.Windows.Controls.TextBox> contrôle que vous souhaitez analyser pour les modifications, insérez une méthode à appeler lorsque le <xref:System.Windows.Controls.Primitives.TextBoxBase.TextChanged> se déclenche des événements.</span><span class="sxs-lookup"><span data-stu-id="b2d12-104">In the code-behind class for the [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] that contains the <xref:System.Windows.Controls.TextBox> control that you want to monitor for changes, insert a method to call whenever the <xref:System.Windows.Controls.Primitives.TextBoxBase.TextChanged> event fires.</span></span>  <span data-ttu-id="b2d12-105">Cette méthode doit avoir une signature qui correspond à celle attendue par le <xref:System.Windows.Controls.TextChangedEventHandler> déléguer.</span><span class="sxs-lookup"><span data-stu-id="b2d12-105">This method must have a signature that matches what is expected by the <xref:System.Windows.Controls.TextChangedEventHandler> delegate.</span></span>  
  
 <span data-ttu-id="b2d12-106">Le Gestionnaire d’événements est appelé chaque fois que le contenu de la <xref:System.Windows.Controls.TextBox> contrôle sont modifiés par un utilisateur ou par programme.</span><span class="sxs-lookup"><span data-stu-id="b2d12-106">The event handler is called whenever the contents of the <xref:System.Windows.Controls.TextBox> control are changed, either by a user or programmatically.</span></span>  
  
 <span data-ttu-id="b2d12-107">**Remarque :** cet événement déclenche lorsque la <xref:System.Windows.Controls.TextBox> contrôle est créée et remplie initialement avec le texte.</span><span class="sxs-lookup"><span data-stu-id="b2d12-107">**Note:** This event fires when the <xref:System.Windows.Controls.TextBox> control is created and initially populated with text.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b2d12-108">Exemple</span><span class="sxs-lookup"><span data-stu-id="b2d12-108">Example</span></span>  
 <span data-ttu-id="b2d12-109">Dans le [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] qui définit votre <xref:System.Windows.Controls.TextBox> contrôler, spécifiez la <xref:System.Windows.Controls.Primitives.TextBoxBase.TextChanged> attribut avec une valeur qui correspond au nom méthode du Gestionnaire d’événements.</span><span class="sxs-lookup"><span data-stu-id="b2d12-109">In the [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] that defines your <xref:System.Windows.Controls.TextBox> control, specify the <xref:System.Windows.Controls.Primitives.TextBoxBase.TextChanged> attribute with a value that matches the event handler method name.</span></span>  
  
 [!code-xaml[TextBox_MiscCode#_TextChangedXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextBox_MiscCode/CSharp/Window1.xaml#_textchangedxaml)]  
  
## <a name="example"></a><span data-ttu-id="b2d12-110">Exemple</span><span class="sxs-lookup"><span data-stu-id="b2d12-110">Example</span></span>  
 <span data-ttu-id="b2d12-111">Dans la classe code-behind pour la [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] qui contient le <xref:System.Windows.Controls.TextBox> contrôle que vous souhaitez analyser pour les modifications, insérez une méthode à appeler lorsque le <xref:System.Windows.Controls.Primitives.TextBoxBase.TextChanged> se déclenche des événements.</span><span class="sxs-lookup"><span data-stu-id="b2d12-111">In the code-behind class for the [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] that contains the <xref:System.Windows.Controls.TextBox> control that you want to monitor for changes, insert a method to call whenever the <xref:System.Windows.Controls.Primitives.TextBoxBase.TextChanged> event fires.</span></span>  <span data-ttu-id="b2d12-112">Cette méthode doit avoir une signature qui correspond à celle attendue par le <xref:System.Windows.Controls.TextChangedEventHandler> déléguer.</span><span class="sxs-lookup"><span data-stu-id="b2d12-112">This method must have a signature that matches what is expected by the <xref:System.Windows.Controls.TextChangedEventHandler> delegate.</span></span>  
  
 [!code-csharp[TextBox_MiscCode#_TextChangedEventHandler](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextBox_MiscCode/CSharp/Window1.xaml.cs#_textchangedeventhandler)]
 [!code-vb[TextBox_MiscCode#_TextChangedEventHandler](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/TextBox_MiscCode/VisualBasic/Window1.xaml.vb#_textchangedeventhandler)]  
  
 <span data-ttu-id="b2d12-113">Le Gestionnaire d’événements est appelé chaque fois que le contenu de la <xref:System.Windows.Controls.TextBox> contrôle sont modifiés par un utilisateur ou par programme.</span><span class="sxs-lookup"><span data-stu-id="b2d12-113">The event handler is called whenever the contents of the <xref:System.Windows.Controls.TextBox> control are changed, either by a user or programmatically.</span></span>  
  
 <span data-ttu-id="b2d12-114">**Remarque :** cet événement déclenche lorsque la <xref:System.Windows.Controls.TextBox> contrôle est créée et remplie initialement avec le texte.</span><span class="sxs-lookup"><span data-stu-id="b2d12-114">**Note:** This event fires when the <xref:System.Windows.Controls.TextBox> control is created and initially populated with text.</span></span>  
  
 <span data-ttu-id="b2d12-115">Commentaires</span><span class="sxs-lookup"><span data-stu-id="b2d12-115">Comments</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b2d12-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="b2d12-116">See Also</span></span>  
 <xref:System.Windows.Controls.TextChangedEventArgs>  
 [<span data-ttu-id="b2d12-117">Vue d’ensemble de TextBox</span><span class="sxs-lookup"><span data-stu-id="b2d12-117">TextBox Overview</span></span>](../../../../docs/framework/wpf/controls/textbox-overview.md)  
 [<span data-ttu-id="b2d12-118">Vue d’ensemble de RichTextBox</span><span class="sxs-lookup"><span data-stu-id="b2d12-118">RichTextBox Overview</span></span>](../../../../docs/framework/wpf/controls/richtextbox-overview.md)
