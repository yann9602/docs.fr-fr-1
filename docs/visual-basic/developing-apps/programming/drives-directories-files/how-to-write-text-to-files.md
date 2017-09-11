---
title: "Guide pratique pour écrire du texte dans des fichiers en Visual Basic"
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
- files, writing to
- text, writing to files
- writing to files
- examples [Visual Basic], text files
ms.assetid: 304956eb-530d-4df7-b48f-9b4d1f2581a0
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
ms.openlocfilehash: dc6f02d6092a30113b8cb973be225e140eca19ad
ms.contentlocale: fr-fr
ms.lasthandoff: 07/28/2017

---
# <a name="how-to-write-text-to-files-in-visual-basic"></a><span data-ttu-id="5c1b8-102">Guide pratique pour écrire du texte dans des fichiers en Visual Basic</span><span class="sxs-lookup"><span data-stu-id="5c1b8-102">How to: Write Text to Files in Visual Basic</span></span>
<span data-ttu-id="5c1b8-103">Vous pouvez utiliser la méthode <xref:Microsoft.VisualBasic.FileIO.FileSystem.WriteAllText%2A> pour écrire du texte dans des fichiers.</span><span class="sxs-lookup"><span data-stu-id="5c1b8-103">The <xref:Microsoft.VisualBasic.FileIO.FileSystem.WriteAllText%2A> method can be used to write text to files.</span></span> <span data-ttu-id="5c1b8-104">Si le fichier spécifié n’existe pas, il est créé.</span><span class="sxs-lookup"><span data-stu-id="5c1b8-104">If the specified file does not exist, it is created.</span></span>  
  
## <a name="procedure"></a><span data-ttu-id="5c1b8-105">Procédure</span><span class="sxs-lookup"><span data-stu-id="5c1b8-105">Procedure</span></span>  
  
#### <a name="to-write-text-to-a-file"></a><span data-ttu-id="5c1b8-106">Pour écrire du texte dans un fichier</span><span class="sxs-lookup"><span data-stu-id="5c1b8-106">To write text to a file</span></span>  
  
