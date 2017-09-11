---
title: Guide pratique pour lire des fichiers texte de largeur fixe en Visual Basic
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
- fixed-width text file
- reading text files, fixed-width
- files, parsing
- text files, tasks
- text files, reading
ms.assetid: 99be5692-967a-4e85-993e-cd18139a5a69
caps.latest.revision: 24
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
ms.openlocfilehash: fc45c6d6e4301b2786fefe947ed011ca95f8a79c
ms.contentlocale: fr-fr
ms.lasthandoff: 07/28/2017

---
# <a name="how-to-read-from-fixed-width-text-files-in-visual-basic"></a><span data-ttu-id="70b70-102">Guide pratique pour lire des fichiers texte de largeur fixe en Visual Basic</span><span class="sxs-lookup"><span data-stu-id="70b70-102">How to: read from fixed-width text files in Visual Basic</span></span>
<span data-ttu-id="70b70-103">L’objet `TextFieldParser` permet d’analyser facilement et efficacement les fichiers texte structurés, tels que les journaux.</span><span class="sxs-lookup"><span data-stu-id="70b70-103">The `TextFieldParser` object provides a way to easily and efficiently parse structured text files, such as logs.</span></span>  
  
 <span data-ttu-id="70b70-104">La propriété `TextFieldType` définit si le fichier analysé est un fichier délimité ou un fichier qui comporte des champs de texte de longueur fixe.</span><span class="sxs-lookup"><span data-stu-id="70b70-104">The `TextFieldType` property defines whether the parsed file is a delimited file or one that has fixed-width fields of text.</span></span> <span data-ttu-id="70b70-105">Dans un fichier texte de largeur fixe, le champ situé à la fin peut avoir une largeur variable.</span><span class="sxs-lookup"><span data-stu-id="70b70-105">In a fixed-width text file, the field at the end can have a variable width.</span></span> <span data-ttu-id="70b70-106">Pour spécifier que le champ situé à la fin a une largeur variable, définissez-le pour que sa largeur soit inférieure ou égale à zéro.</span><span class="sxs-lookup"><span data-stu-id="70b70-106">To specify that the field at the end has a variable width, define it to have a width less than or equal to zero.</span></span>  
  
### <a name="to-parse-a-fixed-width-text-file"></a><span data-ttu-id="70b70-107">Pour analyser un fichier texte de largeur fixe</span><span class="sxs-lookup"><span data-stu-id="70b70-107">To parse a fixed-width text file</span></span>  
  
