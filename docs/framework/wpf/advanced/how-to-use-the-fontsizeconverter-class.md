---
title: Guide pratique pour utiliser la classe FontSizeConverter
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- FontSizeConverter objects [WPF]
- typography [WPF], FontSizeConverter objects
ms.assetid: 3b0592bd-7223-4860-a108-a5d72f3a9178
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: bcf2d7348ca5b6b9d3b2edc44f92afbd46d32594
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/22/2017
---
# <a name="how-to-use-the-fontsizeconverter-class"></a><span data-ttu-id="10c6b-102">Guide pratique pour utiliser la classe FontSizeConverter</span><span class="sxs-lookup"><span data-stu-id="10c6b-102">How to: Use the FontSizeConverter Class</span></span>
## <a name="example"></a><span data-ttu-id="10c6b-103">Exemple</span><span class="sxs-lookup"><span data-stu-id="10c6b-103">Example</span></span>  
 <span data-ttu-id="10c6b-104">Cet exemple montre comment créer une instance de <xref:System.Windows.FontSizeConverter> et l’utiliser pour modifier la taille de police.</span><span class="sxs-lookup"><span data-stu-id="10c6b-104">This example shows how to create an instance of <xref:System.Windows.FontSizeConverter> and use it to change a font size.</span></span>  
  
 <span data-ttu-id="10c6b-105">L’exemple définit une méthode personnalisée appelée `changeSize` qui convertit le contenu d’un <xref:System.Windows.Controls.ListBoxItem>, tel que défini dans une fonction [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] fichier, à une instance de <xref:System.Double>et versions ultérieures dans un <xref:System.String>.</span><span class="sxs-lookup"><span data-stu-id="10c6b-105">The example defines a custom method called `changeSize` that converts the contents of a <xref:System.Windows.Controls.ListBoxItem>, as defined in a separate [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] file, to an instance of <xref:System.Double>, and later into a <xref:System.String>.</span></span> <span data-ttu-id="10c6b-106">Cette méthode passe le <xref:System.Windows.Controls.ListBoxItem> à un <xref:System.Windows.FontSizeConverter> objet, qui convertit le <xref:System.Windows.Controls.ContentControl.Content%2A> d’un <xref:System.Windows.Controls.ListBoxItem> à une instance de <xref:System.Double>.</span><span class="sxs-lookup"><span data-stu-id="10c6b-106">This method passes the <xref:System.Windows.Controls.ListBoxItem> to a <xref:System.Windows.FontSizeConverter> object, which converts the <xref:System.Windows.Controls.ContentControl.Content%2A> of a <xref:System.Windows.Controls.ListBoxItem> to an instance of <xref:System.Double>.</span></span> <span data-ttu-id="10c6b-107">Cette valeur est ensuite retournée comme la valeur de la <xref:System.Windows.Controls.TextBlock.FontSize%2A> propriété de la <xref:System.Windows.Controls.TextBlock> élément.</span><span class="sxs-lookup"><span data-stu-id="10c6b-107">This value is then passed back as the value of the <xref:System.Windows.Controls.TextBlock.FontSize%2A> property of the <xref:System.Windows.Controls.TextBlock> element.</span></span>  
  
 <span data-ttu-id="10c6b-108">Cet exemple définit également une deuxième méthode personnalisée qui est appelée `changeFamily`.</span><span class="sxs-lookup"><span data-stu-id="10c6b-108">This example also defines a second custom method that is called `changeFamily`.</span></span> <span data-ttu-id="10c6b-109">Cette méthode convertit le <xref:System.Windows.Controls.ContentControl.Content%2A> de la <xref:System.Windows.Controls.ListBoxItem> à un <xref:System.String>, puis passe cette valeur à la <xref:System.Windows.Controls.TextBlock.FontFamily%2A> propriété de la <xref:System.Windows.Controls.TextBlock> élément.</span><span class="sxs-lookup"><span data-stu-id="10c6b-109">This method converts the <xref:System.Windows.Controls.ContentControl.Content%2A> of the <xref:System.Windows.Controls.ListBoxItem> to a <xref:System.String>, and then passes that value to the <xref:System.Windows.Controls.TextBlock.FontFamily%2A> property of the <xref:System.Windows.Controls.TextBlock> element.</span></span>  
  
 <span data-ttu-id="10c6b-110">Cet exemple ne s’exécute pas.</span><span class="sxs-lookup"><span data-stu-id="10c6b-110">This example does not run.</span></span>  
  
 [!code-csharp[FontSizeConverter#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FontSizeConverter/CSharp/Window1.xaml.cs#1)]  
  
## <a name="see-also"></a><span data-ttu-id="10c6b-111">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="10c6b-111">See Also</span></span>  
 <xref:System.Windows.FontSizeConverter>
