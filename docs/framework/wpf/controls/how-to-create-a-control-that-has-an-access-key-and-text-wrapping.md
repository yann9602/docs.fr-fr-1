---
title: "Comment : créer un contrôle avec touche d'accès rapide et habillage du texte"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- access keys [WPF], control for
- controls [WPF], text wrapping
- wrapping text [WPF]
- keys [WPF], control for
- controls [WPF], access keys
- text wrapping [WPF]
ms.assetid: 205099d9-2551-4302-a25e-a15af9f67e04
caps.latest.revision: "22"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 2a759011425a3f09a7b91b728442f8e8ea7b92fa
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/22/2017
---
# <a name="how-to-create-a-control-that-has-an-access-key-and-text-wrapping"></a><span data-ttu-id="1bb42-102">Comment : créer un contrôle avec touche d'accès rapide et habillage du texte</span><span class="sxs-lookup"><span data-stu-id="1bb42-102">How to: Create a Control That Has an Access Key and Text Wrapping</span></span>
<span data-ttu-id="1bb42-103">Cet exemple montre comment créer un contrôle avec touche d’accès rapide, prenant en charge l’habillage du texte.</span><span class="sxs-lookup"><span data-stu-id="1bb42-103">This example shows how to create a control that has an access key and supports text wrapping.</span></span> <span data-ttu-id="1bb42-104">L’exemple utilise un <xref:System.Windows.Controls.Label> contrôle pour illustrer ces concepts.</span><span class="sxs-lookup"><span data-stu-id="1bb42-104">The example uses a <xref:System.Windows.Controls.Label> control to illustrate these concepts.</span></span>  
  
