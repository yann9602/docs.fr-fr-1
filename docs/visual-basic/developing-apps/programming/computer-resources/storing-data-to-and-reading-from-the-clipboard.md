---
title: "Storing Data to and Reading from the Clipboard (Visual Basic) | Microsoft Docs"
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
  - "Clipboard, storing data to (My.Computer.Clipboard)"
  - "Clipboard, reading from (My.Computer.Clipboard)"
  - "Clipboard"
  - "My.Computer.Clipboard object, tasks"
  - "data [Visual Basic], Clipboard"
  - "reading data, from Clipboard"
ms.assetid: f690119a-4378-4f7d-b20e-d9377ef49496
caps.latest.revision: 21
caps.handback.revision: 21
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Storing Data to and Reading from the Clipboard (Visual Basic)
[!INCLUDE[vs2017banner](../../../../csharp/includes/vs2017banner.md)]

Le Presse\-papiers peut être utilisé pour stocker des données, telles que du texte et des images.  Comme il est partagé par tous les processus actifs, il peut servir à transférer des données entre ces processus.  L'objet d' `My.Computer.Clipboard` vous permet d'accéder facilement au presse\-papiers et pour lire et écrire lui.  
  
## Lire dans le presse\-papiers  
 Utilisez la méthode d' <xref:Microsoft.VisualBasic.MyServices.ClipboardProxy.GetText%2A> pour lire le texte dans le presse\-papiers.  Le code suivant permet de lire le texte et de l'afficher dans une boîte de message.  Pour que l'exemple s'exécute correctement, du texte doit être stocké dans le Presse\-papiers.  
  
 [!code-vb[VbVbcnMyClipboard#4](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/storing-data-to-and-reading-from-the-clipboard_1.vb)]  
  
 Cet exemple de code est également disponible sous forme d'extrait de code IntelliSense.  Dans le sélecteur d'extrait de code, il se trouve dans **Applications Windows Forms \> Presse\-papiers**.  Pour plus d'informations, consultez [Extraits de code](/visual-studio/ide/code-snippets).  
  
 Utilisez la méthode <xref:Microsoft.VisualBasic.MyServices.ClipboardProxy.GetImage%2A> pour récupérer une image du Presse\-papiers.  Cet exemple vérifie si une image est bien présente dans le Presse\-papiers avant de la récupérer et de l'assigner à  `PictureBox1`.  
  
 [!code-vb[VbResourceTasks#16](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/storing-data-to-and-reading-from-the-clipboard_2.vb)]  
  
 Cet exemple de code est également disponible sous forme d'extrait de code IntelliSense.  Dans le sélecteur d'extrait de code, il se trouve dans **Applications Windows Forms \> Presse\-papiers**.Pour plus d'informations, consultez [Extraits de code](/visual-studio/ide/code-snippets).  
  
 Les éléments placés dans le Presse\-papiers seront persistants même après la fermeture de l'application.  
  
## Détermination du type de fichier stocké dans le presse\-papiers  
 Les données dans le Presse\-papiers peuvent avoir plusieurs formats différents : texte, fichier audio ou image.  Pour déterminer quel type de fichier est dans le Presse\-papiers, vous pouvez utiliser des méthodes telles que <xref:Microsoft.VisualBasic.MyServices.ClipboardProxy.ContainsAudio%2A>, <xref:Microsoft.VisualBasic.MyServices.ClipboardProxy.ContainsFileDropList%2A>, <xref:Microsoft.VisualBasic.MyServices.ClipboardProxy.ContainsImage%2A> et <xref:Microsoft.VisualBasic.MyServices.ClipboardProxy.ContainsText%2A>.  La méthode <xref:Microsoft.VisualBasic.MyServices.ClipboardProxy.ContainsData%2A> peut être utilisée pour vérifier un format personnalisé.  
  
 Utilisez la fonction `ContainsImage` pour déterminer si les données dans le Presse\-papiers correspondent à une image.  Le code suivant vérifie si les données correspondent à une image et indique le résultat.  
  
 [!code-vb[VbResourceTasks#13](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/storing-data-to-and-reading-from-the-clipboard_3.vb)]  
  
## Effacer le presse\-papiers  
 La méthode <xref:Microsoft.VisualBasic.MyServices.ClipboardProxy.Clear%2A> efface toutes les données du Presse\-papiers.  Comme le Presse\-papiers est partagé par d'autres processus, si vous l'effacez, cela peut avoir un impact sur ces processus.  
  
 Le code suivant montre comment utiliser la méthode `Clear`.  
  
 [!code-vb[VbVbcnMyClipboard#3](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/storing-data-to-and-reading-from-the-clipboard_4.vb)]  
  
## Écriture dans le presse\-papiers  
 Utilisez la méthode <xref:Microsoft.VisualBasic.MyServices.ClipboardProxy.SetText%2A> pour écrire du texte dans le Presse\-papiers.  Le code suivant écrit la chaîne "This is a test string" dans le Presse\-papiers.  
  
 [!code-vb[VbVbcnMyClipboard#1](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/storing-data-to-and-reading-from-the-clipboard_5.vb)]  
  
 La méthode d' `SetText` peut accepter un paramètre de format qui contient un type d' <xref:System.Windows.Forms.TextDataFormat>.  Le code suivant écrit la chaîne "This is a test string" au format RTF dans le Presse\-papiers.  
  
 [!code-vb[VbVbcnMyClipboard#2](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/storing-data-to-and-reading-from-the-clipboard_6.vb)]  
  
 Utilisez la méthode <xref:Microsoft.VisualBasic.MyServices.ClipboardProxy.SetData%2A> pour écrire des données dans le Presse\-papiers.  Cet exemple écrit le `DataObject` `dataChunk` dans le Presse\-papiers au format personnalisé `specialFormat`.  
  
 [!code-vb[VbVbcnMyClipboard#7](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/storing-data-to-and-reading-from-the-clipboard_7.vb)]  
  
 Utilisez la méthode <xref:Microsoft.VisualBasic.MyServices.ClipboardProxy.SetAudio%2A> pour écrire les données audio dans le Presse\-papiers.  Dans cet exemple, le tableau d'octets `musicReader` est créé, le fichier `cool.wav` de ce tableau est lu, puis enregistré dans le Presse\-papiers.  
  
 [!code-vb[VbResourceTasks#5](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/storing-data-to-and-reading-from-the-clipboard_8.vb)]  
  
> [!IMPORTANT]
>  Étant donné que d'autres utilisateurs peuvent accéder au Presse\-papiers, ne l'utilisez pas pour stocker des informations sensibles, telles que des mots de passe ou des données confidentielles.  
  
## Voir aussi  
 <xref:Microsoft.VisualBasic.MyServices.ClipboardProxy>   
 <xref:Microsoft.VisualBasic.MyServices.ClipboardProxy.GetAudioStream%2A>   
 <xref:Microsoft.VisualBasic.MyServices.ClipboardProxy.SetDataObject%2A>   
 [Comment : lire des données d’objet à partir d’un fichier XML](../Topic/How%20to:%20Read%20Object%20Data%20from%20an%20XML%20File%20\(C%23%20and%20Visual%20Basic\).md)   
 [Comment : écrire des données d'objet dans un fichier XML](../Topic/How%20to:%20Write%20Object%20Data%20to%20an%20XML%20File%20\(C%23%20and%20Visual%20Basic\).md)