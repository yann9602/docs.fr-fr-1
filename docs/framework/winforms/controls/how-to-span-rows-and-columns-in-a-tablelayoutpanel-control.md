---
title: "Comment&#160;: &#233;tendre des lignes et des colonnes dans un contr&#244;le TableLayoutPanel | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-winforms"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "net.ComponentModel.StyleCollectionEditor.TLP.SpanRowsColumns"
dev_langs: 
  - "jsharp"
helpviewer_keywords: 
  - "cellules, fusionner"
  - "colonnes (Windows Forms), répartir"
  - "fusionner les cellules"
  - "lignes (Windows Forms), répartir"
  - "TableLayoutPanel (contrôle Windows Forms), fixer la mesure des lignes et des colonnes"
ms.assetid: a8a2fdd3-a848-48b0-a4cd-4e85ebded87e
caps.latest.revision: 8
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 8
---
# Comment&#160;: &#233;tendre des lignes et des colonnes dans un contr&#244;le TableLayoutPanel
Les contrôles dans un contrôle <xref:System.Windows.Forms.TableLayoutPanel> peuvent couvrir des colonnes et des lignes adjacentes.  
  
> [!NOTE]
>  Les boîtes de dialogue et les commandes de menu qui s'affichent peuvent être différentes de celles qui sont décrites dans l'aide, en fonction de vos paramètres actifs ou de l'édition utilisée.  Pour modifier vos paramètres, choisissez **Importation et exportation de paramètres** dans le menu **Outils**.  Pour plus d'informations, consultez [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/fr-fr/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
### Pour couvrir des colonnes et des lignes  
  
1.  Faites glisser un contrôle <xref:System.Windows.Forms.TableLayoutPanel> de la **Boîte à outils** vers votre formulaire.  
  
2.  Faites glisser un contrôle <xref:System.Windows.Forms.Button> de la **Boîte à outils** vers la cellule supérieure gauche du contrôle <xref:System.Windows.Forms.TableLayoutPanel>.  
  
3.  Affectez à la propriété **ColumnSpan** du contrôle <xref:System.Windows.Forms.Button> la valeur 2.  Notez que le contrôle <xref:System.Windows.Forms.Button> couvre les première et deuxième colonnes.  
  
4.  Affectez la valeur 2 à la propriété **RowSpan** du contrôle <xref:System.Windows.Forms.Button>.  Notez que le contrôle <xref:System.Windows.Forms.Button> couvre les première et deuxième lignes.  
  
5.  Affectez à la propriété **ColumnSpan** du contrôle <xref:System.Windows.Forms.Button> la valeur 1.  Notez que le contrôle <xref:System.Windows.Forms.Button> se déplace dans la première colonne et couvre les première et deuxième lignes.  
  
## Voir aussi  
 [TableLayoutPanel, contrôle](../../../../docs/framework/winforms/controls/tablelayoutpanel-control-windows-forms.md)