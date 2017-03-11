---
title: "Comment&#160;: imprimer un formulaire &#224; d&#233;filement variable (Visual Basic) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "formulaire complet, impression"
  - "formulaires à défilement, impression"
ms.assetid: 1196e1cf-b77f-4928-a3e4-85b51ba3787d
caps.latest.revision: 15
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 15
---
# Comment&#160;: imprimer un formulaire &#224; d&#233;filement variable (Visual Basic)
[!INCLUDE[vs2017banner](../../../visual-basic/includes/vs2017banner.md)]

Le composant <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm> vous permet d’imprimer rapidement une image d’un formulaire sans utiliser un composant <xref:System.Drawing.Printing.PrintDocument>. Par défaut, seule la partie actuellement visible du formulaire est imprimée ; si un utilisateur a redimensionné le formulaire au moment de l’exécution, l’image ne peut pas être imprimée comme prévu. La procédure suivante montre comment imprimer la zone cliente complète d’un formulaire avec défilement, même si le formulaire a été redimensionné.  
  
 Les contrôles PowerPack ne sont plus inclus dans Visual Studio, mais vous pouvez les télécharger à partir du [Centre de téléchargement](http://www.microsoft.com/en-us/download/details.aspx?id=25169).  
  
### Pour imprimer la zone cliente complète d’un formulaire avec défilement  
  
1.  Dans la **Boîte à outils**, cliquez sur l’onglet **Visual Basic PowerPacks**, puis faites glisser le composant <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm> sur le formulaire.  
  
     Le composant <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm> va être ajouté à la barre d’état des composants.  
  
2.  Dans la fenêtre **Propriétés**, définissez la propriété <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm.PrintAction%2A> sur <xref:System.Drawing.Printing.PrintAction>.  
  
3.  Ajoutez le code suivant dans le gestionnaire d’événements approprié \(par exemple, dans le gestionnaire d’événements `Click` pour un `Button`**Imprimer**\).  
  
    ```  
    PrintForm1.Print(Me, PowerPacks.Printing.PrintForm.PrintOption.Scrollable)  
    ```  
  
    > [!NOTE]
    >  Sur certains systèmes d’exploitation, le texte ou les graphiques dessinés par des méthodes <xref:System.Drawing.Graphics> peuvent ne pas s’imprimer correctement. Dans ce cas, vous ne pourrez pas imprimer avec le paramètre `Scrollable`.  
  
## Voir aussi  
 <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm.PrintAction%2A>   
 <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm.Print%2A>   
 [PrintForm Component](../../../visual-basic/developing-apps/printing/printform-component.md)   
 [Comment : imprimer la zone cliente d'un formulaire](../../../visual-basic/developing-apps/printing/how-to-print-the-client-area-of-a-form.md)   
 [Comment : imprimer des zones clientes et non clientes d'un formulaire](../../../visual-basic/developing-apps/printing/how-to-print-client-and-non-client-areas-of-a-form.md)