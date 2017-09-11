---
title: Guide pratique pour lire des fichiers texte dans Visual Basic
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
- extended characters, reading
- reading text files
- reading data, text files
- examples [Visual Basic], reading text files
- text files, reading
ms.assetid: 735fe9d7-0f7a-4185-ba02-f35e580ec4b8
caps.latest.revision: 27
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
ms.openlocfilehash: 9b38b7f869a1d4ff290042a18a9bc2e0fa2709b7
ms.contentlocale: fr-fr
ms.lasthandoff: 07/28/2017

---
# <a name="how-to-read-from-text-files-in-visual-basic"></a><span data-ttu-id="696e0-102">Guide pratique pour lire des fichiers texte dans Visual Basic</span><span class="sxs-lookup"><span data-stu-id="696e0-102">How to: Read From Text Files in Visual Basic</span></span>
<span data-ttu-id="696e0-103">La méthode <xref:Microsoft.VisualBasic.MyServices.FileSystemProxy.ReadAllText%2A> de l'objet `My.Computer.FileSystem` vous permet de lire un fichier texte.</span><span class="sxs-lookup"><span data-stu-id="696e0-103">The <xref:Microsoft.VisualBasic.MyServices.FileSystemProxy.ReadAllText%2A> method of the `My.Computer.FileSystem` object allows you to read from a text file.</span></span> <span data-ttu-id="696e0-104">L'encodage du fichier peut être spécifié si le contenu de ce dernier utilise l'encodage ASCII ou UTF-8.</span><span class="sxs-lookup"><span data-stu-id="696e0-104">The file encoding can be specified if the contents of the file use an encoding such as ASCII or UTF-8.</span></span>  
  
 <span data-ttu-id="696e0-105">Si vous lisez un fichier avec des caractères étendus, vous devez spécifier son encodage.</span><span class="sxs-lookup"><span data-stu-id="696e0-105">If you are reading from a file with extended characters, you will need to specify the file encoding.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="696e0-106">Pour lire un fichier, une ligne de texte à la fois, utilisez la méthode <xref:Microsoft.VisualBasic.MyServices.FileSystemProxy.OpenTextFileReader%2A> de l'objet `My.Computer.FileSystem`.</span><span class="sxs-lookup"><span data-stu-id="696e0-106">To read a file a single line of text at a time, use the <xref:Microsoft.VisualBasic.MyServices.FileSystemProxy.OpenTextFileReader%2A> method of the `My.Computer.FileSystem` object.</span></span> <span data-ttu-id="696e0-107">La méthode `OpenTextFileReader` retourne un objet <xref:System.IO.StreamReader>.</span><span class="sxs-lookup"><span data-stu-id="696e0-107">The `OpenTextFileReader` method returns a <xref:System.IO.StreamReader> object.</span></span> <span data-ttu-id="696e0-108">Vous pouvez utiliser la méthode <xref:System.IO.StreamReader.ReadLine%2A> de l"objet `StreamReader` pour lire un fichier une ligne à la fois.</span><span class="sxs-lookup"><span data-stu-id="696e0-108">You can use the <xref:System.IO.StreamReader.ReadLine%2A> method of the `StreamReader` object to read a file one line at a time.</span></span> <span data-ttu-id="696e0-109">Vous pouvez tester la fin du fichier à l'aide de la méthode <xref:System.IO.StreamReader.EndOfStream%2A> de l'objet `StreamReader`.</span><span class="sxs-lookup"><span data-stu-id="696e0-109">You can test for the end of the file using the <xref:System.IO.StreamReader.EndOfStream%2A> method of the `StreamReader` object.</span></span>  
  
### <a name="to-read-from-a-text-file"></a><span data-ttu-id="696e0-110">Pour lire un fichier texte</span><span class="sxs-lookup"><span data-stu-id="696e0-110">To read from a text file</span></span>  
  