## <a name="example"></a><span data-ttu-id="1bb42-105">Exemple</span><span class="sxs-lookup"><span data-stu-id="1bb42-105">Example</span></span>  
 <span data-ttu-id="1bb42-106">**Ajouter l’habillage du texte à votre étiquette**</span><span class="sxs-lookup"><span data-stu-id="1bb42-106">**Add Text Wrapping to Your Label**</span></span>  
  
 <span data-ttu-id="1bb42-107">Le <xref:System.Windows.Controls.Label> contrôle ne prend pas en charge l’habillage du texte.</span><span class="sxs-lookup"><span data-stu-id="1bb42-107">The <xref:System.Windows.Controls.Label> control does not support text wrapping.</span></span> <span data-ttu-id="1bb42-108">Si vous avez besoin d’une étiquette couvrant plusieurs lignes, vous pouvez imbriquer un autre élément qui prend en charge l’habillage du texte d’habillage et le placer dans l’étiquette.</span><span class="sxs-lookup"><span data-stu-id="1bb42-108">If you need a label that wraps across multiple lines, you can nest another element that does support text wrapping and put the element inside the label.</span></span> <span data-ttu-id="1bb42-109">L’exemple suivant montre comment utiliser un <xref:System.Windows.Controls.TextBlock> pour faire une étiquette couvrant plusieurs lignes de texte.</span><span class="sxs-lookup"><span data-stu-id="1bb42-109">The following example shows how to use a <xref:System.Windows.Controls.TextBlock> to make a label that wraps several lines of text.</span></span>  
  
 [!code-xaml[LabelSnippet#5](../../../../samples/snippets/csharp/VS_Snippets_Wpf/LabelSnippet/CS/Pane1.xaml#5)]  
  
 <span data-ttu-id="1bb42-110">**Ajouter une touche d’accès rapide et l’habillage du texte à votre étiquette**</span><span class="sxs-lookup"><span data-stu-id="1bb42-110">**Add an Access Key and Text Wrapping to Your Label**</span></span>  
  
 <span data-ttu-id="1bb42-111">Si vous avez besoin d’un <xref:System.Windows.Controls.Label> qui a une clé d’accès (mnémonique), utilisez la <xref:System.Windows.Controls.AccessText> élément qui se trouve dans le <xref:System.Windows.Controls.Label>.</span><span class="sxs-lookup"><span data-stu-id="1bb42-111">If you need a <xref:System.Windows.Controls.Label> that has an access key (mnemonic), use the <xref:System.Windows.Controls.AccessText> element that is inside the <xref:System.Windows.Controls.Label>.</span></span>  
  
 <span data-ttu-id="1bb42-112">Les contrôles tels que <xref:System.Windows.Controls.Label>, <xref:System.Windows.Controls.Button>, <xref:System.Windows.Controls.RadioButton>, <xref:System.Windows.Controls.CheckBox>, <xref:System.Windows.Controls.MenuItem>, <xref:System.Windows.Controls.TabItem>, <xref:System.Windows.Controls.Expander>, et <xref:System.Windows.Controls.GroupBox> ont des modèles de contrôle par défaut.</span><span class="sxs-lookup"><span data-stu-id="1bb42-112">Controls such as <xref:System.Windows.Controls.Label>, <xref:System.Windows.Controls.Button>, <xref:System.Windows.Controls.RadioButton>, <xref:System.Windows.Controls.CheckBox>, <xref:System.Windows.Controls.MenuItem>, <xref:System.Windows.Controls.TabItem>, <xref:System.Windows.Controls.Expander>, and <xref:System.Windows.Controls.GroupBox> have default control templates.</span></span> <span data-ttu-id="1bb42-113">Ces modèles contiennent un <xref:System.Windows.Controls.ContentPresenter>.</span><span class="sxs-lookup"><span data-stu-id="1bb42-113">These templates contain a <xref:System.Windows.Controls.ContentPresenter>.</span></span> <span data-ttu-id="1bb42-114">Une des propriétés que vous pouvez définir sur le <xref:System.Windows.Controls.ContentPresenter> est <xref:System.Windows.Controls.ContentPresenter.RecognizesAccessKey%2A>= « true », ce qui vous permet de spécifier une clé d’accès pour le contrôle.</span><span class="sxs-lookup"><span data-stu-id="1bb42-114">One of the properties that you can set on the <xref:System.Windows.Controls.ContentPresenter> is <xref:System.Windows.Controls.ContentPresenter.RecognizesAccessKey%2A>="true", which you can use to specify an access key for the control.</span></span>  
  
 <span data-ttu-id="1bb42-115">L’exemple suivant montre comment créer un <xref:System.Windows.Controls.Label> qui a une clé d’accès et prend en charge d’habillage du texte.</span><span class="sxs-lookup"><span data-stu-id="1bb42-115">The following example shows how to create a <xref:System.Windows.Controls.Label> that has an access key and supports text wrapping.</span></span> <span data-ttu-id="1bb42-116">Pour activer l’habillage du texte, l’exemple définit le <xref:System.Windows.Controls.AccessText.TextWrapping%2A> propriété et utilise un caractère de soulignement pour spécifier la clé d’accès.</span><span class="sxs-lookup"><span data-stu-id="1bb42-116">To enable text wrapping, the example sets the <xref:System.Windows.Controls.AccessText.TextWrapping%2A> property and uses an underline character to specify the access key.</span></span> <span data-ttu-id="1bb42-117">(Le caractère qui suit immédiatement le caractère de soulignement est la touche d’accès rapide.)</span><span class="sxs-lookup"><span data-stu-id="1bb42-117">(The character that immediately follows the underline character is the access key.)</span></span>  
  
 [!code-xaml[LabelSnippet#4](../../../../samples/snippets/csharp/VS_Snippets_Wpf/LabelSnippet/CS/Pane1.xaml#4)]  
  
## <a name="see-also"></a><span data-ttu-id="1bb42-118">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="1bb42-118">See Also</span></span>  
 <span data-ttu-id="1bb42-119">[How to: Set the Target Property of a Label](http://msdn.microsoft.com/en-us/b24c6977-ebcb-4855-a9bb-3fd4435af8f8) (Comment : définir la propriété Target d’une étiquette)</span><span class="sxs-lookup"><span data-stu-id="1bb42-119">[How to: Set the Target Property of a Label](http://msdn.microsoft.com/en-us/b24c6977-ebcb-4855-a9bb-3fd4435af8f8)</span></span>
