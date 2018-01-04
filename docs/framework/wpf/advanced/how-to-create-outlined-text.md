---
title: "Comment : créer du texte avec contour"
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
- typography [WPF], linear gradient brush
- outlined text [WPF]
- gradient brush [WPF]
- linear gradient brush [WPF]
- typography [WPF], outline effects
ms.assetid: 4aa3cf6e-1953-4f26-8230-7c1409e5f28d
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 41254d8f93174c896923b1c070e6bf9b5b7c863c
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-create-outlined-text"></a><span data-ttu-id="25c47-102">Comment : créer du texte avec contour</span><span class="sxs-lookup"><span data-stu-id="25c47-102">How to: Create Outlined Text</span></span>
<span data-ttu-id="25c47-103">Dans la plupart des cas, lorsque vous ajoutez un ornement que les chaînes de texte dans votre [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] application, à l’aide de texte en termes d’une collection de caractères discrets, ou glyphes.</span><span class="sxs-lookup"><span data-stu-id="25c47-103">In most cases, when you are adding ornamentation to text strings in your [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] application, you are using text in terms of a collection of discrete characters, or glyphs.</span></span> <span data-ttu-id="25c47-104">Par exemple, Impossible de créer un pinceau de dégradé linéaire et de l’appliquer à la <xref:System.Windows.Controls.Control.Foreground%2A> propriété d’un <xref:System.Windows.Controls.TextBox> objet.</span><span class="sxs-lookup"><span data-stu-id="25c47-104">For example, you could create a linear gradient brush and apply it to the <xref:System.Windows.Controls.Control.Foreground%2A> property of a <xref:System.Windows.Controls.TextBox> object.</span></span> <span data-ttu-id="25c47-105">Lorsque vous affichez ou modifiez la zone de texte, le pinceau de dégradé linéaire est appliqué automatiquement à l’ensemble actuel de caractères dans la chaîne de texte.</span><span class="sxs-lookup"><span data-stu-id="25c47-105">When you display or edit the text box, the linear gradient brush is automatically applied to the current set of characters in the text string.</span></span>  
  
 <span data-ttu-id="25c47-106">![Texte affiché avec un pinceau de dégradé linéaire](../../../../docs/framework/wpf/advanced/media/outlinedtext01.jpg "OutlinedText01")</span><span class="sxs-lookup"><span data-stu-id="25c47-106">![Text displayed with a linear gradient brush](../../../../docs/framework/wpf/advanced/media/outlinedtext01.jpg "OutlinedText01")</span></span>  
<span data-ttu-id="25c47-107">Exemple d’un pinceau de dégradé linéaire appliqué à une zone de texte</span><span class="sxs-lookup"><span data-stu-id="25c47-107">Example of a linear gradient brush applied to a text box</span></span>  
  
 <span data-ttu-id="25c47-108">Toutefois, vous pouvez également convertir le texte en <xref:System.Windows.Media.Geometry> objets, ce qui vous permet de créer d’autres types de texte visuellement enrichi.</span><span class="sxs-lookup"><span data-stu-id="25c47-108">However, you can also convert text into <xref:System.Windows.Media.Geometry> objects, allowing you to create other types of visually rich text.</span></span> <span data-ttu-id="25c47-109">Par exemple, vous pouvez créer un <xref:System.Windows.Media.Geometry> objet basé sur le contour d’une chaîne de texte.</span><span class="sxs-lookup"><span data-stu-id="25c47-109">For example, you could create a <xref:System.Windows.Media.Geometry> object based on the outline of a text string.</span></span>  
  
 <span data-ttu-id="25c47-110">![Contour du texte à l’aide d’un pinceau de dégradé linéaire](../../../../docs/framework/wpf/advanced/media/outlinedtext02.jpg "OutlinedText02")</span><span class="sxs-lookup"><span data-stu-id="25c47-110">![Text outline using a linear gradient brush](../../../../docs/framework/wpf/advanced/media/outlinedtext02.jpg "OutlinedText02")</span></span>  
