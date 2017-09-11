---
title: "Guide pratique pour lire des fichiers texte délimités par des virgules en Visual Basic"
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
- files, parsing
- text files, tasks
- reading text files, comma-delimited
- text files, reading
ms.assetid: a8413fe4-0dba-49c8-8692-44fb67a9ec4f
caps.latest.revision: 19
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
ms.openlocfilehash: 2ae6a3f315a8e433386319d1aa1a7f48726a19bb
ms.contentlocale: fr-fr
ms.lasthandoff: 07/28/2017

---
# <a name="how-to-read-from-comma-delimited-text-files-in-visual-basic"></a><span data-ttu-id="c05be-102">Guide pratique pour lire des fichiers texte délimités par des virgules en Visual Basic</span><span class="sxs-lookup"><span data-stu-id="c05be-102">How to: read from comma-delimited text files in Visual Basic</span></span>
<span data-ttu-id="c05be-103">L’objet `TextFieldParser` permet d’analyser facilement et efficacement les fichiers texte structurés, tels que les journaux.</span><span class="sxs-lookup"><span data-stu-id="c05be-103">The `TextFieldParser` object provides a way to easily and efficiently parse structured text files, such as logs.</span></span> <span data-ttu-id="c05be-104">La propriété `TextFieldType` définit s’il s’agit d’un fichier délimité ou d’un fichier avec des champs de texte de longueur fixe.</span><span class="sxs-lookup"><span data-stu-id="c05be-104">The `TextFieldType` property defines whether it is a delimited file or one with fixed-width fields of text.</span></span>  
  
### <a name="to-parse-a-comma-delimited-text-file"></a><span data-ttu-id="c05be-105">Pour analyser un fichier texte délimité par des virgules</span><span class="sxs-lookup"><span data-stu-id="c05be-105">To parse a comma delimited text file</span></span>  
  
