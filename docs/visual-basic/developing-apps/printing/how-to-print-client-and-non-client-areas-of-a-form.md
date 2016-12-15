---
title: "Comment&#160;: imprimer des zones clientes et non clientes d&#39;un formulaire (Visual Basic) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "barre de titre, impression"
  - "imprimer"
  - "bordures, impression"
  - "formulaire complet"
  - "zone non cliente, impression"
ms.assetid: 856bb0e4-dbc3-47e2-81cd-4b376cf07757
caps.latest.revision: 17
caps.handback.revision: 17
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Comment&#160;: imprimer des zones clientes et non clientes d&#39;un formulaire (Visual Basic)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Le composant <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm> vous permet d’imprimer rapidement une image d’un formulaire tel qu’il apparaît à l’écran sans utiliser un composant <xref:System.Drawing.Printing.PrintDocument>. La procédure suivante montre comment imprimer un formulaire, y compris la zone cliente et la zone non cliente. La zone non cliente comprend la barre de titre, les bordures et les barres de défilement.  
  
 Les contrôles PowerPack ne sont plus inclus dans Visual Studio, mais vous pouvez les télécharger à partir du [Centre de téléchargement](http://www.microsoft.com/en-us/download/details.aspx?id=25169).  
  
### Pour imprimer à la fois les zones clientes et les zones non clientes d’un formulaire  
  
1.  Dans la **Boîte à outils**, cliquez sur l’onglet **Visual Basic PowerPacks**, puis faites glisser le composant <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm> sur le formulaire.  
  
     Le composant <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm> est ajouté à la barre d’état des composants.  
  
2.  Dans la fenêtre **Propriétés**, définissez la propriété <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm.PrintAction%2A> sur <xref:System.Drawing.Printing.PrintAction>.  
  
3.  Ajoutez le code suivant dans le gestionnaire d’événements approprié \(par exemple, dans le  gestionnaire d’événements `Click` pour un `Button` Imprimer\).  
  
    ```  
    PrintForm1.Print(Me, PowerPacks.Printing.PrintForm.PrintOption.FullWindow)  
    ```  
  
    > [!NOTE]
    >  Sur certains systèmes d’exploitation, le texte ou les graphiques dessinés par des méthodes <xref:System.Drawing.Graphics> peuvent ne pas s’imprimer correctement. Dans ce cas, utilisez la méthode d’impression compatible : `PrintForm1.Print(Me, PowerPacks.Printing.PrintForm.PrintOption.CompatibleModeFullWindow`\).  
  
## Voir aussi  
 <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm.PrintAction%2A>   
 <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm.Print%2A>   
 [PrintForm Component](../../../visual-basic/developing-apps/printing/printform-component.md)   
 [Comment : imprimer un formulaire à défilement variable](../../../visual-basic/developing-apps/printing/how-to-print-a-scrollable-form.md)