<span data-ttu-id="25c47-111">Exemple d’un pinceau de dégradé linéaire appliqué à la géométrie de plan du texte</span><span class="sxs-lookup"><span data-stu-id="25c47-111">Example of a linear gradient brush applied to the outline geometry of text</span></span>  
  
 <span data-ttu-id="25c47-112">Lorsque le texte est converti en un <xref:System.Windows.Media.Geometry> de l’objet, il n’est plus une collection de caractères, vous ne pouvez pas modifier les caractères dans la chaîne de texte.</span><span class="sxs-lookup"><span data-stu-id="25c47-112">When text is converted to a <xref:System.Windows.Media.Geometry> object, it is no longer a collection of characters—you cannot modify the characters in the text string.</span></span> <span data-ttu-id="25c47-113">Vous pouvez néanmoins modifier l’apparence du texte converti en changeant ses propriétés de trait et de remplissage.</span><span class="sxs-lookup"><span data-stu-id="25c47-113">However, you can affect the appearance of the converted text by modifying its stroke and fill properties.</span></span> <span data-ttu-id="25c47-114">Le trait fait référence au contour du texte converti et le remplissage à la zone située à l’intérieur du contour du texte converti.</span><span class="sxs-lookup"><span data-stu-id="25c47-114">The stroke refers to the outline of the converted text; the fill refers to the area inside the outline of the converted text.</span></span>  
  
 <span data-ttu-id="25c47-115">Les exemples suivants illustrent plusieurs manières de créer des effets visuels en modifiant le trait et le remplissage de texte converti.</span><span class="sxs-lookup"><span data-stu-id="25c47-115">The following examples illustrate several ways of creating visual effects by modifying the stroke and fill of converted text.</span></span>  
  
 <span data-ttu-id="25c47-116">![Texte avec différentes couleurs de trait et de remplissage](../../../../docs/framework/wpf/advanced/media/outlinedtext03.jpg "OutlinedText03")</span><span class="sxs-lookup"><span data-stu-id="25c47-116">![Text with different colors for fill and stroke](../../../../docs/framework/wpf/advanced/media/outlinedtext03.jpg "OutlinedText03")</span></span>  
<span data-ttu-id="25c47-117">Exemple de définition du trait et du remplissage de différentes couleurs</span><span class="sxs-lookup"><span data-stu-id="25c47-117">Example of setting stroke and fill to different colors</span></span>  
  
 <span data-ttu-id="25c47-118">![Texte avec pinceau image appliqué au trait](../../../../docs/framework/wpf/advanced/media/outlinedtext04.jpg "OutlinedText04")</span><span class="sxs-lookup"><span data-stu-id="25c47-118">![Text with image brush applied to stroke](../../../../docs/framework/wpf/advanced/media/outlinedtext04.jpg "OutlinedText04")</span></span>  
<span data-ttu-id="25c47-119">Exemple de pinceau image appliqué au trait</span><span class="sxs-lookup"><span data-stu-id="25c47-119">Example of an image brush applied to the stroke</span></span>  
  
 <span data-ttu-id="25c47-120">Il est également possible de modifier le rectangle de cadre englobant ou mise en surbrillance, du texte converti.</span><span class="sxs-lookup"><span data-stu-id="25c47-120">It is also possible to modify the bounding box rectangle, or highlight, of the converted text.</span></span> <span data-ttu-id="25c47-121">L’exemple suivant illustre un moyen de créer des effets visuels en modifiant le trait et la surbrillance du texte converti.</span><span class="sxs-lookup"><span data-stu-id="25c47-121">The following example illustrates a way to creating visual effects by modifying the stroke and highlight of converted text.</span></span>  
  
 <span data-ttu-id="25c47-122">![Texte avec pinceau image appliqué au trait](../../../../docs/framework/wpf/advanced/media/outlinedtext05.jpg "OutlinedText05")</span><span class="sxs-lookup"><span data-stu-id="25c47-122">![Text with image brush applied to stroke](../../../../docs/framework/wpf/advanced/media/outlinedtext05.jpg "OutlinedText05")</span></span>  
<span data-ttu-id="25c47-123">Exemple de pinceau image appliqué au trait et surbrillance</span><span class="sxs-lookup"><span data-stu-id="25c47-123">Example of an image brush applied to the stroke and highlight</span></span>  
  
