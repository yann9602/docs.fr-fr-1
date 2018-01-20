---
title: "Comment : utiliser un objet ThicknessConverter"
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
- border thickness [WPF]
- ThicknessConverter objects [WPF]
ms.assetid: 52682194-d7fd-499c-8005-73fcc84e7b2c
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: c2445eba7556822c8265337ec97c2f0a9f1d5042
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/19/2018
---
# <a name="how-to-use-a-thicknessconverter-object"></a><span data-ttu-id="2670f-102">Comment : utiliser un objet ThicknessConverter</span><span class="sxs-lookup"><span data-stu-id="2670f-102">How to: Use a ThicknessConverter Object</span></span>
## <a name="example"></a><span data-ttu-id="2670f-103">Exemple</span><span class="sxs-lookup"><span data-stu-id="2670f-103">Example</span></span>  
 <span data-ttu-id="2670f-104">Cet exemple montre comment créer une instance de <xref:System.Windows.ThicknessConverter> et l’utiliser pour modifier l’épaisseur d’une bordure.</span><span class="sxs-lookup"><span data-stu-id="2670f-104">This example shows how to create an instance of <xref:System.Windows.ThicknessConverter> and use it to change the thickness of a border.</span></span>  
  
 <span data-ttu-id="2670f-105">L’exemple définit une méthode personnalisée appelée `changeThickness`; cette méthode convertit d’abord le contenu d’un <xref:System.Windows.Controls.ListBoxItem>, tel que défini dans une fonction [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] fichier, à une instance de <xref:System.Windows.Thickness>et convertit le contenu par la suite un <xref:System.String>.</span><span class="sxs-lookup"><span data-stu-id="2670f-105">The example defines a custom method called `changeThickness`; this method first converts the contents of a <xref:System.Windows.Controls.ListBoxItem>, as defined in a separate [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] file, to an instance of <xref:System.Windows.Thickness>, and later converts the content into a <xref:System.String>.</span></span> <span data-ttu-id="2670f-106">Cette méthode passe le <xref:System.Windows.Controls.ListBoxItem> à un <xref:System.Windows.ThicknessConverter> objet, qui convertit le <xref:System.Windows.Controls.ContentControl.Content%2A> d’un <xref:System.Windows.Controls.ListBoxItem> à une instance de <xref:System.Windows.Thickness>.</span><span class="sxs-lookup"><span data-stu-id="2670f-106">This method passes the <xref:System.Windows.Controls.ListBoxItem> to a <xref:System.Windows.ThicknessConverter> object, which converts the <xref:System.Windows.Controls.ContentControl.Content%2A> of a <xref:System.Windows.Controls.ListBoxItem> to an instance of <xref:System.Windows.Thickness>.</span></span> <span data-ttu-id="2670f-107">Cette valeur est ensuite retournée comme la valeur de la <xref:System.Windows.Controls.Border.BorderThickness%2A> propriété de la <xref:System.Windows.Controls.Border>.</span><span class="sxs-lookup"><span data-stu-id="2670f-107">This value is then passed back as the value of the <xref:System.Windows.Controls.Border.BorderThickness%2A> property of the <xref:System.Windows.Controls.Border>.</span></span>  
  
 <span data-ttu-id="2670f-108">Cet exemple ne s’exécute pas.</span><span class="sxs-lookup"><span data-stu-id="2670f-108">This example does not run.</span></span>  
  
 [!code-csharp[ThicknessConverter#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ThicknessConverter/CSharp/Window1.xaml.cs#1)]
 [!code-vb[ThicknessConverter#1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ThicknessConverter/VisualBasic/Window1.xaml.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="2670f-109">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="2670f-109">See Also</span></span>  
 <xref:System.Windows.Thickness>  
 <xref:System.Windows.ThicknessConverter>  
 <xref:System.Windows.Controls.Border>  
 [<span data-ttu-id="2670f-110">Comment : modifier la propriété Margin</span><span class="sxs-lookup"><span data-stu-id="2670f-110">How to: Change the Margin Property</span></span>](http://msdn.microsoft.com/library/8a313efd-5f99-4097-b4c1-8fa49d8379a2)  
 [<span data-ttu-id="2670f-111">Comment : convertir un ListBoxItem en un nouveau Type de données</span><span class="sxs-lookup"><span data-stu-id="2670f-111">How to: Convert a ListBoxItem to a new Data Type</span></span>](http://msdn.microsoft.com/library/7a080b88-184e-4b27-bb61-d42bafba9727)  
 [<span data-ttu-id="2670f-112">Vue d’ensemble de Panel</span><span class="sxs-lookup"><span data-stu-id="2670f-112">Panels Overview</span></span>](../../../../docs/framework/wpf/controls/panels-overview.md)
