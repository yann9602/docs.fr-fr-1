---
title: "Guide pratique pour écrire du texte dans des fichiers à l'aide de Streamwriter dans Visual Basic"
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
- writing to files, StreamWriter
ms.assetid: 99762e57-ef46-4dcc-8959-a8f79c22f067
caps.latest.revision: 14
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
ms.openlocfilehash: ea85d57e9af4fdd640733db5dc2fa8b0ab25325c
ms.contentlocale: fr-fr
ms.lasthandoff: 07/28/2017

---
# <a name="how-to-write-text-to-files-with-a-streamwriter-in-visual-basic"></a><span data-ttu-id="2c3ca-102">Guide pratique pour écrire du texte dans des fichiers à l'aide de Streamwriter dans Visual Basic</span><span class="sxs-lookup"><span data-stu-id="2c3ca-102">How to: Write Text to Files with a StreamWriter in Visual Basic</span></span>
<span data-ttu-id="2c3ca-103">Cet exemple ouvre un objet <xref:System.IO.StreamWriter> avec la méthode `My.Computer.FileSystem.OpenTextFileWriter` et l’utilise pour écrire une chaîne dans un fichier texte avec la méthode <xref:System.IO.TextWriter.WriteLine%2A> de la classe <xref:System.IO.StreamWriter>.</span><span class="sxs-lookup"><span data-stu-id="2c3ca-103">This example opens a <xref:System.IO.StreamWriter> object with the `My.Computer.FileSystem.OpenTextFileWriter` method and uses it to write a string to a text file with the <xref:System.IO.TextWriter.WriteLine%2A> method of the <xref:System.IO.StreamWriter> class.</span></span>  
  
## <a name="example"></a><span data-ttu-id="2c3ca-104">Exemple</span><span class="sxs-lookup"><span data-stu-id="2c3ca-104">Example</span></span>  
 <span data-ttu-id="2c3ca-105">[!code-vb[VbFileIOWrite#5](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-write-text-to-files-with-a-streamwriter_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="2c3ca-105">[!code-vb[VbFileIOWrite#5](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-write-text-to-files-with-a-streamwriter_1.vb)]</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="2c3ca-106">Programmation fiable</span><span class="sxs-lookup"><span data-stu-id="2c3ca-106">Robust Programming</span></span>  
 <span data-ttu-id="2c3ca-107">Les conditions ci-dessous peuvent générer une exception.</span><span class="sxs-lookup"><span data-stu-id="2c3ca-107">The following conditions may cause an exception:</span></span>  
  
-   <span data-ttu-id="2c3ca-108">Le fichier existe et est en lecture seule (<xref:System.IO.IOException>).</span><span class="sxs-lookup"><span data-stu-id="2c3ca-108">The file exists and is read-only (<xref:System.IO.IOException>).</span></span>  
  
-   <span data-ttu-id="2c3ca-109">Le disque est plein (<xref:System.IO.IOException>).</span><span class="sxs-lookup"><span data-stu-id="2c3ca-109">The disk is full (<xref:System.IO.IOException>).</span></span>  
  
-   <span data-ttu-id="2c3ca-110">Le nom du chemin est trop long (<xref:System.IO.PathTooLongException>).</span><span class="sxs-lookup"><span data-stu-id="2c3ca-110">The pathname is too long (<xref:System.IO.PathTooLongException>).</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="2c3ca-111">Sécurité .NET Framework</span><span class="sxs-lookup"><span data-stu-id="2c3ca-111">.NET Framework Security</span></span>  
 <span data-ttu-id="2c3ca-112">Cet exemple crée un fichier s’il n’existe pas déjà.</span><span class="sxs-lookup"><span data-stu-id="2c3ca-112">This example creates a new file, if the file does not already exist.</span></span> <span data-ttu-id="2c3ca-113">Si une application doit créer un fichier, elle doit disposer de l’autorisation `Create` pour accéder au dossier.</span><span class="sxs-lookup"><span data-stu-id="2c3ca-113">If an application needs to create a file, that application needs `Create` access for the folder.</span></span> <span data-ttu-id="2c3ca-114">Si le fichier existe déjà, l’application a uniquement besoin de l’autorisation `Write`, qui est une autorisation de niveau inférieur.</span><span class="sxs-lookup"><span data-stu-id="2c3ca-114">If the file already exists, the application needs only `Write` access, a lesser privilege.</span></span> <span data-ttu-id="2c3ca-115">Quand cela est possible, il est plus sûr de créer le fichier au cours du déploiement et de n’accorder l’autorisation `Read` que sur un seul fichier, plutôt que l’autorisation `Create` sur un dossier.</span><span class="sxs-lookup"><span data-stu-id="2c3ca-115">Where possible, it is more secure to create the file during deployment, and only grant `Read` access to a single file, rather than `Create` access for a folder.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2c3ca-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="2c3ca-116">See Also</span></span>  
 <span data-ttu-id="2c3ca-117"><xref:System.IO.StreamWriter></span><span class="sxs-lookup"><span data-stu-id="2c3ca-117"><xref:System.IO.StreamWriter></span></span>   
 <span data-ttu-id="2c3ca-118"><xref:Microsoft.VisualBasic.FileIO.FileSystem.OpenTextFileWriter%2A></span><span class="sxs-lookup"><span data-stu-id="2c3ca-118"><xref:Microsoft.VisualBasic.FileIO.FileSystem.OpenTextFileWriter%2A></span></span>   
 <span data-ttu-id="2c3ca-119">[Guide pratique pour lire des fichiers texte](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-read-from-text-files.md) </span><span class="sxs-lookup"><span data-stu-id="2c3ca-119">[How to: Read from Text Files](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-read-from-text-files.md) </span></span>  
 [<span data-ttu-id="2c3ca-120">Écriture dans des fichiers</span><span class="sxs-lookup"><span data-stu-id="2c3ca-120">Writing to Files</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/writing-to-files.md)

