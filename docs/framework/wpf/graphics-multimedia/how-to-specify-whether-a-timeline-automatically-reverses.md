---
title: "Comment&#160;: sp&#233;cifier l&#39;inversion automatique ou non d&#39;une chronologie | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-wpf"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "AutoReverse (propriété de chronologies)"
  - "chronologies, AutoReverse (propriété)"
ms.assetid: 1648dd90-1bee-409a-ac69-ac729867f557
caps.latest.revision: 4
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 4
---
# Comment&#160;: sp&#233;cifier l&#39;inversion automatique ou non d&#39;une chronologie
La propriété <xref:System.Windows.Media.Animation.Timeline.AutoReverse%2A> d'une chronologie détermine si elle repart en arrière après avoir effectué une itération en avant.  L'exemple suivant affiche plusieurs animations dont la durée et les valeurs cibles sont identiques, mais qui comportent des paramètres <xref:System.Windows.Media.Animation.Timeline.AutoReverse%2A> différents.  Pour illustrer le comportement de la propriété <xref:System.Windows.Media.Animation.Timeline.AutoReverse%2A> avec différents paramètres <xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A>, certaines animations sont définies pour être répétées.  La dernière animation indique le fonctionnement de la propriété <xref:System.Windows.Media.Animation.Timeline.AutoReverse%2A> dans des chronologies imbriquées.  
  
## Exemple  
 [!code-xml[timingbehaviors_snip#AutoReverseAndRepeatBehaviorExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_snip/CSharp/AutoReverseExample.xaml#autoreverseandrepeatbehaviorexamplewholepage)]