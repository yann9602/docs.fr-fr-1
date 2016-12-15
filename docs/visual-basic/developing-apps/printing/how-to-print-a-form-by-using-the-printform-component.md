---
title: "Comment&#160;: imprimer un formulaire &#224; l&#39;aide du composant PrintForm (Visual Basic) | Microsoft Docs"
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
  - "formulaire, impression"
ms.assetid: df963bf6-3ee1-49f4-8b2e-1d95d1beb0be
caps.latest.revision: 19
caps.handback.revision: 19
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Comment&#160;: imprimer un formulaire &#224; l&#39;aide du composant PrintForm (Visual Basic)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Le composant <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm> vous permet d’imprimer rapidement une image d’un formulaire tel qu’il apparaît à l’écran sans utiliser un composant <xref:System.Drawing.Printing.PrintDocument>. Les procédures suivantes montrent comment imprimer un formulaire sur une imprimante, dans une fenêtre d’aperçu avant impression et dans un fichier PostScript encapsulé.  
  
 Les contrôles PowerPack ne sont plus inclus dans Visual Studio, mais vous pouvez les télécharger à partir du [Centre de téléchargement](http://www.microsoft.com/en-us/download/details.aspx?id=25169).  
  
### Pour imprimer un formulaire sur l’imprimante par défaut  
  
1.  Dans la **Boîte à outils**, cliquez sur l’onglet **Visual Basic PowerPacks**, puis faites glisser le composant <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm> sur le formulaire.  
  
     Le composant <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm> est ajouté à la barre d’état des composants.  
  
2.  Dans la fenêtre **Propriétés**, définissez la propriété <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm.PrintAction%2A> sur <xref:System.Drawing.Printing.PrintAction>.  
  
3.  Ajoutez le code suivant dans le gestionnaire d’événements approprié \(par exemple, dans le gestionnaire d’événements `Click` pour un `Button`**Imprimer**\).  
  
    ```  
    PrintForm1.Print()  
    ```  
  
### Pour afficher un formulaire dans une fenêtre d’aperçu avant impression  
  
1.  Dans la **Boîte à outils**, cliquez sur l’onglet **Visual Basic PowerPacks**, puis faites glisser le composant <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm> sur le formulaire.  
  
     Le composant <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm> est ajouté à la barre d’état des composants.  
  
2.  Dans la fenêtre **Propriétés**, définissez la propriété <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm.PrintAction%2A> sur <xref:System.Drawing.Printing.PrintAction>.  
  
3.  Ajoutez le code suivant dans le gestionnaire d’événements approprié \(par exemple, dans le gestionnaire d’événements `Click` pour un `Button`**Imprimer**\).  
  
    ```  
    PrintForm1.Print()  
    ```  
  
### Pour imprimer un formulaire dans un fichier  
  
1.  Dans la **Boîte à outils**, cliquez sur l’onglet **Visual Basic PowerPacks**, puis faites glisser le composant <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm> sur le formulaire.  
  
     Le composant <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm> est ajouté à la barre d’état des composants.  
  
2.  Dans la fenêtre **Propriétés**, définissez la propriété <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm.PrintAction%2A> sur <xref:System.Drawing.Printing.PrintAction>.  
  
3.  Si vous le souhaitez, sélectionnez la propriété <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm.PrintFileName%2A>, puis tapez le chemin complet et le nom de fichier du fichier de destination.  
  
     Si vous ignorez cette étape, l’utilisateur sera invité à entrer un nom de fichier lors de l’exécution.  
  
4.  Ajoutez le code suivant dans le gestionnaire d’événements approprié \(par exemple, dans le gestionnaire d’événements `Click` pour un `Button`**Imprimer**\).  
  
    ```  
    PrintForm1.Print()  
    ```  
  
## Voir aussi  
 <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm.PrintAction%2A>   
 <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm.PrintFileName%2A>   
 [Comment : imprimer la zone cliente d'un formulaire](../../../visual-basic/developing-apps/printing/how-to-print-the-client-area-of-a-form.md)   
 [Comment : imprimer des zones clientes et non clientes d'un formulaire](../../../visual-basic/developing-apps/printing/how-to-print-client-and-non-client-areas-of-a-form.md)   
 [Comment : imprimer un formulaire à défilement variable](../../../visual-basic/developing-apps/printing/how-to-print-a-scrollable-form.md)   
 [PrintForm Component](../../../visual-basic/developing-apps/printing/printform-component.md)