-   <span data-ttu-id="696e0-111">Utilisez la méthode `ReadAllText` de l'objet `My.Computer.FileSystem` pour lire le contenu d'un fichier texte dans une chaîne en fournissant le chemin d'accès.</span><span class="sxs-lookup"><span data-stu-id="696e0-111">Use the `ReadAllText` method of the `My.Computer.FileSystem` object to read the contents of a text file into a string, supplying the path.</span></span> <span data-ttu-id="696e0-112">L'exemple suivant lit le contenu du fichier test.txt dans une chaîne puis l'affiche dans un message.</span><span class="sxs-lookup"><span data-stu-id="696e0-112">The following example reads the contents of test.txt into a string and then displays it in a message box.</span></span>  
  
     <span data-ttu-id="696e0-113">[!code-vb[VbFileIORead#2](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-read-from-text-files_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="696e0-113">[!code-vb[VbFileIORead#2](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-read-from-text-files_1.vb)]</span></span>  
  
### <a name="to-read-from-a-text-file-that-is-encoded"></a><span data-ttu-id="696e0-114">Pour lire un fichier texte encodé</span><span class="sxs-lookup"><span data-stu-id="696e0-114">To read from a text file that is encoded</span></span>  
  
-   <span data-ttu-id="696e0-115">Utilisez la méthode `ReadAllText` de l'objet `My.Computer.FileSystem` pour lire le contenu d'un fichier texte dans une chaîne en fournissant le chemin d'accès et le type d'encodage du fichier.</span><span class="sxs-lookup"><span data-stu-id="696e0-115">Use the `ReadAllText` method of the `My.Computer.FileSystem` object to read the contents of a text file into a string, supplying the path and file encoding type.</span></span> <span data-ttu-id="696e0-116">L'exemple suivant lit le contenu du fichier UTF32 test.txt dans une chaîne puis l'affiche dans un message.</span><span class="sxs-lookup"><span data-stu-id="696e0-116">The following example reads the contents of the UTF32 file test.txt into a string and then displays it in a message box.</span></span>  
  
     <span data-ttu-id="696e0-117">[!code-vb[VbFileIORead#3](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-read-from-text-files_2.vb)]</span><span class="sxs-lookup"><span data-stu-id="696e0-117">[!code-vb[VbFileIORead#3](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-read-from-text-files_2.vb)]</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="696e0-118">Programmation fiable</span><span class="sxs-lookup"><span data-stu-id="696e0-118">Robust Programming</span></span>  
 <span data-ttu-id="696e0-119">Les conditions ci-dessous peuvent générer une exception.</span><span class="sxs-lookup"><span data-stu-id="696e0-119">The following conditions may cause an exception:</span></span>  
  
-   <span data-ttu-id="696e0-120">Le chemin d'accès n'est pas valide pour une des raisons suivantes : il s'agit d'une chaîne de longueur nulle ; il ne contient que des espaces blancs ; il contient des caractères non valides ou il s'agit d'un chemin d'accès de périphérique (<xref:System.ArgumentException>).</span><span class="sxs-lookup"><span data-stu-id="696e0-120">The path is not valid for one of the following reasons: it is a zero-length string, it contains only white space, it contains invalid characters, or it is a device path (<xref:System.ArgumentException>).</span></span>  
  
-   <span data-ttu-id="696e0-121">Le chemin d'accès n'est pas valide, car il a la valeur `Nothing` (<xref:System.ArgumentNullException>).</span><span class="sxs-lookup"><span data-stu-id="696e0-121">The path is not valid because it is `Nothing` (<xref:System.ArgumentNullException>).</span></span>  
  
-   <span data-ttu-id="696e0-122">Le fichier n'existe pas (<xref:System.IO.FileNotFoundException>).</span><span class="sxs-lookup"><span data-stu-id="696e0-122">The file does not exist (<xref:System.IO.FileNotFoundException>).</span></span>  
  
-   <span data-ttu-id="696e0-123">Le fichier est utilisé par un autre processus, ou une erreur E/S se produit (<xref:System.IO.IOException>).</span><span class="sxs-lookup"><span data-stu-id="696e0-123">The file is in use by another process or an I/O error occurs (<xref:System.IO.IOException>).</span></span>  
  
-   <span data-ttu-id="696e0-124">Le chemin d'accès dépasse la longueur maximale définie par le système (<xref:System.IO.PathTooLongException>).</span><span class="sxs-lookup"><span data-stu-id="696e0-124">The path exceeds the system-defined maximum length (<xref:System.IO.PathTooLongException>).</span></span>  
  
-   <span data-ttu-id="696e0-125">Un nom de fichier ou de répertoire du chemin d'accès contient un signe deux-points (:) ou n'a pas un format correct (<xref:System.NotSupportedException>).</span><span class="sxs-lookup"><span data-stu-id="696e0-125">A file or directory name in the path contains a colon (:) or is in an invalid format (<xref:System.NotSupportedException>).</span></span>  
  
-   <span data-ttu-id="696e0-126">Il n'y a pas assez de mémoire pour écrire la chaîne dans la mémoire tampon (<xref:System.OutOfMemoryException>).</span><span class="sxs-lookup"><span data-stu-id="696e0-126">There is not enough memory to write the string to buffer (<xref:System.OutOfMemoryException>).</span></span>  
  
-   <span data-ttu-id="696e0-127">L'utilisateur n'a pas les autorisations nécessaires pour afficher le chemin d'accès (<xref:System.Security.SecurityException>).</span><span class="sxs-lookup"><span data-stu-id="696e0-127">The user lacks necessary permissions to view the path (<xref:System.Security.SecurityException>).</span></span>  
  
 <span data-ttu-id="696e0-128">Ne vous basez pas sur le nom d'un fichier pour en déterminer le contenu.</span><span class="sxs-lookup"><span data-stu-id="696e0-128">Do not make decisions about the contents of the file based on the name of the file.</span></span> <span data-ttu-id="696e0-129">Par exemple, il se peut que le fichier nommé Form1.vb ne soit pas un fichier source [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)].</span><span class="sxs-lookup"><span data-stu-id="696e0-129">For example, the file Form1.vb may not be a [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] source file.</span></span>  
  
 <span data-ttu-id="696e0-130">Vérifiez toutes les entrées avant d'utiliser les données dans votre application.</span><span class="sxs-lookup"><span data-stu-id="696e0-130">Verify all inputs before using the data in your application.</span></span> <span data-ttu-id="696e0-131">Le fichier n'a peut-être pas le contenu attendu, et les méthodes utilisées pour lire le fichier peuvent échouer.</span><span class="sxs-lookup"><span data-stu-id="696e0-131">The contents of the file may not be what is expected, and methods to read from the file may fail.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="696e0-132">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="696e0-132">See Also</span></span>  
 <span data-ttu-id="696e0-133"><xref:Microsoft.VisualBasic.FileIO.FileSystem></span><span class="sxs-lookup"><span data-stu-id="696e0-133"><xref:Microsoft.VisualBasic.FileIO.FileSystem></span></span>   
 <span data-ttu-id="696e0-134"><xref:Microsoft.VisualBasic.FileIO.FileSystem.ReadAllText%2A></span><span class="sxs-lookup"><span data-stu-id="696e0-134"><xref:Microsoft.VisualBasic.FileIO.FileSystem.ReadAllText%2A></span></span>   
 <span data-ttu-id="696e0-135">[Lecture à partir de fichiers](../../../../visual-basic/developing-apps/programming/drives-directories-files/reading-from-files.md) </span><span class="sxs-lookup"><span data-stu-id="696e0-135">[Reading from Files](../../../../visual-basic/developing-apps/programming/drives-directories-files/reading-from-files.md) </span></span>  
 <span data-ttu-id="696e0-136">[Guide pratique pour lire des fichiers texte délimités par des virgules](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-read-from-comma-delimited-text-files.md) </span><span class="sxs-lookup"><span data-stu-id="696e0-136">[How to: Read From Comma-Delimited Text Files](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-read-from-comma-delimited-text-files.md) </span></span>  
 <span data-ttu-id="696e0-137">[Guide pratique pour lire des fichiers texte de largeur fixe](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-read-from-fixed-width-text-files.md) </span><span class="sxs-lookup"><span data-stu-id="696e0-137">[How to: Read From Fixed-width Text Files](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-read-from-fixed-width-text-files.md) </span></span>  
 <span data-ttu-id="696e0-138">[Guide pratique pour lire des fichiers texte avec plusieurs formats](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-read-from-text-files-with-multiple-formats.md) </span><span class="sxs-lookup"><span data-stu-id="696e0-138">[How to: Read From Text Files with Multiple Formats](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-read-from-text-files-with-multiple-formats.md) </span></span>  
 <span data-ttu-id="696e0-139">[Dépannage : lecture et écriture dans des fichiers texte](../../../../visual-basic/developing-apps/programming/drives-directories-files/troubleshooting-reading-from-and-writing-to-text-files.md) </span><span class="sxs-lookup"><span data-stu-id="696e0-139">[Troubleshooting: Reading from and Writing to Text Files](../../../../visual-basic/developing-apps/programming/drives-directories-files/troubleshooting-reading-from-and-writing-to-text-files.md) </span></span>  
 <span data-ttu-id="696e0-140">[Procédure pas à pas : manipulation de fichiers et de répertoires en Visual Basic](../../../../visual-basic/developing-apps/programming/drives-directories-files/walkthrough-manipulating-files-and-directories.md) </span><span class="sxs-lookup"><span data-stu-id="696e0-140">[Walkthrough: Manipulating Files and Directories in Visual Basic](../../../../visual-basic/developing-apps/programming/drives-directories-files/walkthrough-manipulating-files-and-directories.md) </span></span>  
 [<span data-ttu-id="696e0-141">Codages de fichiers</span><span class="sxs-lookup"><span data-stu-id="696e0-141">File Encodings</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/file-encodings.md)

