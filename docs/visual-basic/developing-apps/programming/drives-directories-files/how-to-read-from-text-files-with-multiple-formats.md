---
title: Guide pratique pour lire des fichiers texte avec plusieurs formats en Visual Basic
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- TextFieldParser object, reading from a file
- TextFieldType enumeration
- My.Computer.FileSystem.WriteAllText method, parsing structured text files
- WriteAllText method [Visual Basic], parsing structured text files
- PeekChars method [Visual Basic], determining format of text
- reading text files [Visual Basic], multiple formats
- I/O [Visual Basic], reading text files
- text files [Visual Basic], reading
ms.assetid: 8d185eb2-79ca-42cd-95a7-d3ff44a5a0f8
caps.latest.revision: "17"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 12362f932561bf16412e5beb364f785778c58814
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-read-from-text-files-with-multiple-formats-in-visual-basic"></a><span data-ttu-id="3c046-102">Guide pratique pour lire des fichiers texte avec plusieurs formats en Visual Basic</span><span class="sxs-lookup"><span data-stu-id="3c046-102">How to: Read From Text Files with Multiple Formats in Visual Basic</span></span>
<span data-ttu-id="3c046-103">L’objet <xref:Microsoft.VisualBasic.FileIO.TextFieldParser> permet d’analyser facilement et efficacement les fichiers texte structurés, tels que les journaux.</span><span class="sxs-lookup"><span data-stu-id="3c046-103">The <xref:Microsoft.VisualBasic.FileIO.TextFieldParser> object provides a way to easily and efficiently parse structured text files, such as logs.</span></span> <span data-ttu-id="3c046-104">Vous pouvez traiter un fichier contenant plusieurs formats en utilisant la méthode `PeekChars` pour déterminer le format de chaque ligne à mesure que vous analysez le fichier.</span><span class="sxs-lookup"><span data-stu-id="3c046-104">You can process a file with multiple formats by using the `PeekChars` method to determine the format of each line as you parse through the file.</span></span>  
  
### <a name="to-parse-a-text-file-with-multiple-formats"></a><span data-ttu-id="3c046-105">Pour analyser un fichier texte avec plusieurs formats</span><span class="sxs-lookup"><span data-stu-id="3c046-105">To parse a text file with multiple formats</span></span>  
  
1.  <span data-ttu-id="3c046-106">Ajoutez un fichier texte nommé testfile.txt à votre projet.</span><span class="sxs-lookup"><span data-stu-id="3c046-106">Add a text file named testfile.txt to your project.</span></span> <span data-ttu-id="3c046-107">Ajoutez le contenu suivant au fichier texte.</span><span class="sxs-lookup"><span data-stu-id="3c046-107">Add the following content to the text file.</span></span>  
  
    ```  
    Err  1001 Cannot access resource.  
    Err  2014 Resource not found.  
    Acc  10/03/2009User1      Administrator.  
    Err  0323 Warning: Invalid access attempt.  
    Acc  10/03/2009User2      Standard user.  
    Acc  10/04/2009User2      Standard user.  
    ```  
  
