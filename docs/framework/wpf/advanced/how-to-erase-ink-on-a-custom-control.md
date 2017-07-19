---
title: "Comment&#160;: effacer l&#39;encre sur un contr&#244;le personnalis&#233; | Microsoft Docs"
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
  - "contrôles personnalisés, effacer l'encre sur"
  - "encre, effacer sur un contrôle personnalisé"
ms.assetid: d88c50f9-b4d8-4962-a28b-67d6a15a5fe0
caps.latest.revision: 4
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 4
---
# Comment&#160;: effacer l&#39;encre sur un contr&#244;le personnalis&#233;
Le <xref:System.Windows.Ink.IncrementalStrokeHitTester> détermine si le trait qui est dessiné croise un autre trait.  Cela est très utile pour créer un contrôle permettant à un utilisateur d'effacer certaines parties d'un trait, comme le peut un utilisateur sur un <xref:System.Windows.Controls.InkCanvas> lorsque le <xref:System.Windows.Controls.InkCanvas.EditingMode%2A> a la valeur <xref:System.Windows.Controls.InkCanvasEditingMode>.  
  
## Exemple  
 L'exemple suivant crée un contrôle personnalisé qui permet à l'utilisateur d'effacer certaines parties des traits.  Cet exemple crée un contrôle qui contient de l'encre lorsqu'il est initialisé.  Pour créer un contrôle qui collecte de l'encre, consultez [Création d'un contrôle d'entrée d'encre](../../../../docs/framework/wpf/advanced/creating-an-ink-input-control.md).  
  
 [!code-csharp[HowToEraseInk#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HowToEraseInk/CSharp/InkEraser.cs#1)]
 [!code-vb[HowToEraseInk#1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/HowToEraseInk/VisualBasic/InkEraser.vb#1)]