---
title: "Comment&#160;: r&#233;assignation de contr&#244;les existants &#224; un parent diff&#233;rent | Microsoft Docs"
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
  - "contrôles de conteneur (Windows Forms)"
  - "disposition (Windows Forms), redimensionner"
  - "disposition (Windows Forms), contrôles enfants"
ms.assetid: 5a5723ff-34e0-4b6f-a57b-be4ebe35cb34
caps.latest.revision: 7
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 7
---
# Comment&#160;: r&#233;assignation de contr&#244;les existants &#224; un parent diff&#233;rent
Vous pouvez affecter des contrôles qui existent sur votre formulaire à un nouveau contrôle de conteneur.  
  
> [!NOTE]
>  Les boîtes de dialogue et les commandes de menu qui s'affichent peuvent être différentes de celles qui sont décrites dans l'aide, en fonction de vos paramètres actifs ou de l'édition utilisée. Pour modifier vos paramètres, choisissez **Importation et exportation de paramètres** dans le menu **Outils**. Pour plus d’informations, consultez [Personnalisation des paramètres de développement dans Visual Studio](http://msdn.microsoft.com/fr-fr/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
### Pour réaffecter des contrôles existants à un autre parent  
  
1.  Faites glisser trois contrôles <xref:System.Windows.Forms.Button> de la **Boîte à outils** vers le formulaire.  
  
     Placez\-les près les uns des autres, mais laissez\-les non alignés.  
  
2.  Dans la **Boîte à outils**, cliquez sur l’icône de contrôle <xref:System.Windows.Forms.FlowLayoutPanel>.  
  
     Ne faites pas glisser l’icône vers le formulaire.  
  
3.  Déplacez le pointeur de la souris près des trois contrôles <xref:System.Windows.Forms.Button>.  
  
     Le pointeur devient une croix à laquelle est attachée l’icône de contrôle <xref:System.Windows.Forms.FlowLayoutPanel>.  
  
4.  Cliquez et maintenez le bouton de la souris enfoncé.  
  
5.  Faites glisser le pointeur de la souris pour dessiner le contour du contrôle <xref:System.Windows.Forms.FlowLayoutPanel>.  
  
6.  Dessinez le contour autour des trois contrôles <xref:System.Windows.Forms.Button>.  
  
7.  Relâchez le bouton de la souris.  
  
     Les trois contrôles <xref:System.Windows.Forms.Button> sont maintenant insérés dans le contrôle <xref:System.Windows.Forms.FlowLayoutPanel>.  
  
## Voir aussi  
 <xref:System.Windows.Forms.FlowLayoutPanel>   
 <xref:System.Windows.Forms.TableLayoutPanel>   
 [Disposition des contrôles dans les Windows Forms](../../../../docs/framework/winforms/controls/arranging-controls-on-windows-forms.md)   
 [Procédure pas à pas : organisation des contrôles dans les Windows Forms à l'aide d'un TableLayoutPanel](../../../../docs/framework/winforms/controls/walkthrough-arranging-controls-on-windows-forms-using-a-tablelayoutpanel.md)   
 [Procédure pas à pas : organisation des contrôles dans les Windows Forms à l'aide des lignes d'alignement \(SnapLines\)](../../../../docs/framework/winforms/controls/walkthrough-arranging-controls-on-windows-forms-using-snaplines.md)