## <a name="example"></a><span data-ttu-id="25c47-124">Exemple</span><span class="sxs-lookup"><span data-stu-id="25c47-124">Example</span></span>  
 <span data-ttu-id="25c47-125">La clé pour convertir du texte à un <xref:System.Windows.Media.Geometry> objet consiste à utiliser le <xref:System.Windows.Media.FormattedText> objet.</span><span class="sxs-lookup"><span data-stu-id="25c47-125">The key to converting text to a <xref:System.Windows.Media.Geometry> object is to use the <xref:System.Windows.Media.FormattedText> object.</span></span> <span data-ttu-id="25c47-126">Une fois que vous avez créé cet objet, vous pouvez utiliser la <xref:System.Windows.Media.FormattedText.BuildGeometry%2A> et <xref:System.Windows.Media.FormattedText.BuildHighlightGeometry%2A> des méthodes pour convertir le texte à <xref:System.Windows.Media.Geometry> objets.</span><span class="sxs-lookup"><span data-stu-id="25c47-126">Once you have created this object, you can use the <xref:System.Windows.Media.FormattedText.BuildGeometry%2A> and <xref:System.Windows.Media.FormattedText.BuildHighlightGeometry%2A> methods to convert the text to <xref:System.Windows.Media.Geometry> objects.</span></span> <span data-ttu-id="25c47-127">La première méthode retourne la géométrie du texte mis en forme ; la deuxième méthode retourne que la géométrie de mise en forme du texte de la zone de délimitation.</span><span class="sxs-lookup"><span data-stu-id="25c47-127">The first method returns the geometry of the formatted text; the second method returns the geometry of the formatted text's bounding box.</span></span> <span data-ttu-id="25c47-128">L’exemple de code suivant montre comment créer un <xref:System.Windows.Media.FormattedText> objet et récupérer les géométries du texte mis en forme et son cadre englobant.</span><span class="sxs-lookup"><span data-stu-id="25c47-128">The following code example shows how to create a <xref:System.Windows.Media.FormattedText> object and to retrieve the geometries of the formatted text and its bounding box.</span></span>  
  
 [!code-csharp[OutlineTextControlViewer#CreateText](../../../../samples/snippets/csharp/VS_Snippets_Wpf/OutlineTextControlViewer/CSharp/OutlineTextControl.cs#createtext)]
 [!code-vb[OutlineTextControlViewer#CreateText](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/OutlineTextControlViewer/visualbasic/outlinetextcontrol.vb#createtext)]  
  
 <span data-ttu-id="25c47-129">Pour afficher les données récupérées du <xref:System.Windows.Media.Geometry> objets, vous avez besoin pour accéder à la <xref:System.Windows.Media.DrawingContext> de l’objet qui affiche le texte converti.</span><span class="sxs-lookup"><span data-stu-id="25c47-129">In order to display the retrieved the <xref:System.Windows.Media.Geometry> objects, you need to access the <xref:System.Windows.Media.DrawingContext> of the object that is displaying the converted text.</span></span> <span data-ttu-id="25c47-130">Dans ces exemples de code, cela en créant un objet de contrôle personnalisé qui est dérivé d’une classe qui prend en charge le rendu défini par l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="25c47-130">In these code examples, this is done by creating a custom control object that is derived from a class that supports user-defined rendering.</span></span>  
  
 <span data-ttu-id="25c47-131">Pour afficher les <xref:System.Windows.Media.Geometry> objets dans le contrôle personnalisé, fournissez une substitution pour la <xref:System.Windows.UIElement.OnRender%2A> (méthode).</span><span class="sxs-lookup"><span data-stu-id="25c47-131">To display <xref:System.Windows.Media.Geometry> objects in the custom control, provide an override for the <xref:System.Windows.UIElement.OnRender%2A> method.</span></span> <span data-ttu-id="25c47-132">Votre méthode de substitution doit utiliser le <xref:System.Windows.Media.DrawingContext.DrawGeometry%2A> méthode pour dessiner le <xref:System.Windows.Media.Geometry> objets.</span><span class="sxs-lookup"><span data-stu-id="25c47-132">Your overridden method should use the <xref:System.Windows.Media.DrawingContext.DrawGeometry%2A> method to draw the <xref:System.Windows.Media.Geometry> objects.</span></span>  
  
 [!code-csharp[OutlineTextControlViewer#OnRender](../../../../samples/snippets/csharp/VS_Snippets_Wpf/OutlineTextControlViewer/CSharp/OutlineTextControl.cs#onrender)]
 [!code-vb[OutlineTextControlViewer#OnRender](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/OutlineTextControlViewer/visualbasic/outlinetextcontrol.vb#onrender)]  
  
## <a name="see-also"></a><span data-ttu-id="25c47-133">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="25c47-133">See Also</span></span>  
 [<span data-ttu-id="25c47-134">Dessin du texte mis en forme</span><span class="sxs-lookup"><span data-stu-id="25c47-134">Drawing Formatted Text</span></span>](../../../../docs/framework/wpf/advanced/drawing-formatted-text.md)