-   <span data-ttu-id="5c1b8-107">Utilisez la méthode `WriteAllText` pour écrire du texte dans un fichier, en spécifiant le fichier et le texte à écrire.</span><span class="sxs-lookup"><span data-stu-id="5c1b8-107">Use the `WriteAllText` method to write text to a file, specifying the file and text to be written.</span></span> <span data-ttu-id="5c1b8-108">Cet exemple écrit la ligne `"This is new text."` dans le fichier nommé `test.txt`. Le texte est ajouté au texte existant dans le fichier.</span><span class="sxs-lookup"><span data-stu-id="5c1b8-108">This example writes the line `"This is new text."` to the file named `test.txt`, appending the text to any existing text in the file.</span></span>  
  
     <span data-ttu-id="5c1b8-109">[!code-vb[VbFileIOWrite#3](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-write-text-to-files_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="5c1b8-109">[!code-vb[VbFileIOWrite#3](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-write-text-to-files_1.vb)]</span></span>  
  
#### <a name="to-write-a-series-of-strings-to-a-file"></a><span data-ttu-id="5c1b8-110">Pour écrire une série de chaînes dans un fichier</span><span class="sxs-lookup"><span data-stu-id="5c1b8-110">To write a series of strings to a file</span></span>  
  
-   <span data-ttu-id="5c1b8-111">Parcourez la collection de chaînes.</span><span class="sxs-lookup"><span data-stu-id="5c1b8-111">Loop through the string collection.</span></span> <span data-ttu-id="5c1b8-112">Utilisez la méthode `WriteAllText` pour écrire du texte dans un fichier, en spécifiant le fichier cible et la chaîne à ajouter, puis en affectant la valeur `True` au paramètre `append`.</span><span class="sxs-lookup"><span data-stu-id="5c1b8-112">Use the `WriteAllText` method to write text to a file, specifying the target file and string to be added and setting `append` to `True`.</span></span>  
  
     <span data-ttu-id="5c1b8-113">Cet exemple écrit les noms des fichiers dans le répertoire `Documents and Settings` dans `FileList.txt`, et insère un retour chariot entre chacun d’eux pour une meilleure lisibilité.</span><span class="sxs-lookup"><span data-stu-id="5c1b8-113">This example writes the names of the files in the `Documents and Settings` directory to `FileList.txt`, inserting a carriage return between each for better readability.</span></span>  
  
     <span data-ttu-id="5c1b8-114">[!code-vb[VbFileIOWrite#4](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-write-text-to-files_2.vb)]</span><span class="sxs-lookup"><span data-stu-id="5c1b8-114">[!code-vb[VbFileIOWrite#4](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-write-text-to-files_2.vb)]</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="5c1b8-115">Programmation fiable</span><span class="sxs-lookup"><span data-stu-id="5c1b8-115">Robust Programming</span></span>  
 <span data-ttu-id="5c1b8-116">Les conditions ci-dessous peuvent générer une exception.</span><span class="sxs-lookup"><span data-stu-id="5c1b8-116">The following conditions may cause an exception:</span></span>  
  
-   <span data-ttu-id="5c1b8-117">Le chemin n’est pas valide pour l’une des raisons suivantes : il s’agit d’une chaîne de longueur nulle, il ne contient que des espaces blancs, il contient des caractères non valides ou il s’agit d’un chemin d’appareil (il commence par \\\\.\\) (<xref:System.ArgumentException>).</span><span class="sxs-lookup"><span data-stu-id="5c1b8-117">The path is not valid for one of the following reasons: it is a zero-length string, it contains only white space, it contains invalid characters, or it is a device path (starts with \\\\.\\) (<xref:System.ArgumentException>).</span></span>  
  
-   <span data-ttu-id="5c1b8-118">Le chemin n’est pas valide, car il a la valeur `Nothing` (<xref:System.ArgumentNullException>).</span><span class="sxs-lookup"><span data-stu-id="5c1b8-118">The path is not valid because it is `Nothing` (<xref:System.ArgumentNullException>).</span></span>  
  
-   <span data-ttu-id="5c1b8-119">`File` pointe vers un chemin qui n’existe pas (<xref:System.IO.FileNotFoundException> ou <xref:System.IO.DirectoryNotFoundException>).</span><span class="sxs-lookup"><span data-stu-id="5c1b8-119">`File` points to a path that does not exist (<xref:System.IO.FileNotFoundException> or <xref:System.IO.DirectoryNotFoundException>).</span></span>  
  
-   <span data-ttu-id="5c1b8-120">Le fichier est utilisé par un autre processus, ou une erreur E/S se produit (<xref:System.IO.IOException>).</span><span class="sxs-lookup"><span data-stu-id="5c1b8-120">The file is in use by another process, or an I/O error occurs (<xref:System.IO.IOException>).</span></span>  
  
-   <span data-ttu-id="5c1b8-121">Le chemin d'accès dépasse la longueur maximale définie par le système (<xref:System.IO.PathTooLongException>).</span><span class="sxs-lookup"><span data-stu-id="5c1b8-121">The path exceeds the system-defined maximum length (<xref:System.IO.PathTooLongException>).</span></span>  
  
-   <span data-ttu-id="5c1b8-122">Un nom de fichier ou de répertoire du chemin contient un signe deux-points (:) ou n'a pas un format correct (<xref:System.NotSupportedException>).</span><span class="sxs-lookup"><span data-stu-id="5c1b8-122">A file or directory name in the path contains a colon (:) or is in an invalid format (<xref:System.NotSupportedException>).</span></span>  
  
-   <span data-ttu-id="5c1b8-123">L'utilisateur n'a pas les autorisations nécessaires pour afficher le chemin d'accès (<xref:System.Security.SecurityException>).</span><span class="sxs-lookup"><span data-stu-id="5c1b8-123">The user lacks necessary permissions to view the path (<xref:System.Security.SecurityException>).</span></span>  
  
-   <span data-ttu-id="5c1b8-124">Le disque est plein et l’appel à `WriteAllText` échoue (<xref:System.IO.IOException>).</span><span class="sxs-lookup"><span data-stu-id="5c1b8-124">The disk is full, and the call to `WriteAllText` fails (<xref:System.IO.IOException>).</span></span>  
  
 <span data-ttu-id="5c1b8-125">Si vous l’exécutez dans un contexte de confiance partielle, le code peut lever une exception en raison de privilèges insuffisants.</span><span class="sxs-lookup"><span data-stu-id="5c1b8-125">If you are running in a partial-trust context, the code might throw an exception due to insufficient privileges.</span></span> <span data-ttu-id="5c1b8-126">Pour plus d’informations, consultez [Notions fondamentales de la sécurité d’accès du code](https://msdn.microsoft.com/library/33tceax8).</span><span class="sxs-lookup"><span data-stu-id="5c1b8-126">For more information, see [Code Access Security Basics](https://msdn.microsoft.com/library/33tceax8).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5c1b8-127">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="5c1b8-127">See Also</span></span>  
 <span data-ttu-id="5c1b8-128"><xref:Microsoft.VisualBasic.FileIO.FileSystem></span><span class="sxs-lookup"><span data-stu-id="5c1b8-128"><xref:Microsoft.VisualBasic.FileIO.FileSystem></span></span>   
 <span data-ttu-id="5c1b8-129"><xref:Microsoft.VisualBasic.FileIO.FileSystem.WriteAllText%2A></span><span class="sxs-lookup"><span data-stu-id="5c1b8-129"><xref:Microsoft.VisualBasic.FileIO.FileSystem.WriteAllText%2A></span></span>   
 [<span data-ttu-id="5c1b8-130">Guide pratique : lire à partir de fichiers texte</span><span class="sxs-lookup"><span data-stu-id="5c1b8-130">How to: Read from Text Files</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-read-from-text-files.md)

