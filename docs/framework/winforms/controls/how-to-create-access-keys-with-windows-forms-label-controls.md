---
title: "Comment&#160;: cr&#233;er des touches d&#39;acc&#232;s rapide &#224; l&#39;aide des contr&#244;les Label Windows Forms | Microsoft Docs"
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
  - "touches d'accès rapide, créer des touches pour les contrôles"
  - "touches d'accès rapide, Windows Forms"
  - "contrôles (Windows Forms), touches d'accès rapide"
  - "contrôles de boîte de dialogue, mnémoniques"
  - "raccourcis clavier, créer des touches pour les contrôles"
  - "Label (contrôle Windows Forms), créer des touches d'accès"
  - "mnémoniques"
  - "mnémoniques, ajouter aux contrôles de boîte de dialogue"
  - "UseMnemonic (propriété), Label (contrôle)"
  - "contrôles Windows Forms, touches d'accès rapide"
ms.assetid: 5ee8f823-80be-4a4f-96a4-412671e2e306
caps.latest.revision: 11
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 11
---
# Comment&#160;: cr&#233;er des touches d&#39;acc&#232;s rapide &#224; l&#39;aide des contr&#244;les Label Windows Forms
Le contrôle Windows Forms <xref:System.Windows.Forms.Label> peut servir à définir des touches d'accès rapide pour d'autres contrôles.  Lorsque vous définissez une touche d'accès rapide dans un contrôle Label, l'utilisateur, en appuyant sur la touche ALT en même temps que sur le caractère que vous avez indiqué, peut déplacer le focus sur le contrôle qui le suit dans l'ordre de tabulation.  Comme les étiquettes ne peuvent pas recevoir le focus, celui\-ci se déplace automatiquement jusqu'au contrôle suivant dans l'ordre de tabulation.  Utilisez cette technique pour assigner des touches d'accès rapide à des zones de texte, à des zones de liste modifiable, à des zones de liste ou encore à des grilles de données.  
  
### Pour assigner une touche d'accès rapide à un contrôle à l'aide d'un contrôle Label  
  
1.  Dessinez le contrôle Label, puis l'autre contrôle.  
  
     ou  
  
     Dessinez les contrôles dans n'importe quel ordre et attribuez à la propriété <xref:System.Windows.Forms.Control.TabIndex%2A> du contrôle Label un numéro de rang inférieur d'une unité à celui de l'autre contrôle.  
  
2.  Affectez la valeur `true` à la propriété <xref:System.Windows.Forms.Label.UseMnemonic%2A> de l'étiquette.  
  
3.  Entrez un signe & dans la propriété <xref:System.Windows.Forms.Label.Text%2A> du contrôle Label pour assigner la touche d'accès rapide de l'étiquette.  Pour plus d'informations, consultez [Création de touches d'accès rapide pour les contrôles Windows Forms](../../../../docs/framework/winforms/controls/how-to-create-access-keys-for-windows-forms-controls.md).  
  
    > [!NOTE]
    >  Il peut arriver que vous vouliez afficher le symbole & dans un contrôle Label au lieu de vous en servir pour créer des touches d'accès rapide.  C'est le cas, par exemple, si vous liez un contrôle Label à un champ d'un recordset dont les données contiennent des et commerciaux \(signe &\).  Pour afficher ce symbole dans un contrôle Label, attribuez à la propriété <xref:System.Windows.Forms.Label.UseMnemonic%2A> la valeur `false`.  Si vous souhaitez afficher des et commerciaux et disposer également de touches d'accès rapide, attribuez à la propriété <xref:System.Windows.Forms.Label.UseMnemonic%2A> la valeur `true`, puis indiquez la touche d'accès rapide par un seul signe & et les et commerciaux par deux signes &.  
  
    ```vb  
    Label1.UseMnemonic = True  
    Label1.Text = "&Print"  
    Label2.UseMnemonic = True  
    Label2.Text = "&Copy && Paste"  
  
    ```  
  
    ```csharp  
    label1.UseMnemonic = true;  
    label1.Text = "&Print";  
    label2.UseMnemonic = true;  
    label2.Text = "&Copy && Paste";  
  
    ```  
  
    ```cpp  
    label1->UseMnemonic = true;  
    label1->Text = "&Print";  
    label2->UseMnemonic = true;  
    label2->Text = "&Copy && Paste";  
    ```  
  
## Voir aussi  
 [Comment : dimensionner un contrôle Label Windows Forms en fonction de son contenu](../../../../docs/framework/winforms/controls/how-to-size-a-windows-forms-label-control-to-fit-its-contents.md)   
 [Vue d'ensemble du contrôle Label](../../../../docs/framework/winforms/controls/label-control-overview-windows-forms.md)   
 [Label, contrôle](../../../../docs/framework/winforms/controls/label-control-windows-forms.md)