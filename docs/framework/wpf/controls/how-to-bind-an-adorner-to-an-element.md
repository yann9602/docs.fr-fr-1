---
title: "Comment&#160;: lier un ornement &#224; un &#233;l&#233;ment | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-wpf"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "ornements, lier à des UIElements spécifiés"
  - "UIElements, lier des ornements à"
ms.assetid: b2101611-a0ee-4137-bdb8-9b3673d2e6b9
caps.latest.revision: 10
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 10
---
# Comment&#160;: lier un ornement &#224; un &#233;l&#233;ment
Cet exemple montre comment lier par programme un ornement à un <xref:System.Windows.UIElement> spécifié.  
  
## Exemple  
 Pour lier un ornement à un <xref:System.Windows.UIElement> particulier, suivez les étapes ci\-dessous :  
  
1.  Appelez la méthode `static` <xref:System.Windows.Documents.AdornerLayer.GetAdornerLayer%2A> pour obtenir un objet <xref:System.Windows.Documents.AdornerLayer> pour le <xref:System.Windows.UIElement> à orner.  <xref:System.Windows.Documents.AdornerLayer.GetAdornerLayer%2A> parcourt l'arborescence d'éléments visuels en commençant par l'**UIElement** spécifié et retourne la première couche d'ornement qu'il trouve.  \(Si aucune couche d'ornement n'est trouvée, la méthode retourne la valeur null.\)  
  
2.  Appelez la méthode <xref:System.Windows.Documents.AdornerLayer.Add%2A> pour lier l'ornement à l'**UIElement** cible.  
  
 L'exemple suivant lie un SimpleCircleAdorner \(illustré ci\-dessus\) à une <xref:System.Windows.Controls.TextBox> appelée *myTextBox*.  
  
 [!code-csharp[Adorners_SimpleCircleAdorner#_AdornSingleElement](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Adorners_SimpleCircleAdorner/CSharp/Window1.xaml.cs#_adornsingleelement)]
 [!code-vb[Adorners_SimpleCircleAdorner#_AdornSingleElement](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/Adorners_SimpleCircleAdorner/VisualBasic/Window1.xaml.vb#_adornsingleelement)]  
  
> [!NOTE]
>  L'utilisation de [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] pour lier un ornement à un autre élément n'est pas prise en charge actuellement.  
  
## Voir aussi  
 [Vue d'ensemble des ornements](../../../../docs/framework/wpf/controls/adorners-overview.md)