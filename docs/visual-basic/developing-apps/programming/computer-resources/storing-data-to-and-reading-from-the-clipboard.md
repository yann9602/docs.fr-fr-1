---
title: "Stockage de données dans le Presse-papiers et lecture du Presse-papiers (Visual Basic)"
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
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 3b60942cf3e3a7f588a7838bcae0cb7b6fae2278
ms.contentlocale: fr-fr
ms.lasthandoff: 07/28/2017

---
# <a name="storing-data-to-and-reading-from-the-clipboard-visual-basic"></a><span data-ttu-id="c1e59-102">Stockage de données dans le Presse-papiers et lecture du Presse-papiers (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c1e59-102">Storing data to and reading from the Clipboard (Visual Basic)</span></span>
<span data-ttu-id="c1e59-103">Le Presse-papiers peut être utilisé pour stocker des données, telles que du texte et des images.</span><span class="sxs-lookup"><span data-stu-id="c1e59-103">The Clipboard can be used to store data, such as text and images.</span></span> <span data-ttu-id="c1e59-104">Comme le Presse-papiers est partagé par tous les processus actifs, il peut être utilisé pour transférer des données entre ces processus.</span><span class="sxs-lookup"><span data-stu-id="c1e59-104">Because the Clipboard is shared by all active processes, it can be used to transfer data between them.</span></span> <span data-ttu-id="c1e59-105">L’objet `My.Computer.Clipboard` permet d’accéder facilement au Presse-papiers et de lire et écrire dedans.</span><span class="sxs-lookup"><span data-stu-id="c1e59-105">The `My.Computer.Clipboard` object allows you to easily access the Clipboard and to read from and write to it.</span></span>  
  