2.  <span data-ttu-id="3c046-108">Définissez le format attendu et le format utilisé quand une erreur est signalée.</span><span class="sxs-lookup"><span data-stu-id="3c046-108">Define the expected format and the format used when an error is reported.</span></span> <span data-ttu-id="3c046-109">La dernière entrée dans chaque tableau étant -1, le dernier champ est supposé avoir une largeur variable.</span><span class="sxs-lookup"><span data-stu-id="3c046-109">The last entry in each array is -1, therefore the last field is assumed to be of variable width.</span></span> <span data-ttu-id="3c046-110">Cela se produit quand la dernière entrée du tableau est inférieure ou égale à 0.</span><span class="sxs-lookup"><span data-stu-id="3c046-110">This occurs when the last entry in the array is less than or equal to 0.</span></span>  
  
     [!code-vb[VbFileIORead#4](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-read-from-text-files-with-multiple-formats_1.vb)]  
  
3.  <span data-ttu-id="3c046-111">Créez un nouvel objet <xref:Microsoft.VisualBasic.FileIO.TextFieldParser> en définissant la largeur et le format.</span><span class="sxs-lookup"><span data-stu-id="3c046-111">Create a new <xref:Microsoft.VisualBasic.FileIO.TextFieldParser> object, defining the width and format.</span></span>  
  
     [!code-vb[VbFileIORead#5](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-read-from-text-files-with-multiple-formats_2.vb)]  
  
4.  <span data-ttu-id="3c046-112">Parcourez les lignes en boucle, en testant le format avant la lecture.</span><span class="sxs-lookup"><span data-stu-id="3c046-112">Loop through the rows, testing for format before reading.</span></span>  
  
     [!code-vb[VbFileIORead#6](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-read-from-text-files-with-multiple-formats_3.vb)]  
  
5.  <span data-ttu-id="3c046-113">Écrivez les erreurs dans la console.</span><span class="sxs-lookup"><span data-stu-id="3c046-113">Write errors to the console.</span></span>  
  
     [!code-vb[VbFileIORead#7](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-read-from-text-files-with-multiple-formats_4.vb)]  
  
## <a name="example"></a><span data-ttu-id="3c046-114">Exemple</span><span class="sxs-lookup"><span data-stu-id="3c046-114">Example</span></span>  
 <span data-ttu-id="3c046-115">Voici l’exemple complet qui lit le fichier `testfile.txt`.</span><span class="sxs-lookup"><span data-stu-id="3c046-115">Following is the complete example that reads from the file `testfile.txt`.</span></span>  
  
 [!code-vb[VbFileIORead#8](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-read-from-text-files-with-multiple-formats_5.vb)]  
  
## <a name="robust-programming"></a><span data-ttu-id="3c046-116">Programmation fiable</span><span class="sxs-lookup"><span data-stu-id="3c046-116">Robust Programming</span></span>  
 <span data-ttu-id="3c046-117">Les conditions ci-dessous peuvent générer une exception.</span><span class="sxs-lookup"><span data-stu-id="3c046-117">The following conditions may cause an exception:</span></span>  
  
-   <span data-ttu-id="3c046-118">Une ligne ne peut pas être analysée à l’aide du format spécifié (<xref:Microsoft.VisualBasic.FileIO.MalformedLineException>).</span><span class="sxs-lookup"><span data-stu-id="3c046-118">A row cannot be parsed using the specified format (<xref:Microsoft.VisualBasic.FileIO.MalformedLineException>).</span></span> <span data-ttu-id="3c046-119">Le message d’exception spécifie la ligne qui provoque l’exception, tandis que la propriété <xref:Microsoft.VisualBasic.FileIO.TextFieldParser.ErrorLine%2A> est assignée au texte contenu dans la ligne.</span><span class="sxs-lookup"><span data-stu-id="3c046-119">The exception message specifies the line causing the exception, while the <xref:Microsoft.VisualBasic.FileIO.TextFieldParser.ErrorLine%2A> property is assigned to the text contained in the line.</span></span>  
  
-   <span data-ttu-id="3c046-120">Le fichier spécifié n’existe pas (<xref:System.IO.FileNotFoundException>).</span><span class="sxs-lookup"><span data-stu-id="3c046-120">The specified file does not exist (<xref:System.IO.FileNotFoundException>).</span></span>  
  
-   <span data-ttu-id="3c046-121">Situation de confiance partielle dans laquelle l’utilisateur ne dispose pas des autorisations suffisantes pour accéder au fichier</span><span class="sxs-lookup"><span data-stu-id="3c046-121">A partial-trust situation in which the user does not have sufficient permissions to access the file.</span></span> <span data-ttu-id="3c046-122">(<xref:System.Security.SecurityException>).</span><span class="sxs-lookup"><span data-stu-id="3c046-122">(<xref:System.Security.SecurityException>).</span></span>  
  
-   <span data-ttu-id="3c046-123">Le chemin est trop long (<xref:System.IO.PathTooLongException>).</span><span class="sxs-lookup"><span data-stu-id="3c046-123">The path is too long (<xref:System.IO.PathTooLongException>).</span></span>  
  
-   <span data-ttu-id="3c046-124">L’utilisateur ne dispose pas des autorisations suffisantes pour accéder au fichier (<xref:System.UnauthorizedAccessException>).</span><span class="sxs-lookup"><span data-stu-id="3c046-124">The user does not have sufficient permissions to access the file (<xref:System.UnauthorizedAccessException>).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3c046-125">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="3c046-125">See Also</span></span>  
 <xref:Microsoft.VisualBasic.FileIO.TextFieldParser?displayProperty=nameWithType>  
 <xref:Microsoft.VisualBasic.FileIO.TextFieldParser.PeekChars%2A>  
 <xref:Microsoft.VisualBasic.FileIO.MalformedLineException>  
 <xref:Microsoft.VisualBasic.FileIO.FileSystem.WriteAllText%2A>  
 <xref:Microsoft.VisualBasic.FileIO.TextFieldParser.EndOfData%2A>  
 <xref:Microsoft.VisualBasic.FileIO.TextFieldParser.TextFieldType%2A>  
 [<span data-ttu-id="3c046-126">Guide pratique : lire des fichiers texte délimités par des virgules</span><span class="sxs-lookup"><span data-stu-id="3c046-126">How to: Read From Comma-Delimited Text Files</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-read-from-comma-delimited-text-files.md)  
 [<span data-ttu-id="3c046-127">Guide pratique : lire des fichiers texte de largeur fixe</span><span class="sxs-lookup"><span data-stu-id="3c046-127">How to: Read From Fixed-width Text Files</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-read-from-fixed-width-text-files.md)  
 [<span data-ttu-id="3c046-128">Analyse des fichiers texte avec l’objet TextFieldParser</span><span class="sxs-lookup"><span data-stu-id="3c046-128">Parsing Text Files with the TextFieldParser Object</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/parsing-text-files-with-the-textfieldparser-object.md)
