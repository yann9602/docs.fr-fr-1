---
title: "Reconnaissance d&#39;&#233;criture manuscrite | Microsoft Docs"
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
  - "écriture manuscrite (reconnaissance)"
  - "reconnaissance de l'écriture manuscrite"
ms.assetid: f4e8576d-e731-4bac-9818-22e2ae636636
caps.latest.revision: 11
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 9
---
# Reconnaissance d&#39;&#233;criture manuscrite
Cette section explique les notions de base de la reconnaissance relative à l'encre numérique dans la plateforme [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].  
  
## Solutions de reconnaissance  
 L'exemple suivant montre comment reconnaître de l'encre à l'aide de <xref:System.Windows.Ink.InkAnalyzer>.  
  
> [!NOTE]
>  Cet exemple requiert que les modules de reconnaissance d'écriture manuscrite soient installés sur le système.  
  
 Créez un projet d'application [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] dans Visual Studio 2005, intitulé InkRecognition.  Remplacez le contenu du fichier Window1.xaml par le code XAML suivant.  Ce code restitue l'interface utilisateur de l'application.  
  
 [!code-xml[InkRecognition#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/InkRecognition/CSharp/Window1.xaml#1)]  
  
 Ajoutez une référence aux assemblys WPF Ink Analysis, IAWinFX.dll, IACore.dll et IALoader.dll que vous pouvez trouver dans \\Program Files\\Reference Assemblies\\Microsoft\\Tablet PC\\v1.7.  Remplacez le contenu du fichier code\-behind par le code suivant.  
  
 [!code-csharp[InkRecognition#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/InkRecognition/CSharp/Window1.xaml.cs#2)]
 [!code-vb[InkRecognition#2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/InkRecognition/VisualBasic/Window1.xaml.vb#2)]  
  
## Voir aussi  
 <xref:System.Windows.Ink.InkAnalyzer>   
 <xref:System.Windows.Ink.AnalysisStatus>   
 <xref:System.Windows.Controls.InkCanvas>