1.  <span data-ttu-id="c05be-106">Créez un `TextFieldParser`.</span><span class="sxs-lookup"><span data-stu-id="c05be-106">Create a new `TextFieldParser`.</span></span> <span data-ttu-id="c05be-107">Le code suivant crée le `TextFieldParser` nommé `MyReader` et ouvre le fichier `test.txt`.</span><span class="sxs-lookup"><span data-stu-id="c05be-107">The following code creates the `TextFieldParser` named `MyReader` and opens the file `test.txt`.</span></span>  
  
     <span data-ttu-id="c05be-108">[!code-vb[VbFileIORead#15](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-read-from-comma-delimited-text-files_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="c05be-108">[!code-vb[VbFileIORead#15](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-read-from-comma-delimited-text-files_1.vb)]</span></span>  
  
2.  <span data-ttu-id="c05be-109">Définissez le type `TextField` et le séparateur.</span><span class="sxs-lookup"><span data-stu-id="c05be-109">Define the `TextField` type and delimiter.</span></span> <span data-ttu-id="c05be-110">Le code suivant définit la propriété `TextFieldType` comme `Delimited` et le délimiteur comme ",".</span><span class="sxs-lookup"><span data-stu-id="c05be-110">The following code defines the `TextFieldType` property as `Delimited` and the delimiter as ",".</span></span>  
  
     <span data-ttu-id="c05be-111">[!code-vb[VbFileIORead#16](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-read-from-comma-delimited-text-files_2.vb)]</span><span class="sxs-lookup"><span data-stu-id="c05be-111">[!code-vb[VbFileIORead#16](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-read-from-comma-delimited-text-files_2.vb)]</span></span>  
  
3.  <span data-ttu-id="c05be-112">Parcourez les champs du fichier à l’aide d’une boucle.</span><span class="sxs-lookup"><span data-stu-id="c05be-112">Loop through the fields in the file.</span></span> <span data-ttu-id="c05be-113">Si des lignes sont endommagées, signalez une erreur et poursuivez l’analyse.</span><span class="sxs-lookup"><span data-stu-id="c05be-113">If any lines are corrupt, report an error and continue parsing.</span></span> <span data-ttu-id="c05be-114">Le code suivant parcourt le fichier à l’aide d’une boucle, affiche chaque champ l’un après l’autre et signale les champs dont le format n’est pas valide.</span><span class="sxs-lookup"><span data-stu-id="c05be-114">The following code loops through the file, displaying each field in turn and reporting any fields that are formatted incorrectly.</span></span>  
  
     <span data-ttu-id="c05be-115">[!code-vb[VbFileIORead#17](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-read-from-comma-delimited-text-files_3.vb)]</span><span class="sxs-lookup"><span data-stu-id="c05be-115">[!code-vb[VbFileIORead#17](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-read-from-comma-delimited-text-files_3.vb)]</span></span>  
  
4.  <span data-ttu-id="c05be-116">Fermez les blocs `While` et `Using` avec `End While` et `End Using`.</span><span class="sxs-lookup"><span data-stu-id="c05be-116">Close the `While` and `Using` blocks with `End While` and `End Using`.</span></span>  
  
     <span data-ttu-id="c05be-117">[!code-vb[VbFileIORead#18](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-read-from-comma-delimited-text-files_4.vb)]</span><span class="sxs-lookup"><span data-stu-id="c05be-117">[!code-vb[VbFileIORead#18](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-read-from-comma-delimited-text-files_4.vb)]</span></span>  
  
## <a name="example"></a><span data-ttu-id="c05be-118">Exemple</span><span class="sxs-lookup"><span data-stu-id="c05be-118">Example</span></span>  
 <span data-ttu-id="c05be-119">Cet exemple lit le fichier `test.txt`.</span><span class="sxs-lookup"><span data-stu-id="c05be-119">This example reads from the file `test.txt`.</span></span>  
  
 <span data-ttu-id="c05be-120">[!code-vb[VbFileIORead#19](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-read-from-comma-delimited-text-files_5.vb)]</span><span class="sxs-lookup"><span data-stu-id="c05be-120">[!code-vb[VbFileIORead#19](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-read-from-comma-delimited-text-files_5.vb)]</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="c05be-121">Programmation fiable</span><span class="sxs-lookup"><span data-stu-id="c05be-121">Robust programming</span></span>  
 <span data-ttu-id="c05be-122">Les conditions ci-dessous peuvent générer une exception.</span><span class="sxs-lookup"><span data-stu-id="c05be-122">The following conditions may cause an exception:</span></span>  
  
-   <span data-ttu-id="c05be-123">Une ligne ne peut pas être analysée à l’aide du format spécifié (<xref:Microsoft.VisualBasic.FileIO.MalformedLineException>).</span><span class="sxs-lookup"><span data-stu-id="c05be-123">A row cannot be parsed using the specified format (<xref:Microsoft.VisualBasic.FileIO.MalformedLineException>).</span></span> <span data-ttu-id="c05be-124">Le message d’exception spécifie la ligne qui provoque l’exception, tandis que la propriété <xref:Microsoft.VisualBasic.FileIO.TextFieldParser.ErrorLine%2A> est assignée au texte contenu dans la ligne.</span><span class="sxs-lookup"><span data-stu-id="c05be-124">The exception message specifies the line causing the exception, while the <xref:Microsoft.VisualBasic.FileIO.TextFieldParser.ErrorLine%2A> property is assigned the text contained in the line.</span></span>  
  
-   <span data-ttu-id="c05be-125">Le fichier spécifié n’existe pas (<xref:System.IO.FileNotFoundException>).</span><span class="sxs-lookup"><span data-stu-id="c05be-125">The specified file does not exist (<xref:System.IO.FileNotFoundException>).</span></span>  
  
-   <span data-ttu-id="c05be-126">Situation de confiance partielle dans laquelle l’utilisateur ne dispose pas des autorisations suffisantes pour accéder au fichier</span><span class="sxs-lookup"><span data-stu-id="c05be-126">A partial-trust situation in which the user does not have sufficient permissions to access the file.</span></span> <span data-ttu-id="c05be-127">(<xref:System.Security.SecurityException>).</span><span class="sxs-lookup"><span data-stu-id="c05be-127">(<xref:System.Security.SecurityException>).</span></span>  
  
-   <span data-ttu-id="c05be-128">Le chemin est trop long (<xref:System.IO.PathTooLongException>).</span><span class="sxs-lookup"><span data-stu-id="c05be-128">The path is too long (<xref:System.IO.PathTooLongException>).</span></span>  
  
-   <span data-ttu-id="c05be-129">L’utilisateur ne dispose pas des autorisations suffisantes pour accéder au fichier (<xref:System.UnauthorizedAccessException>).</span><span class="sxs-lookup"><span data-stu-id="c05be-129">The user does not have sufficient permissions to access the file (<xref:System.UnauthorizedAccessException>).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c05be-130">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="c05be-130">See also</span></span>  
 <span data-ttu-id="c05be-131"><xref:Microsoft.VisualBasic.FileIO.TextFieldParser?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="c05be-131"><xref:Microsoft.VisualBasic.FileIO.TextFieldParser?displayProperty=fullName></span></span>   
 <span data-ttu-id="c05be-132">[Guide pratique pour lire des fichiers texte de largeur fixe](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-read-from-fixed-width-text-files.md) </span><span class="sxs-lookup"><span data-stu-id="c05be-132">[How to: Read From Fixed-width Text Files](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-read-from-fixed-width-text-files.md) </span></span>  
 <span data-ttu-id="c05be-133">[Guide pratique pour lire des fichiers texte avec plusieurs formats](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-read-from-text-files-with-multiple-formats.md) </span><span class="sxs-lookup"><span data-stu-id="c05be-133">[How to: Read From Text Files with Multiple Formats](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-read-from-text-files-with-multiple-formats.md) </span></span>  
 <span data-ttu-id="c05be-134">[Analyse des fichiers texte avec l’objet TextFieldParser](../../../../visual-basic/developing-apps/programming/drives-directories-files/parsing-text-files-with-the-textfieldparser-object.md) </span><span class="sxs-lookup"><span data-stu-id="c05be-134">[Parsing Text Files with the TextFieldParser Object](../../../../visual-basic/developing-apps/programming/drives-directories-files/parsing-text-files-with-the-textfieldparser-object.md) </span></span>  
 <span data-ttu-id="c05be-135">[Procédure pas à pas : manipulation de fichiers et de répertoires en Visual Basic](../../../../visual-basic/developing-apps/programming/drives-directories-files/walkthrough-manipulating-files-and-directories.md) </span><span class="sxs-lookup"><span data-stu-id="c05be-135">[Walkthrough: Manipulating Files and Directories in Visual Basic](../../../../visual-basic/developing-apps/programming/drives-directories-files/walkthrough-manipulating-files-and-directories.md) </span></span>  
 [<span data-ttu-id="c05be-136">Dépannage : lecture et écriture dans des fichiers texte</span><span class="sxs-lookup"><span data-stu-id="c05be-136">Troubleshooting: Reading from and Writing to Text Files</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/troubleshooting-reading-from-and-writing-to-text-files.md)