1.  <span data-ttu-id="70b70-108">Créez un `TextFieldParser`.</span><span class="sxs-lookup"><span data-stu-id="70b70-108">Create a new `TextFieldParser`.</span></span> <span data-ttu-id="70b70-109">Le code suivant crée le `TextFieldParser` nommé `Reader` et ouvre le fichier `test.log`.</span><span class="sxs-lookup"><span data-stu-id="70b70-109">The following code creates the `TextFieldParser` named `Reader` and opens the file `test.log`.</span></span>  
  
     <span data-ttu-id="70b70-110">[!code-vb[VbFileIORead#9](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-read-from-fixed-width-text-files_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="70b70-110">[!code-vb[VbFileIORead#9](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-read-from-fixed-width-text-files_1.vb)]</span></span>  
  
2.  <span data-ttu-id="70b70-111">Définissez la propriété `TextFieldType` en tant que `FixedWidth`, en définissant la largeur et le format.</span><span class="sxs-lookup"><span data-stu-id="70b70-111">Define the `TextFieldType` property as `FixedWidth`, defining the width and format.</span></span> <span data-ttu-id="70b70-112">Le code suivant définit les colonnes de texte. La première a une largeur de 5 caractères, la deuxième de 10 caractères, la troisième de 11 caractères et la quatrième a une largeur variable.</span><span class="sxs-lookup"><span data-stu-id="70b70-112">The following code defines the columns of text; the first is 5 characters wide, the second 10, the third 11, and the fourth is of variable width.</span></span>  
  
     <span data-ttu-id="70b70-113">[!code-vb[VbFileIORead#10](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-read-from-fixed-width-text-files_2.vb)]</span><span class="sxs-lookup"><span data-stu-id="70b70-113">[!code-vb[VbFileIORead#10](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-read-from-fixed-width-text-files_2.vb)]</span></span>  
  
3.  <span data-ttu-id="70b70-114">Parcourez les champs du fichier à l’aide d’une boucle.</span><span class="sxs-lookup"><span data-stu-id="70b70-114">Loop through the fields in the file.</span></span> <span data-ttu-id="70b70-115">Si des lignes sont endommagées, signalez une erreur et poursuivez l’analyse.</span><span class="sxs-lookup"><span data-stu-id="70b70-115">If any lines are corrupted, report an error and continue parsing.</span></span>  
  
     <span data-ttu-id="70b70-116">[!code-vb[VbFileIORead#11](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-read-from-fixed-width-text-files_3.vb)]</span><span class="sxs-lookup"><span data-stu-id="70b70-116">[!code-vb[VbFileIORead#11](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-read-from-fixed-width-text-files_3.vb)]</span></span>  
  
4.  <span data-ttu-id="70b70-117">Fermez les blocs `While` et `Using` avec `End While` et `End Using`.</span><span class="sxs-lookup"><span data-stu-id="70b70-117">Close the `While` and `Using` blocks with `End While` and `End Using`.</span></span>  
  
     <span data-ttu-id="70b70-118">[!code-vb[VbFileIORead#12](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-read-from-fixed-width-text-files_4.vb)]</span><span class="sxs-lookup"><span data-stu-id="70b70-118">[!code-vb[VbFileIORead#12](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-read-from-fixed-width-text-files_4.vb)]</span></span>  
  
## <a name="example"></a><span data-ttu-id="70b70-119">Exemple</span><span class="sxs-lookup"><span data-stu-id="70b70-119">Example</span></span>  
 <span data-ttu-id="70b70-120">Cet exemple lit le fichier `test.log`.</span><span class="sxs-lookup"><span data-stu-id="70b70-120">This example reads from the file `test.log`.</span></span>  
  
 <span data-ttu-id="70b70-121">[!code-vb[VbFileIORead#13](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-read-from-fixed-width-text-files_5.vb)]</span><span class="sxs-lookup"><span data-stu-id="70b70-121">[!code-vb[VbFileIORead#13](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-read-from-fixed-width-text-files_5.vb)]</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="70b70-122">Programmation fiable</span><span class="sxs-lookup"><span data-stu-id="70b70-122">Robust programming</span></span>  
 <span data-ttu-id="70b70-123">Les conditions ci-dessous peuvent générer une exception.</span><span class="sxs-lookup"><span data-stu-id="70b70-123">The following conditions may cause an exception:</span></span>  
  
-   <span data-ttu-id="70b70-124">Une ligne ne peut pas être analysée à l’aide du format spécifié (<xref:Microsoft.VisualBasic.FileIO.MalformedLineException>).</span><span class="sxs-lookup"><span data-stu-id="70b70-124">A row cannot be parsed using the specified format (<xref:Microsoft.VisualBasic.FileIO.MalformedLineException>).</span></span> <span data-ttu-id="70b70-125">Le message d’exception spécifie la ligne qui provoque l’exception, tandis que la propriété <xref:Microsoft.VisualBasic.FileIO.TextFieldParser.ErrorLine%2A> est assignée au texte contenu dans la ligne.</span><span class="sxs-lookup"><span data-stu-id="70b70-125">The exception message specifies the line causing the exception, while the <xref:Microsoft.VisualBasic.FileIO.TextFieldParser.ErrorLine%2A> property is assigned to the text contained in the line.</span></span>  
  
-   <span data-ttu-id="70b70-126">Le fichier spécifié n’existe pas (<xref:System.IO.FileNotFoundException>).</span><span class="sxs-lookup"><span data-stu-id="70b70-126">The specified file does not exist (<xref:System.IO.FileNotFoundException>).</span></span>  
  
-   <span data-ttu-id="70b70-127">Situation de confiance partielle dans laquelle l’utilisateur ne dispose pas des autorisations suffisantes pour accéder au fichier</span><span class="sxs-lookup"><span data-stu-id="70b70-127">A partial-trust situation in which the user does not have sufficient permissions to access the file.</span></span> <span data-ttu-id="70b70-128">(<xref:System.Security.SecurityException>).</span><span class="sxs-lookup"><span data-stu-id="70b70-128">(<xref:System.Security.SecurityException>).</span></span>  
  
-   <span data-ttu-id="70b70-129">Le chemin est trop long (<xref:System.IO.PathTooLongException>).</span><span class="sxs-lookup"><span data-stu-id="70b70-129">The path is too long (<xref:System.IO.PathTooLongException>).</span></span>  
  
-   <span data-ttu-id="70b70-130">L’utilisateur ne dispose pas des autorisations suffisantes pour accéder au fichier (<xref:System.UnauthorizedAccessException>).</span><span class="sxs-lookup"><span data-stu-id="70b70-130">The user does not have sufficient permissions to access the file (<xref:System.UnauthorizedAccessException>).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="70b70-131">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="70b70-131">See also</span></span>  
 <span data-ttu-id="70b70-132"><xref:Microsoft.VisualBasic.FileIO.TextFieldParser?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="70b70-132"><xref:Microsoft.VisualBasic.FileIO.TextFieldParser?displayProperty=fullName></span></span>   
 <span data-ttu-id="70b70-133">[Guide pratique pour lire des fichiers texte délimités par des virgules](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-read-from-comma-delimited-text-files.md) </span><span class="sxs-lookup"><span data-stu-id="70b70-133">[How to: Read From Comma-Delimited Text Files](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-read-from-comma-delimited-text-files.md) </span></span>  
 <span data-ttu-id="70b70-134">[Guide pratique pour lire des fichiers texte avec plusieurs formats](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-read-from-text-files-with-multiple-formats.md) </span><span class="sxs-lookup"><span data-stu-id="70b70-134">[How to: Read From Text Files with Multiple Formats](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-read-from-text-files-with-multiple-formats.md) </span></span>  
 <span data-ttu-id="70b70-135">[Analyse des fichiers texte avec l’objet TextFieldParser](../../../../visual-basic/developing-apps/programming/drives-directories-files/parsing-text-files-with-the-textfieldparser-object.md) </span><span class="sxs-lookup"><span data-stu-id="70b70-135">[Parsing Text Files with the TextFieldParser Object](../../../../visual-basic/developing-apps/programming/drives-directories-files/parsing-text-files-with-the-textfieldparser-object.md) </span></span>  
 <span data-ttu-id="70b70-136">[Procédure pas à pas : manipulation de fichiers et de répertoires en Visual Basic](../../../../visual-basic/developing-apps/programming/drives-directories-files/walkthrough-manipulating-files-and-directories.md) </span><span class="sxs-lookup"><span data-stu-id="70b70-136">[Walkthrough: Manipulating Files and Directories in Visual Basic](../../../../visual-basic/developing-apps/programming/drives-directories-files/walkthrough-manipulating-files-and-directories.md) </span></span>  
 [<span data-ttu-id="70b70-137">Dépannage : lecture et écriture dans des fichiers texte</span><span class="sxs-lookup"><span data-stu-id="70b70-137">Troubleshooting: Reading from and Writing to Text Files</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/troubleshooting-reading-from-and-writing-to-text-files.md)   
 

