---
title: "Stockage de l&#39;encre | Microsoft Docs"
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
  - "ISF (Ink Serialized Format)"
  - "encre, stocker"
  - "Ink Serialized Format (ISF)"
  - "récupérer l'encre"
  - "stocker l'encre"
ms.assetid: a3f6d16b-d682-4680-9965-907332b4d2b8
caps.latest.revision: 9
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 9
---
# Stockage de l&#39;encre
Les méthodes <xref:System.Windows.Ink.StrokeCollection.Save%2A> offrent une prise en charge pour le stockage de l'encre au format ISF \(Ink Serialized Format\).  Les constructeurs de la classe <xref:System.Windows.Ink.StrokeCollection> offrent une prise en charge pour la lecture des données de l'encre.  
  
## Stockage de l'encre et récupération  
 Cette section étudie le stockage et la récupération de l'encre dans la plateforme [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].  
  
 L'exemple suivant implémente un gestionnaire d'événements du clic de bouton qui présente une boîte de dialogue Enregistrer à l'utilisateur et enregistre l'encre d'un <xref:System.Windows.Controls.InkCanvas> dans un fichier.  
  
 [!code-csharp[DigitalInkTopics#12](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DigitalInkTopics/CSharp/Window1.xaml.cs#12)]
 [!code-vb[DigitalInkTopics#12](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DigitalInkTopics/VisualBasic/Window1.xaml.vb#12)]  
  
 L'exemple suivant implémente un gestionnaire d'événements du clic de bouton qui présente une boîte de dialogue Ouvrir à l'utilisateur et lit l'encre du fichier dans un élément <xref:System.Windows.Controls.InkCanvas>.  
  
 [!code-csharp[DigitalInkTopics#13](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DigitalInkTopics/CSharp/Window1.xaml.cs#13)]
 [!code-vb[DigitalInkTopics#13](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DigitalInkTopics/VisualBasic/Window1.xaml.vb#13)]  
  
## Voir aussi  
 <xref:System.Windows.Controls.InkCanvas>   
 [Windows Presentation Foundation](../../../../docs/framework/wpf/index.md)