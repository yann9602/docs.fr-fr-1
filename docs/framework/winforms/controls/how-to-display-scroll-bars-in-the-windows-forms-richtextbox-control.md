---
title: "Comment&#160;: afficher les barres de d&#233;filement dans le contr&#244;le RichTextBox Windows Forms | Microsoft Docs"
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
  - "RichTextBox (contrôle Windows Forms), afficher les barres de défilement"
  - "barres de défilement, afficher dans les contrôles"
  - "zones de texte, afficher les barres de défilement"
ms.assetid: cdeb42e1-86e8-410c-ba46-18aec264ef5f
caps.latest.revision: 9
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 9
---
# Comment&#160;: afficher les barres de d&#233;filement dans le contr&#244;le RichTextBox Windows Forms
Par défaut, le contrôle <xref:System.Windows.Forms.RichTextBox> Windows Forms affiche les barres de défilement horizontale et verticale si nécessaire.  La propriété <xref:System.Windows.Forms.RichTextBox.ScrollBars%2A> du contrôle <xref:System.Windows.Forms.RichTextBox> peut prendre sept valeurs différentes, décrites dans le tableau ci\-dessous.  
  
### Pour afficher les barres de défilement dans un contrôle RichTextBox  
  
1.  Affectez à la propriété <xref:System.Windows.Forms.RichTextBox.Multiline%2A> la valeur `true`.  Aucun type de barre de défilement, horizontal y compris, ne sera affiché si la propriété <xref:System.Windows.Forms.RichTextBox.Multiline%2A> a la valeur `false`.  
  
2.  Affectez à la propriété <xref:System.Windows.Forms.RichTextBox.ScrollBars%2A> une valeur appropriée de l'énumération <xref:System.Windows.Forms.RichTextBoxScrollBars>.  
  
    |Valeur|Description|  
    |------------|-----------------|  
    |<xref:System.Windows.Forms.RichTextBoxScrollBars> \(par défaut\)|Affiche les barres de défilement horizontal ou vertical, ou les deux, uniquement lorsque le texte dépasse la largeur et la longueur du contrôle.|  
    |<xref:System.Windows.Forms.RichTextBoxScrollBars>|N'affiche jamais l'un ou l'autre type de barre de défilement.|  
    |<xref:System.Windows.Forms.RichTextBoxScrollBars>|Affiche une barre de défilement horizontal uniquement lorsque le texte dépasse la largeur du contrôle.  \(Pour que cela se produise, la propriété <xref:System.Windows.Forms.TextBoxBase.WordWrap%2A> doit avoir la valeur `false`.\)|  
    |<xref:System.Windows.Forms.RichTextBoxScrollBars>|Affiche une barre de défilement vertical uniquement lorsque le texte dépasse la hauteur du contrôle.|  
    |<xref:System.Windows.Forms.RichTextBoxScrollBars>|Affiche une barre de défilement horizontal lorsque la propriété <xref:System.Windows.Forms.TextBoxBase.WordWrap%2A> a la valeur `false`.  La barre de défilement est estompée lorsque le texte ne dépasse pas la largeur du contrôle.|  
    |<xref:System.Windows.Forms.RichTextBoxScrollBars>|Affiche toujours une barre de défilement vertical.  La barre de défilement est estompée lorsque le texte ne dépasse pas la longueur du contrôle.|  
    |<xref:System.Windows.Forms.RichTextBoxScrollBars>|Affiche toujours une barre de défilement vertical.  Affiche une barre de défilement horizontal lorsque la propriété <xref:System.Windows.Forms.TextBoxBase.WordWrap%2A> a la valeur `false`.  Les barres de défilement sont estompées lorsque le texte ne dépasse pas la largeur et la longueur du contrôle.|  
  
3.  Affectez à la propriété <xref:System.Windows.Forms.TextBoxBase.WordWrap%2A> une valeur appropriée.  
  
    |Valeur|Description|  
    |------------|-----------------|  
    |`false`|Le texte dans le contrôle n'est pas automatiquement ajusté à la largeur du contrôle et défilera vers la droite jusqu'au prochain saut de ligne.  Utilisez cette valeur si vous avez choisi Horizontal ou Both, ci\-dessus.|  
    |`true` \(par défaut\)|Le texte dans le contrôle est automatiquement ajusté à la largeur du contrôle.  La barre de défilement horizontal n'apparaîtra pas.  Utilisez cette valeur si vous avez choisi Vertical ou None ci\-dessus afin d'afficher un ou plusieurs paragraphes.|  
  
## Voir aussi  
 <xref:System.Windows.Forms.RichTextBoxScrollBars>   
 <xref:System.Windows.Forms.RichTextBox>   
 [RichTextBox, contrôle](../../../../docs/framework/winforms/controls/richtextbox-control-windows-forms.md)   
 [Contrôles à utiliser dans les Windows Forms](../../../../docs/framework/winforms/controls/controls-to-use-on-windows-forms.md)