---
title: Guide pratique pour lire le texte des fichiers avec un StreamReader (Visual Basic)
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- reading files [Visual Basic], text
- text, reading from files
- reading text from files [Visual Basic]
- files [Visual Basic], reading
ms.assetid: 384033c6-18f9-4d59-9610-36371226558f
caps.latest.revision: "18"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 7b306c0e32f619a3e351cd08524767a44cee8005
ms.sourcegitcommit: 34ec7753acf76f90a0fa845235ef06663dc9e36e
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/21/2017
---
# <a name="how-to-read-text-from-files-with-a-streamreader-visual-basic"></a><span data-ttu-id="90ce5-102">Guide pratique pour lire le texte des fichiers avec un StreamReader (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="90ce5-102">How to: Read Text from Files with a StreamReader (Visual Basic)</span></span>
<span data-ttu-id="90ce5-103">L’objet `My.Computer.FileSystem` fournit des méthodes pour ouvrir un <xref:System.IO.TextReader> et <xref:System.IO.TextWriter>.</span><span class="sxs-lookup"><span data-stu-id="90ce5-103">The `My.Computer.FileSystem` object provides methods to open a <xref:System.IO.TextReader> and a <xref:System.IO.TextWriter>.</span></span> <span data-ttu-id="90ce5-104">Ces méthodes, `OpenTextFileWriter` et `OpenTextFileReader`, sont des méthodes avancées qui n’apparaissent pas dans IntelliSense, sauf si vous sélectionnez l’onglet **Tout**.</span><span class="sxs-lookup"><span data-stu-id="90ce5-104">These methods, `OpenTextFileWriter` and `OpenTextFileReader`, are advanced methods that do not appear in IntelliSense unless you select the **All** tab.</span></span>  
  
### <a name="to-read-a-line-from-a-file-with-a-text-reader"></a><span data-ttu-id="90ce5-105">Pour lire une ligne dans un fichier avec un lecteur de texte</span><span class="sxs-lookup"><span data-stu-id="90ce5-105">To read a line from a file with a text reader</span></span>  
  
-   <span data-ttu-id="90ce5-106">Utilisez la méthode `OpenTextFileReader` pour ouvrir le <xref:System.IO.TextReader>, en spécifiant le fichier.</span><span class="sxs-lookup"><span data-stu-id="90ce5-106">Use the `OpenTextFileReader` method to open the <xref:System.IO.TextReader>, specifying the file.</span></span> <span data-ttu-id="90ce5-107">Cet exemple ouvre le fichier nommé `testfile.txt`, y lit une ligne et l’affiche dans une boîte de message.</span><span class="sxs-lookup"><span data-stu-id="90ce5-107">This example opens the file named `testfile.txt`, reads a line from it, and displays the line in a message box.</span></span>  
  
     [!code-vb[VbFileIORead#1](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-read-text-from-files-with-a-streamreader_1.vb)]  
  
## <a name="robust-programming"></a><span data-ttu-id="90ce5-108">Programmation fiable</span><span class="sxs-lookup"><span data-stu-id="90ce5-108">Robust Programming</span></span>  
 <span data-ttu-id="90ce5-109">Le fichier lu doit être un fichier texte.</span><span class="sxs-lookup"><span data-stu-id="90ce5-109">The file that is read must be a text file.</span></span>  
  
 <span data-ttu-id="90ce5-110">Ne vous basez pas sur le nom d'un fichier pour en déterminer le contenu.</span><span class="sxs-lookup"><span data-stu-id="90ce5-110">Do not make decisions about the contents of the file based on the name of the file.</span></span> <span data-ttu-id="90ce5-111">Par exemple, le fichier Form1.vb peut ne pas être un fichier source Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="90ce5-111">For example, the file Form1.vb may not be a Visual Basic source file.</span></span>  
  
 <span data-ttu-id="90ce5-112">Vérifiez toutes les entrées avant d'utiliser les données dans votre application.</span><span class="sxs-lookup"><span data-stu-id="90ce5-112">Verify all inputs before using the data in your application.</span></span> <span data-ttu-id="90ce5-113">Le fichier n'a peut-être pas le contenu attendu, et les méthodes utilisées pour lire le fichier peuvent échouer.</span><span class="sxs-lookup"><span data-stu-id="90ce5-113">The contents of the file may not be what is expected, and methods to read from the file may fail.</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="90ce5-114">Sécurité .NET Framework</span><span class="sxs-lookup"><span data-stu-id="90ce5-114">.NET Framework Security</span></span>  
 <span data-ttu-id="90ce5-115">Pour lire un fichier, votre assembly nécessite un niveau de privilège accordé par la classe <xref:System.Security.Permissions.FileIOPermission>.</span><span class="sxs-lookup"><span data-stu-id="90ce5-115">To read from a file, your assembly requires a privilege level granted by the <xref:System.Security.Permissions.FileIOPermission> class.</span></span> <span data-ttu-id="90ce5-116">Si vous l’exécutez dans un contexte de confiance partielle, le code peut lever une exception en raison de privilèges insuffisants.</span><span class="sxs-lookup"><span data-stu-id="90ce5-116">If you are running in a partial-trust context, the code might throw an exception due to insufficient privileges.</span></span> <span data-ttu-id="90ce5-117">Pour plus d’informations, consultez [Notions fondamentales de la sécurité d’accès du code](../../../../framework/misc/code-access-security-basics.md).</span><span class="sxs-lookup"><span data-stu-id="90ce5-117">For more information, see [Code Access Security Basics](../../../../framework/misc/code-access-security-basics.md).</span></span> <span data-ttu-id="90ce5-118">L’utilisateur doit également avoir accès au fichier.</span><span class="sxs-lookup"><span data-stu-id="90ce5-118">The user also needs access to the file.</span></span> <span data-ttu-id="90ce5-119">Pour plus d’informations, consultez [Vue d’ensemble de la technologie ACL](http://msdn.microsoft.com/en-us/06fbf66d-6f02-4378-b863-b2f12e349045).</span><span class="sxs-lookup"><span data-stu-id="90ce5-119">For more information, see [ACL Technology Overview](http://msdn.microsoft.com/en-us/06fbf66d-6f02-4378-b863-b2f12e349045).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="90ce5-120">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="90ce5-120">See Also</span></span>  
 <xref:Microsoft.VisualBasic.FileIO.FileSystem>  
 <xref:System.Windows.Forms.OpenFileDialog>  
 <xref:Microsoft.VisualBasic.FileIO.FileSystem.OpenTextFileWriter%2A>  
 <xref:Microsoft.VisualBasic.FileIO.FileSystem.OpenTextFileReader%2A>  
 [<span data-ttu-id="90ce5-121">SaveFileDialog, composant</span><span class="sxs-lookup"><span data-stu-id="90ce5-121">SaveFileDialog Component</span></span>](../../../../framework/winforms/controls/savefiledialog-component-windows-forms.md)  
 [<span data-ttu-id="90ce5-122">Lecture à partir de fichiers</span><span class="sxs-lookup"><span data-stu-id="90ce5-122">Reading from Files</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/reading-from-files.md)
