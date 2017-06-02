---
title: "Stockage de données dans le Presse-papiers et lecture du Presse-papiers (Visual Basic) | Microsoft Docs"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
dev_langs:
- VB
helpviewer_keywords:
- Clipboard, storing data to (My.Computer.Clipboard)
- Clipboard, reading from (My.Computer.Clipboard)
- Clipboard
- My.Computer.Clipboard object, tasks
- data [Visual Basic], Clipboard
- reading data, from Clipboard
ms.assetid: f690119a-4378-4f7d-b20e-d9377ef49496
caps.latest.revision: 21
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Human Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: 06a97ffe88fdae344b07d04b6ce560d4c163d431
ms.contentlocale: fr-fr
ms.lasthandoff: 05/22/2017

---
# <a name="storing-data-to-and-reading-from-the-clipboard-visual-basic"></a>Stockage de données dans le Presse-papiers et lecture du Presse-papiers (Visual Basic)
Le Presse-papiers peut être utilisé pour stocker des données, telles que du texte et des images. Comme le Presse-papiers est partagé par tous les processus actifs, il peut être utilisé pour transférer des données entre ces processus. L’objet `My.Computer.Clipboard` permet d’accéder facilement au Presse-papiers et de lire et écrire dedans.  
  
## <a name="reading-from-the-clipboard"></a>Lecture à partir du Presse-papiers  
 Utilisez la méthode <xref:Microsoft.VisualBasic.MyServices.ClipboardProxy.GetText%2A> pour lire le texte dans le Presse-papiers. Le code suivant lit le texte et l’affiche dans une boîte de message. Du texte doit être stocké dans le Presse-papiers pour que l’exemple s’exécute correctement.  
  
 [!code-vb[VbVbcnMyClipboard#4](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/storing-data-to-and-reading-from-the-clipboard_1.vb)]  
  
 Cet exemple de code est également disponible sous la forme d’un extrait de code IntelliSense. Dans le sélecteur d’extraits de code, il se trouve dans **Applications Windows Forms > Presse-papiers**. Pour plus d’informations, consultez [Extraits de code](https://docs.microsoft.com/visualstudio/ide/code-snippets).  
  
 Utilisez la méthode <xref:Microsoft.VisualBasic.MyServices.ClipboardProxy.GetImage%2A> pour récupérer une image à partir du Presse-papiers. Cet exemple vérifie si une image se trouve dans le Presse-papiers avant de la récupérer et de l’assigner à `PictureBox1`.  
  
 [!code-vb[VbResourceTasks#16](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/storing-data-to-and-reading-from-the-clipboard_2.vb)]  
  
 Cet exemple de code est également disponible sous la forme d’un extrait de code IntelliSense. Dans le sélecteur d’extraits de code, il se trouve dans **Applications Windows Forms > Presse-papiers**. Pour plus d’informations, consultez [Extraits de Code](https://docs.microsoft.com/visualstudio/ide/code-snippets).  
  
 Les éléments placés dans le Presse-papiers sont conservés même après l’arrêt de l’application.  
  
## <a name="determining-the-type-of-file-stored-in-the-clipboard"></a>Détermination du type de fichier stocké dans le Presse-papiers  
 Les données du Presse-papiers peuvent présenter différentes formes, telles que du texte, un fichier audio ou une image. Pour déterminer le type de fichier qui se trouve dans le Presse-papiers, vous pouvez utiliser des méthodes telles que <xref:Microsoft.VisualBasic.MyServices.ClipboardProxy.ContainsAudio%2A>, <xref:Microsoft.VisualBasic.MyServices.ClipboardProxy.ContainsFileDropList%2A>, <xref:Microsoft.VisualBasic.MyServices.ClipboardProxy.ContainsImage%2A> et <xref:Microsoft.VisualBasic.MyServices.ClipboardProxy.ContainsText%2A>. Vous pouvez utiliser la méthode <xref:Microsoft.VisualBasic.MyServices.ClipboardProxy.ContainsData%2A> si vous avez un format personnalisé que vous souhaitez vérifier.  
  
 Utilisez la fonction `ContainsImage` pour déterminer si les données contenues dans le Presse-papiers sont une image. Le code suivant vérifie si les données sont une image et en rend compte en conséquence.  
  
 [!code-vb[VbResourceTasks#13](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/storing-data-to-and-reading-from-the-clipboard_3.vb)]  
  
## <a name="clearing-the-clipboard"></a>Effacement du contenu du Presse-papiers  
 La méthode <xref:Microsoft.VisualBasic.MyServices.ClipboardProxy.Clear%2A> efface le Presse-papiers. Comme le Presse-papiers est partagé par d’autres processus, l’effacement de son contenu peut avoir un impact sur ces processus.  
  
 Le code suivant met en œuvre la méthode `Clear`.  
  
 [!code-vb[VbVbcnMyClipboard#3](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/storing-data-to-and-reading-from-the-clipboard_4.vb)]  
  
## <a name="writing-to-the-clipboard"></a>Écriture dans le Presse-papiers  
 Utilisez la méthode <xref:Microsoft.VisualBasic.MyServices.ClipboardProxy.SetText%2A> pour écrire du texte dans le Presse-papiers. Le code suivant écrit la chaîne « This is a test string » dans le Presse-papiers.  
  
 [!code-vb[VbVbcnMyClipboard#1](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/storing-data-to-and-reading-from-the-clipboard_5.vb)]  
  
 La méthode `SetText` peut accepter un paramètre de format qui contient un type de <xref:System.Windows.Forms.TextDataFormat>. Le code suivant écrit la chaîne « This is a test string » dans le Presse-papiers sous la forme de texte RTF.  
  
 [!code-vb[VbVbcnMyClipboard#2](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/storing-data-to-and-reading-from-the-clipboard_6.vb)]  
  
 Utilisez la méthode <xref:Microsoft.VisualBasic.MyServices.ClipboardProxy.SetData%2A> pour écrire des données dans le Presse-papiers. Cet exemple écrit `DataObject``dataChunk` dans le Presse-papiers au format personnalisé `specialFormat`.  
  
 [!code-vb[VbVbcnMyClipboard#7](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/storing-data-to-and-reading-from-the-clipboard_7.vb)]  
  
 Utilisez la méthode <xref:Microsoft.VisualBasic.MyServices.ClipboardProxy.SetAudio%2A> pour écrire des données audio dans le Presse-papiers. Cet exemple crée le tableau d’octets `musicReader`, lit le fichier `cool.wav`, puis l’écrit dans le Presse-papiers.  
  
 [!code-vb[VbResourceTasks#5](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/storing-data-to-and-reading-from-the-clipboard_8.vb)]  
  
> [!IMPORTANT]
>  Étant donné que le Presse-papiers est accessible par d’autres utilisateurs, ne l’utilisez pas pour stocker des informations sensibles, telles que des mots de passe ou des données confidentielles.  
  
## <a name="see-also"></a>Voir aussi  
 <xref:Microsoft.VisualBasic.MyServices.ClipboardProxy>   
 <xref:Microsoft.VisualBasic.MyServices.ClipboardProxy.GetAudioStream%2A>   
 <xref:Microsoft.VisualBasic.MyServices.ClipboardProxy.SetDataObject%2A>   
 [Guide pratique pour lire des données d’objet à partir d’un fichier XML](../../../programming-guide/concepts/serialization/how-to-read-object-data-from-an-xml-file.md)   
 [Guide pratique : écrire des données d’objet dans un fichier XML](../../../programming-guide/concepts/serialization/how-to-write-object-data-to-an-xml-file.md)
