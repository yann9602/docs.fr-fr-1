---
title: Le composant PrintForm (Visual Basic) | Documents Microsoft
ms.date: 2015-07-20
ms.prod: .net
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
dev_langs:
- VB
helpviewer_keywords:
- PrintForm component [Visual Basic]
ms.assetid: 03de98b8-b54c-4764-91d7-83c64e974750
caps.latest.revision: 19
author: stevehoag
ms.author: shoag
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: f0c51ef0131c874ed33af7a19f9145a790d14ade
ms.lasthandoff: 03/13/2017

---
# <a name="printform-component-visual-basic"></a>PrintForm, composant (Visual Basic)
Le <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm>composant [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] vous permet d’imprimer une image d’un Windows Form en cours d’exécution.</xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm> Son comportement remplace celui de la méthode `PrintForm` dans les versions antérieures de Visual Basic.  
  
 Les contrôles PowerPack ne sont plus inclus dans Visual Studio, mais vous pouvez les télécharger à partir du [Centre de téléchargement](http://www.microsoft.com/en-us/download/details.aspx?id=25169).  
  
## <a name="printform-component-overview"></a>Présentation du composant PrintForm  
 Un scénario courant pour Windows Forms est de créer un formulaire qui est mis en forme pour ressembler à un format papier ou à un rapport, puis à imprimer une image du formulaire. Bien que vous puissiez utiliser un <xref:System.Drawing.Printing.PrintDocument>composant pour ce faire, il requiert beaucoup de code.</xref:System.Drawing.Printing.PrintDocument> Le <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm>composant vous permet d’imprimer une image d’un formulaire à une imprimante, à une fenêtre d’aperçu avant impression ou dans un fichier sans utiliser un <xref:System.Drawing.Printing.PrintDocument>composant.</xref:System.Drawing.Printing.PrintDocument> </xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm>  
  
 Le <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm>composant se trouve sur le **Visual Basic PowerPacks** onglet de la **boîte à outils**.</xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm> Quand vous le faites glisser sur un formulaire, il apparaît dans la barre d’état des composants, qui est la petite zone sous la bordure inférieure du formulaire. Quand le composant est sélectionné, les propriétés qui définissent son comportement peuvent être définies dans la fenêtre **Propriétés** . Toutes ces propriétés peuvent également être définies dans le code. Vous pouvez également créer une instance de la <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm>composants dans le code sans ajouter le composant au moment du design.</xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm>  
  
 Quand vous imprimez un formulaire, tous les éléments de la zone cliente du formulaire sont imprimés. Ceci comprend tous les contrôles ainsi que tous les textes et les graphiques dessinés sur le formulaire à l’aide de méthodes de graphiques. Par défaut, la barre de titre, les barres de défilement et les bordures du formulaire ne sont pas imprimées. Également par défaut, le <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm>composant imprime uniquement la partie visible de l’écran.</xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm> Par exemple, si l’utilisateur redimensionne le formulaire au moment de l’exécution, seuls les contrôles et les graphiques qui sont actuellement visibles sont imprimés.  
  
 L’imprimante par défaut utilisé par le <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm>composant est déterminé par les paramètres du Panneau de configuration du système d’exploitation.</xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm>  
  
 Une fois que l’impression est lancée, une norme <xref:System.Drawing.Printing.PrintDocument>boîte de dialogue Imprimer s’affiche.</xref:System.Drawing.Printing.PrintDocument> Cette boîte de dialogue permet aux utilisateurs d’annuler la tâche d’impression.  
  
### <a name="key-methods-properties-and-events"></a>Méthodes, propriétés et événements principaux  
 La méthode de clé de le <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm>composant est le <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm.Print%2A>(méthode), qui permet d’imprimer une image de l’écran pour une imprimante, une fenêtre d’aperçu avant impression ou un fichier.</xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm.Print%2A> </xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm> Il existe deux versions de la <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm.Print%2A>méthode :</xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm.Print%2A>  
  
-   Une version de base sans paramètres :`Print()`  
  
-   Une version surchargée avec des paramètres qui spécifient le comportement d’impression :`Print(printForm As Form, printFormOption As PrintOption)`  
  
     Le paramètre `PrintOption` de la méthode surchargée détermine l’implémentation sous-jacente utilisée pour imprimer le formulaire, si la barre de titre, les barres de défilement et la bordure du formulaire sont imprimées, et si les parties avec défilement  du formulaire sont imprimées.  
  
 Le <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm.PrintAction%2A>propriété est une propriété de clé de le <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm>composant.</xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm> </xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm.PrintAction%2A> Cette propriété détermine si la sortie est envoyée à une imprimante, affichée dans une fenêtre d’aperçu avant impression ou enregistrée comme fichier PostScript encapsulé. Si la <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm.PrintAction%2A>est définie sur <xref:System.Drawing.Printing.PrintAction>, le <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm.PrintFileName%2A>propriété spécifie le chemin d’accès et nom de fichier.</xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm.PrintFileName%2A> </xref:System.Drawing.Printing.PrintAction> </xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm.PrintAction%2A>  
  
 La <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm.PrinterSettings%2A>propriété fournit l’accès à un sous-jacent <xref:System.Drawing.Printing.PrintDocument.PrinterSettings%2A>objet qui vous permet de spécifier des paramètres, tels que l’imprimante à utiliser et le nombre de copies à imprimer.</xref:System.Drawing.Printing.PrintDocument.PrinterSettings%2A> </xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm.PrinterSettings%2A> Vous pouvez également interroger les fonctionnalités de l’imprimante, comme la prise en charge de la couleur ou du recto-verso. Cette propriété n’apparaît pas dans la fenêtre **Propriétés** ; elle est accessible seulement à partir du code.  
  
 Le <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm.Form%2A>propriété est utilisée pour spécifier le formulaire à imprimer lorsque vous appelez le <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm>composant par programmation.</xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm> </xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm.Form%2A> Si le composant est ajouté à un formulaire au moment du design, ce formulaire est le formulaire par défaut.  
  
 Clé d’événements pour le <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm>composant sont les suivantes :</xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm>  
  
-   <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm.BeginPrint>événement.</xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm.BeginPrint> Se produit lorsque la <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm.Print%2A>méthode est appelée et avant la première page de l’impression du document.</xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm.Print%2A>  
  
-   <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm.EndPrint>événement.</xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm.EndPrint> Se produit après que la dernière page est imprimée.  
  
-   <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm.QueryPageSettings>événement.</xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm.QueryPageSettings> Se produit juste avant l'impression de chaque page.  
  
### <a name="remarks"></a>Remarques  
 Si un formulaire contient du texte ou des graphiques dessinés par <xref:System.Drawing.Graphics>méthodes, utilisez la basic <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm.Print%2A>(`Print()`) méthode imprimez-le.</xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm.Print%2A> </xref:System.Drawing.Graphics> Graphiques ne soient pas rendus sur certains systèmes d’exploitation lorsque surchargées <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm.Print%2A>méthode est utilisée.</xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm.Print%2A>  
  
 Si la largeur d’un formulaire est supérieure à la largeur du papier dans l’imprimante, le côté droit du formulaire est tronqué. Quand vous concevez des formulaires pour l’impression, assurez-vous que le formulaire tient sur du papier au format standard.  
  
## <a name="example"></a>Exemple  
 L’exemple suivant montre une utilisation courante de la <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm>composant.</xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm>  
  
```  
' Visual Basic.  
Dim pf As New PrintForm  
pf.Form = Me  
pf.PrintAction = PrintToPrinter  
pf.Print()  
```  
  
## <a name="see-also"></a>Voir aussi  
 <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm.Print%2A></xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm.Print%2A>   
 <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm.PrintAction%2A></xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm.PrintAction%2A>   
 [Comment : imprimer un formulaire à l’aide du composant PrintForm](../../../visual-basic/developing-apps/printing/how-to-print-a-form-by-using-the-printform-component.md)   
 [Comment : imprimer la zone cliente d’un formulaire](../../../visual-basic/developing-apps/printing/how-to-print-the-client-area-of-a-form.md)   
 [Comment : imprimer des zones Non cliente d’un formulaire et](../../../visual-basic/developing-apps/printing/how-to-print-client-and-non-client-areas-of-a-form.md)   
 [Guide pratique : imprimer un formulaire à défilement variable](../../../visual-basic/developing-apps/printing/how-to-print-a-scrollable-form.md)