## <a name="reading-from-the-clipboard"></a><span data-ttu-id="c1e59-106">Lecture à partir du Presse-papiers</span><span class="sxs-lookup"><span data-stu-id="c1e59-106">Reading from the Clipboard</span></span>  
 <span data-ttu-id="c1e59-107">Utilisez la méthode <xref:Microsoft.VisualBasic.MyServices.ClipboardProxy.GetText%2A> pour lire le texte dans le Presse-papiers.</span><span class="sxs-lookup"><span data-stu-id="c1e59-107">Use the <xref:Microsoft.VisualBasic.MyServices.ClipboardProxy.GetText%2A> method to read the text in the Clipboard.</span></span> <span data-ttu-id="c1e59-108">Le code suivant lit le texte et l’affiche dans une boîte de message.</span><span class="sxs-lookup"><span data-stu-id="c1e59-108">The following code reads the text and displays it in a message box.</span></span> <span data-ttu-id="c1e59-109">Du texte doit être stocké dans le Presse-papiers pour que l’exemple s’exécute correctement.</span><span class="sxs-lookup"><span data-stu-id="c1e59-109">There must be text stored on the Clipboard for the example to run correctly.</span></span>  
  
 <span data-ttu-id="c1e59-110">[!code-vb[VbVbcnMyClipboard#4](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/storing-data-to-and-reading-from-the-clipboard_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="c1e59-110">[!code-vb[VbVbcnMyClipboard#4](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/storing-data-to-and-reading-from-the-clipboard_1.vb)]</span></span>  
  
 <span data-ttu-id="c1e59-111">Cet exemple de code est également disponible sous la forme d’un extrait de code IntelliSense.</span><span class="sxs-lookup"><span data-stu-id="c1e59-111">This code example is also available as an IntelliSense code snippet.</span></span> <span data-ttu-id="c1e59-112">Dans le sélecteur d’extraits de code, il se trouve dans **Applications Windows Forms > Presse-papiers**.</span><span class="sxs-lookup"><span data-stu-id="c1e59-112">In the code snippet picker, it is located in **Windows Forms Applications > Clipboard**.</span></span> <span data-ttu-id="c1e59-113">Pour plus d’informations, consultez [Extraits de code](/visualstudio/ide/code-snippets).</span><span class="sxs-lookup"><span data-stu-id="c1e59-113">For more information, see [Code Snippets](/visualstudio/ide/code-snippets).</span></span>  
  
 <span data-ttu-id="c1e59-114">Utilisez la méthode <xref:Microsoft.VisualBasic.MyServices.ClipboardProxy.GetImage%2A> pour récupérer une image à partir du Presse-papiers.</span><span class="sxs-lookup"><span data-stu-id="c1e59-114">Use the <xref:Microsoft.VisualBasic.MyServices.ClipboardProxy.GetImage%2A> method to retrieve an image from the Clipboard.</span></span> <span data-ttu-id="c1e59-115">Cet exemple vérifie si une image se trouve dans le Presse-papiers avant de la récupérer et de l’assigner à `PictureBox1`.</span><span class="sxs-lookup"><span data-stu-id="c1e59-115">This example checks to see if there is an image on the Clipboard before retrieving it and assigning it to `PictureBox1`.</span></span>  
  
 <span data-ttu-id="c1e59-116">[!code-vb[VbResourceTasks#16](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/storing-data-to-and-reading-from-the-clipboard_2.vb)]</span><span class="sxs-lookup"><span data-stu-id="c1e59-116">[!code-vb[VbResourceTasks#16](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/storing-data-to-and-reading-from-the-clipboard_2.vb)]</span></span>  
  
 <span data-ttu-id="c1e59-117">Cet exemple de code est également disponible sous la forme d’un extrait de code IntelliSense.</span><span class="sxs-lookup"><span data-stu-id="c1e59-117">This code example is also available as an IntelliSense code snippet.</span></span> <span data-ttu-id="c1e59-118">Dans le sélecteur d’extraits de code, il se trouve dans **Applications Windows Forms > Presse-papiers**. Pour plus d’informations, consultez [Extraits de Code](/visualstudio/ide/code-snippets).</span><span class="sxs-lookup"><span data-stu-id="c1e59-118">In the code snippet picker, it is located in **Windows Forms Applications > Clipboard**.For more information, see [Code Snippets](/visualstudio/ide/code-snippets).</span></span>  
  
 <span data-ttu-id="c1e59-119">Les éléments placés dans le Presse-papiers sont conservés même après l’arrêt de l’application.</span><span class="sxs-lookup"><span data-stu-id="c1e59-119">Items placed on the Clipboard will persist even after the application is shut down.</span></span>  
  
## <a name="determining-the-type-of-file-stored-in-the-clipboard"></a><span data-ttu-id="c1e59-120">Détermination du type de fichier stocké dans le Presse-papiers</span><span class="sxs-lookup"><span data-stu-id="c1e59-120">Determining the type of file stored in the Clipboard</span></span>  
 <span data-ttu-id="c1e59-121">Les données du Presse-papiers peuvent présenter différentes formes, telles que du texte, un fichier audio ou une image.</span><span class="sxs-lookup"><span data-stu-id="c1e59-121">Data on the Clipboard may take a number of different forms, such as text, an audio file, or an image.</span></span> <span data-ttu-id="c1e59-122">Pour déterminer le type de fichier qui se trouve dans le Presse-papiers, vous pouvez utiliser des méthodes telles que <xref:Microsoft.VisualBasic.MyServices.ClipboardProxy.ContainsAudio%2A>, <xref:Microsoft.VisualBasic.MyServices.ClipboardProxy.ContainsFileDropList%2A>, <xref:Microsoft.VisualBasic.MyServices.ClipboardProxy.ContainsImage%2A> et <xref:Microsoft.VisualBasic.MyServices.ClipboardProxy.ContainsText%2A>.</span><span class="sxs-lookup"><span data-stu-id="c1e59-122">In order to determine what sort of file is on the Clipboard, you can use methods such as <xref:Microsoft.VisualBasic.MyServices.ClipboardProxy.ContainsAudio%2A>, <xref:Microsoft.VisualBasic.MyServices.ClipboardProxy.ContainsFileDropList%2A>, <xref:Microsoft.VisualBasic.MyServices.ClipboardProxy.ContainsImage%2A>, and <xref:Microsoft.VisualBasic.MyServices.ClipboardProxy.ContainsText%2A>.</span></span> <span data-ttu-id="c1e59-123">Vous pouvez utiliser la méthode <xref:Microsoft.VisualBasic.MyServices.ClipboardProxy.ContainsData%2A> si vous avez un format personnalisé que vous souhaitez vérifier.</span><span class="sxs-lookup"><span data-stu-id="c1e59-123">The <xref:Microsoft.VisualBasic.MyServices.ClipboardProxy.ContainsData%2A> method can be used if you have a custom format that you want to check.</span></span>  
  
 <span data-ttu-id="c1e59-124">Utilisez la fonction `ContainsImage` pour déterminer si les données contenues dans le Presse-papiers sont une image.</span><span class="sxs-lookup"><span data-stu-id="c1e59-124">Use the `ContainsImage` function to determine whether the data contained on the Clipboard is an image.</span></span> <span data-ttu-id="c1e59-125">Le code suivant vérifie si les données sont une image et en rend compte en conséquence.</span><span class="sxs-lookup"><span data-stu-id="c1e59-125">The following code checks to see whether the data is an image and reports accordingly.</span></span>  
  
 <span data-ttu-id="c1e59-126">[!code-vb[VbResourceTasks#13](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/storing-data-to-and-reading-from-the-clipboard_3.vb)]</span><span class="sxs-lookup"><span data-stu-id="c1e59-126">[!code-vb[VbResourceTasks#13](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/storing-data-to-and-reading-from-the-clipboard_3.vb)]</span></span>  
  
## <a name="clearing-the-clipboard"></a><span data-ttu-id="c1e59-127">Effacement du contenu du Presse-papiers</span><span class="sxs-lookup"><span data-stu-id="c1e59-127">Clearing the Clipboard</span></span>  
 <span data-ttu-id="c1e59-128">La méthode <xref:Microsoft.VisualBasic.MyServices.ClipboardProxy.Clear%2A> efface le Presse-papiers.</span><span class="sxs-lookup"><span data-stu-id="c1e59-128">The <xref:Microsoft.VisualBasic.MyServices.ClipboardProxy.Clear%2A> method clears the Clipboard.</span></span> <span data-ttu-id="c1e59-129">Comme le Presse-papiers est partagé par d’autres processus, l’effacement de son contenu peut avoir un impact sur ces processus.</span><span class="sxs-lookup"><span data-stu-id="c1e59-129">Because the Clipboard is shared by other processes, clearing it may have an impact on those processes.</span></span>  
  
 <span data-ttu-id="c1e59-130">Le code suivant met en œuvre la méthode `Clear`.</span><span class="sxs-lookup"><span data-stu-id="c1e59-130">The following code shows how to use the `Clear` method.</span></span>  
  
 <span data-ttu-id="c1e59-131">[!code-vb[VbVbcnMyClipboard#3](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/storing-data-to-and-reading-from-the-clipboard_4.vb)]</span><span class="sxs-lookup"><span data-stu-id="c1e59-131">[!code-vb[VbVbcnMyClipboard#3](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/storing-data-to-and-reading-from-the-clipboard_4.vb)]</span></span>  
  
## <a name="writing-to-the-clipboard"></a><span data-ttu-id="c1e59-132">Écriture dans le Presse-papiers</span><span class="sxs-lookup"><span data-stu-id="c1e59-132">Writing to the Clipboard</span></span>  
 <span data-ttu-id="c1e59-133">Utilisez la méthode <xref:Microsoft.VisualBasic.MyServices.ClipboardProxy.SetText%2A> pour écrire du texte dans le Presse-papiers.</span><span class="sxs-lookup"><span data-stu-id="c1e59-133">Use the <xref:Microsoft.VisualBasic.MyServices.ClipboardProxy.SetText%2A> method to write text to the Clipboard.</span></span> <span data-ttu-id="c1e59-134">Le code suivant écrit la chaîne « This is a test string » dans le Presse-papiers.</span><span class="sxs-lookup"><span data-stu-id="c1e59-134">The following code writes the string "This is a test string" to the Clipboard.</span></span>  
  
 <span data-ttu-id="c1e59-135">[!code-vb[VbVbcnMyClipboard#1](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/storing-data-to-and-reading-from-the-clipboard_5.vb)]</span><span class="sxs-lookup"><span data-stu-id="c1e59-135">[!code-vb[VbVbcnMyClipboard#1](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/storing-data-to-and-reading-from-the-clipboard_5.vb)]</span></span>  
  
 <span data-ttu-id="c1e59-136">La méthode `SetText` peut accepter un paramètre de format qui contient un type de <xref:System.Windows.Forms.TextDataFormat>.</span><span class="sxs-lookup"><span data-stu-id="c1e59-136">The `SetText` method can accept a format parameter that contains a type of <xref:System.Windows.Forms.TextDataFormat>.</span></span> <span data-ttu-id="c1e59-137">Le code suivant écrit la chaîne « This is a test string » dans le Presse-papiers sous la forme de texte RTF.</span><span class="sxs-lookup"><span data-stu-id="c1e59-137">The following code writes the string "This is a test string" to the Clipboard as RTF text.</span></span>  
  
 <span data-ttu-id="c1e59-138">[!code-vb[VbVbcnMyClipboard#2](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/storing-data-to-and-reading-from-the-clipboard_6.vb)]</span><span class="sxs-lookup"><span data-stu-id="c1e59-138">[!code-vb[VbVbcnMyClipboard#2](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/storing-data-to-and-reading-from-the-clipboard_6.vb)]</span></span>  
  
 <span data-ttu-id="c1e59-139">Utilisez la méthode <xref:Microsoft.VisualBasic.MyServices.ClipboardProxy.SetData%2A> pour écrire des données dans le Presse-papiers.</span><span class="sxs-lookup"><span data-stu-id="c1e59-139">Use the <xref:Microsoft.VisualBasic.MyServices.ClipboardProxy.SetData%2A> method to write data to the Clipboard.</span></span> <span data-ttu-id="c1e59-140">Cet exemple écrit `DataObject``dataChunk` dans le Presse-papiers au format personnalisé `specialFormat`.</span><span class="sxs-lookup"><span data-stu-id="c1e59-140">This example writes the `DataObject``dataChunk` to the Clipboard in the custom format `specialFormat`.</span></span>  
  
 <span data-ttu-id="c1e59-141">[!code-vb[VbVbcnMyClipboard#7](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/storing-data-to-and-reading-from-the-clipboard_7.vb)]</span><span class="sxs-lookup"><span data-stu-id="c1e59-141">[!code-vb[VbVbcnMyClipboard#7](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/storing-data-to-and-reading-from-the-clipboard_7.vb)]</span></span>  
  
 <span data-ttu-id="c1e59-142">Utilisez la méthode <xref:Microsoft.VisualBasic.MyServices.ClipboardProxy.SetAudio%2A> pour écrire des données audio dans le Presse-papiers.</span><span class="sxs-lookup"><span data-stu-id="c1e59-142">Use the <xref:Microsoft.VisualBasic.MyServices.ClipboardProxy.SetAudio%2A> method to write audio data to the Clipboard.</span></span> <span data-ttu-id="c1e59-143">Cet exemple crée le tableau d’octets `musicReader`, lit le fichier `cool.wav`, puis l’écrit dans le Presse-papiers.</span><span class="sxs-lookup"><span data-stu-id="c1e59-143">This example creates the byte array `musicReader`, reads the file `cool.wav` into it, and then writes it to the Clipboard.</span></span>  
  
 <span data-ttu-id="c1e59-144">[!code-vb[VbResourceTasks#5](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/storing-data-to-and-reading-from-the-clipboard_8.vb)]</span><span class="sxs-lookup"><span data-stu-id="c1e59-144">[!code-vb[VbResourceTasks#5](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/storing-data-to-and-reading-from-the-clipboard_8.vb)]</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="c1e59-145">Étant donné que le Presse-papiers est accessible par d’autres utilisateurs, ne l’utilisez pas pour stocker des informations sensibles, telles que des mots de passe ou des données confidentielles.</span><span class="sxs-lookup"><span data-stu-id="c1e59-145">Because the Clipboard can be accessed by other users, do not use it to store sensitive information, such as passwords or confidential data.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c1e59-146">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="c1e59-146">See also</span></span>  
 <span data-ttu-id="c1e59-147"><xref:Microsoft.VisualBasic.MyServices.ClipboardProxy></span><span class="sxs-lookup"><span data-stu-id="c1e59-147"><xref:Microsoft.VisualBasic.MyServices.ClipboardProxy></span></span>   
 <span data-ttu-id="c1e59-148"><xref:Microsoft.VisualBasic.MyServices.ClipboardProxy.GetAudioStream%2A></span><span class="sxs-lookup"><span data-stu-id="c1e59-148"><xref:Microsoft.VisualBasic.MyServices.ClipboardProxy.GetAudioStream%2A></span></span>   
 <span data-ttu-id="c1e59-149"><xref:Microsoft.VisualBasic.MyServices.ClipboardProxy.SetDataObject%2A></span><span class="sxs-lookup"><span data-stu-id="c1e59-149"><xref:Microsoft.VisualBasic.MyServices.ClipboardProxy.SetDataObject%2A></span></span>   
 <span data-ttu-id="c1e59-150">[Guide pratique pour lire des données d’objet à partir d’un fichier XML](../../../programming-guide/concepts/serialization/how-to-read-object-data-from-an-xml-file.md) </span><span class="sxs-lookup"><span data-stu-id="c1e59-150">[How to: Read Object Data from an XML File](../../../programming-guide/concepts/serialization/how-to-read-object-data-from-an-xml-file.md) </span></span>  
 [<span data-ttu-id="c1e59-151">Guide pratique : écrire des données d’objet dans un fichier XML</span><span class="sxs-lookup"><span data-stu-id="c1e59-151">How to: Write Object Data to an XML File</span></span>](../../../programming-guide/concepts/serialization/how-to-write-object-data-to-an-xml-file.md)

