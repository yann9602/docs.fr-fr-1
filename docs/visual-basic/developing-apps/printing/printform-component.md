---
title: PrintForm, composant (Visual Basic)
ms.date: 07/20/2015
ms.prod: .net
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords: PrintForm component [Visual Basic]
ms.assetid: 03de98b8-b54c-4764-91d7-83c64e974750
caps.latest.revision: "19"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 890d5a3a3f9c3a737a59e17fef0d4ac0407e9924
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="printform-component-visual-basic"></a>PrintForm, composant (Visual Basic)
Le composant <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm> pour [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] vous permet d’imprimer une image d’un Windows Form au moment de l’exécution. Son comportement remplace celui de la méthode `PrintForm` dans les versions antérieures de Visual Basic.  
  
 Les contrôles PowerPack ne sont plus inclus dans Visual Studio, mais vous pouvez les télécharger à partir du [Centre de téléchargement](http://www.microsoft.com/en-us/download/details.aspx?id=25169).  
  
## <a name="printform-component-overview"></a>Présentation du composant PrintForm  
 Un scénario courant pour Windows Forms est de créer un formulaire qui est mis en forme pour ressembler à un format papier ou à un rapport, puis à imprimer une image du formulaire. Même si vous pouvez utiliser un composant <xref:System.Drawing.Printing.PrintDocument> pour le faire, cela nécessite une grande quantité de code. Le composant <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm> vous permet d’imprimer une image d’un formulaire sur une imprimante, dans une fenêtre d’aperçu avant impression ou dans un fichier, sans utiliser un composant <xref:System.Drawing.Printing.PrintDocument> .  
  
 Le composant <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm> se trouve sous l’onglet **Visual Basic PowerPacks** de la **Boîte à outils**. Quand vous le faites glisser sur un formulaire, il apparaît dans la barre d’état des composants, qui est la petite zone sous la bordure inférieure du formulaire. Quand le composant est sélectionné, les propriétés qui définissent son comportement peuvent être définies dans la fenêtre **Propriétés** . Toutes ces propriétés peuvent également être définies dans le code. Vous pouvez également créer une instance du composant <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm> dans le code sans ajouter le composant au moment du design.  
  
 Quand vous imprimez un formulaire, tous les éléments de la zone cliente du formulaire sont imprimés. Ceci comprend tous les contrôles ainsi que tous les textes et les graphiques dessinés sur le formulaire à l’aide de méthodes de graphiques. Par défaut, la barre de titre, les barres de défilement et les bordures du formulaire ne sont pas imprimées. Toujours par défaut, le composant <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm> imprime seulement la partie visible du formulaire. Par exemple, si l’utilisateur redimensionne le formulaire au moment de l’exécution, seuls les contrôles et les graphiques qui sont actuellement visibles sont imprimés.  
  
 L’imprimante par défaut utilisé par le composant <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm> est déterminée par les paramètres du Panneau de configuration du système d’exploitation.  
  
 Une fois que l’impression est lancée, une boîte de dialogue d’impression <xref:System.Drawing.Printing.PrintDocument> standard est affichée. Cette boîte de dialogue permet aux utilisateurs d’annuler la tâche d’impression.  
  
### <a name="key-methods-properties-and-events"></a>Méthodes, propriétés et événements principaux  
 La méthode principale du composant <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm> est la méthode <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm.Print%2A> , qui imprime une image du formulaire sur une imprimante, dans une fenêtre d’aperçu avant impression ou dans un fichier. Il existe deux versions de la méthode <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm.Print%2A> :  
  
-   Une version de base sans paramètres : `Print()`  
  
-   Une version surchargée avec des paramètres qui spécifient le comportement d’impression : `Print(printForm As Form, printFormOption As PrintOption)`  
  
     Le paramètre `PrintOption` de la méthode surchargée détermine l’implémentation sous-jacente utilisée pour imprimer le formulaire, si la barre de titre, les barres de défilement et la bordure du formulaire sont imprimées, et si les parties avec défilement  du formulaire sont imprimées.  
  
 La propriété <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm.PrintAction%2A> est une propriété clé du composant <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm> . Cette propriété détermine si la sortie est envoyée à une imprimante, affichée dans une fenêtre d’aperçu avant impression ou enregistrée comme fichier PostScript encapsulé. Si la propriété <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm.PrintAction%2A> est définie sur <xref:System.Drawing.Printing.PrintAction.PrintToFile>, la propriété <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm.PrintFileName%2A> spécifie le chemin et le nom du fichier.  
  
 La propriété <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm.PrinterSettings%2A> fournit l’accès à un objet <xref:System.Drawing.Printing.PrintDocument.PrinterSettings%2A> sous-jacent, qui vous permet de spécifier des paramètres comme l’imprimante à utiliser et le nombre de copies à imprimer. Vous pouvez également interroger les fonctionnalités de l’imprimante, comme la prise en charge de la couleur ou du recto-verso. Cette propriété n’apparaît pas dans la fenêtre **Propriétés** ; elle est accessible seulement à partir du code.  
  
 La propriété <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm.Form%2A> est utilisée pour spécifier le formulaire à imprimer quand vous appelez le composant <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm> par programmation. Si le composant est ajouté à un formulaire au moment du design, ce formulaire est le formulaire par défaut.  
  
 Les principaux événements pour le composant <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm> sont les suivants :  
  
-   Événement<xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm.BeginPrint> . Se produit quand la méthode <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm.Print%2A> est appelée et avant l’impression de la première page du document.  
  
-   Événement<xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm.EndPrint> . Se produit après que la dernière page est imprimée.  
  
-   Événement<xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm.QueryPageSettings> . Se produit juste avant l'impression de chaque page.  
  
### <a name="remarks"></a>Notes  
 Si un formulaire contient du texte ou des graphiques dessinés par des méthodes <xref:System.Drawing.Graphics> , utilisez la méthode <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm.Print%2A> (`Print()`) de base pour l’imprimer. Des graphiques peuvent ne pas être rendus sur certains systèmes d’exploitation quand la méthode <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm.Print%2A> surchargée est utilisée.  
  
 Si la largeur d’un formulaire est supérieure à la largeur du papier dans l’imprimante, le côté droit du formulaire est tronqué. Quand vous concevez des formulaires pour l’impression, assurez-vous que le formulaire tient sur du papier au format standard.  
  
## <a name="example"></a>Exemple  
 L’exemple suivant montre une utilisation courante du composant <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm> .  
  
```  
' Visual Basic.  
Dim pf As New PrintForm  
pf.Form = Me  
pf.PrintAction = PrintToPrinter  
pf.Print()  
```  
  
## <a name="see-also"></a>Voir aussi  
 <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm.Print%2A>  
 <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm.PrintAction%2A>  
 [Guide pratique : imprimer un formulaire à l’aide du composant PrintForm](../../../visual-basic/developing-apps/printing/how-to-print-a-form-by-using-the-printform-component.md)  
 [Guide pratique : imprimer la zone cliente d’un formulaire](../../../visual-basic/developing-apps/printing/how-to-print-the-client-area-of-a-form.md)  
 [Guide pratique : imprimer des zones clientes et non clientes d’un formulaire](../../../visual-basic/developing-apps/printing/how-to-print-client-and-non-client-areas-of-a-form.md)  
 [Guide pratique : imprimer un formulaire à défilement variable](../../../visual-basic/developing-apps/printing/how-to-print-a-scrollable-form.md)
