---
title: "Comment&#160;: restituer un &#233;l&#233;ment de style visuel | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-winforms"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "jsharp"
helpviewer_keywords: 
  - "aspect professionnel, appliquer à des éléments des applications Windows Forms"
  - "styles visuels, rendu des contrôles Windows Forms"
  - "thèmes visuels, appliquer à des éléments des applications Windows Forms"
ms.assetid: a207781b-1baa-4ce9-b788-1e951bd4b5df
caps.latest.revision: 9
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 9
---
# Comment&#160;: restituer un &#233;l&#233;ment de style visuel
L'espace de noms <xref:System.Windows.Forms.VisualStyles?displayProperty=fullName> expose des objets <xref:System.Windows.Forms.VisualStyles.VisualStyleElement> qui représentent les éléments de l'interface utilisateur Windows pris en charge par les styles visuels.  Cette rubrique montre comment utiliser la classe <xref:System.Windows.Forms.VisualStyles.VisualStyleRenderer> pour restituer l'<xref:System.Windows.Forms.VisualStyles.VisualStyleElement> qui représente les boutons **Fermer la session** et **Arrêter** du menu Démarrer.  
  
### Pour restituer un élément de style visuel  
  
1.  Créez un <xref:System.Windows.Forms.VisualStyles.VisualStyleRenderer> et définissez\-le selon l'élément que vous souhaitez dessiner.  Notez l'utilisation de la propriété <xref:System.Windows.Forms.Application.RenderWithVisualStyles%2A?displayProperty=fullName> et de la méthode <xref:System.Windows.Forms.VisualStyles.VisualStyleRenderer.IsElementDefined%2A?displayProperty=fullName> ; le constructeur <xref:System.Windows.Forms.VisualStyles.VisualStyleRenderer.%23ctor%2A> lèvera une exception si les styles visuels sont désactivés ou si un élément est indéfini.  
  
     [!code-cpp[System.Windows.Forms.VisualStyles.VisualStyleRenderer_Simple#4](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.VisualStyles.VisualStyleRenderer_Simple/cpp/form1.cpp#4)]
     [!code-csharp[System.Windows.Forms.VisualStyles.VisualStyleRenderer_Simple#4](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.VisualStyles.VisualStyleRenderer_Simple/CS/form1.cs#4)]
     [!code-vb[System.Windows.Forms.VisualStyles.VisualStyleRenderer_Simple#4](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.VisualStyles.VisualStyleRenderer_Simple/VB/form1.vb#4)]  
  
2.  Appelez la méthode <xref:System.Windows.Forms.VisualStyles.VisualStyleRenderer.DrawBackground%2A> pour restituer l'élément que <xref:System.Windows.Forms.VisualStyles.VisualStyleRenderer> représente actuellement.  
  
     [!code-cpp[System.Windows.Forms.VisualStyles.VisualStyleRenderer_Simple#6](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.VisualStyles.VisualStyleRenderer_Simple/cpp/form1.cpp#6)]
     [!code-csharp[System.Windows.Forms.VisualStyles.VisualStyleRenderer_Simple#6](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.VisualStyles.VisualStyleRenderer_Simple/CS/form1.cs#6)]
     [!code-vb[System.Windows.Forms.VisualStyles.VisualStyleRenderer_Simple#6](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.VisualStyles.VisualStyleRenderer_Simple/VB/form1.vb#6)]  
  
## Compilation du code  
 Cet exemple nécessite :  
  
-   Un contrôle personnalisé dérivé de la classe <xref:System.Windows.Forms.Control>.  
  
-   Un <xref:System.Windows.Forms.Form> qui héberge le contrôle personnalisé.  
  
-   Des références aux espaces de noms <xref:System?displayProperty=fullName>, <xref:System.Drawing?displayProperty=fullName>, <xref:System.Windows.Forms?displayProperty=fullName> et <xref:System.Windows.Forms.VisualStyles?displayProperty=fullName>.  
  
## Voir aussi  
 [Rendu des contrôles avec les styles visuels](../../../../docs/framework/winforms/controls/rendering-controls-with-visual-styles.md)