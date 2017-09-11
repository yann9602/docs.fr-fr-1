---
title: "Comment : insérer du texte dans les fichiers du répertoire Mes Documents dans Visual Basic"
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
- examples [Visual Basic], text files
- writing to files, in My Documents
ms.assetid: 1c726124-781d-4976-9baa-ed46814ff3fe
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
ms.openlocfilehash: c900072d184469ead75bb76a3e152edce357a34f
ms.contentlocale: fr-fr
ms.lasthandoff: 07/28/2017

---
# <a name="how-to-write-text-to-files-in-the-my-documents-directory-in-visual-basic"></a><span data-ttu-id="a1d28-102">Comment : insérer du texte dans les fichiers du répertoire Mes Documents dans Visual Basic</span><span class="sxs-lookup"><span data-stu-id="a1d28-102">How to: Write Text to Files in the My Documents Directory in Visual Basic</span></span>
<span data-ttu-id="a1d28-103">L’objet `My.Computer.FileSystem.SpecialDirectories` vous permet d’accéder à des répertoires spéciaux, comme le répertoire **Mes documents**.</span><span class="sxs-lookup"><span data-stu-id="a1d28-103">The `My.Computer.FileSystem.SpecialDirectories` object allows you to access special directories, such as the **MyDocuments** directory.</span></span>  
  
## <a name="procedure"></a><span data-ttu-id="a1d28-104">Procédure</span><span class="sxs-lookup"><span data-stu-id="a1d28-104">Procedure</span></span>  
  
#### <a name="to-write-new-text-files-in-the-my-documents-directory"></a><span data-ttu-id="a1d28-105">Pour écrire de nouveaux fichiers texte dans le répertoire Mes Documents</span><span class="sxs-lookup"><span data-stu-id="a1d28-105">To write new text files in the My Documents directory</span></span>  
  
1.  <span data-ttu-id="a1d28-106">Utilisez la propriété `My.Computer.FileSystem.SpecialDirectories.MyDocuments` pour fournir le chemin.</span><span class="sxs-lookup"><span data-stu-id="a1d28-106">Use the `My.Computer.FileSystem.SpecialDirectories.MyDocuments` property to supply the path.</span></span>  
  
     <span data-ttu-id="a1d28-107">[!code-vb[VbFileIOWrite#1](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-write-text-to-files-in-the-my-documents-directory_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="a1d28-107">[!code-vb[VbFileIOWrite#1](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-write-text-to-files-in-the-my-documents-directory_1.vb)]</span></span>  
  
2.  <span data-ttu-id="a1d28-108">Utilisez la méthode `WriteAllText` pour écrire du texte dans le fichier spécifié.</span><span class="sxs-lookup"><span data-stu-id="a1d28-108">Use the `WriteAllText` method to write text to the specified file.</span></span>  
  
     <span data-ttu-id="a1d28-109">[!code-vb[VbVbcnMyFileSystem#14](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-write-text-to-files-in-the-my-documents-directory_2.vb)]</span><span class="sxs-lookup"><span data-stu-id="a1d28-109">[!code-vb[VbVbcnMyFileSystem#14](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-write-text-to-files-in-the-my-documents-directory_2.vb)]</span></span>  
  
## <a name="example"></a><span data-ttu-id="a1d28-110">Exemple</span><span class="sxs-lookup"><span data-stu-id="a1d28-110">Example</span></span>  
 <span data-ttu-id="a1d28-111">[!code-vb[VbFileIOWrite#2](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-write-text-to-files-in-the-my-documents-directory_3.vb)]</span><span class="sxs-lookup"><span data-stu-id="a1d28-111">[!code-vb[VbFileIOWrite#2](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-write-text-to-files-in-the-my-documents-directory_3.vb)]</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="a1d28-112">Compilation du code</span><span class="sxs-lookup"><span data-stu-id="a1d28-112">Compiling the Code</span></span>  
 <span data-ttu-id="a1d28-113">Remplacez `test.txt` par le nom du fichier dans lequel vous voulez écrire.</span><span class="sxs-lookup"><span data-stu-id="a1d28-113">Replace `test.txt` with the name of the file you want to write to.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="a1d28-114">Programmation fiable</span><span class="sxs-lookup"><span data-stu-id="a1d28-114">Robust Programming</span></span>  
 <span data-ttu-id="a1d28-115">Ce code lève de nouveau toutes les exceptions qui peuvent se produire lors de l’écriture de texte dans le fichier.</span><span class="sxs-lookup"><span data-stu-id="a1d28-115">This code rethrows all the exceptions that may occur when writing text to the file.</span></span> <span data-ttu-id="a1d28-116">Vous pouvez réduire la probabilité d’exceptions en utilisant des contrôles Windows Forms comme les composants [OpenFileDialog](../../../../framework/winforms/controls/openfiledialog-component-windows-forms.md) et [SaveFileDialog](../../../../framework/winforms/controls/savefiledialog-component-windows-forms.md) qui limitent les choix de l’utilisateur à des noms de fichier valides.</span><span class="sxs-lookup"><span data-stu-id="a1d28-116">You can reduce the likelihood of exceptions by using Windows Forms controls such as the [OpenFileDialog](../../../../framework/winforms/controls/openfiledialog-component-windows-forms.md) and the [SaveFileDialog](../../../../framework/winforms/controls/savefiledialog-component-windows-forms.md) components that limit the user choices to valid file names.</span></span> <span data-ttu-id="a1d28-117">Toutefois, l’utilisation de ces contrôles n’est pas infaillible.</span><span class="sxs-lookup"><span data-stu-id="a1d28-117">Using these controls is not foolproof, however.</span></span> <span data-ttu-id="a1d28-118">Le système de fichiers peut changer entre le moment où l’utilisateur sélectionne un fichier et celui où le code s’exécute.</span><span class="sxs-lookup"><span data-stu-id="a1d28-118">The file system can change between the time the user selects a file and the time that the code executes.</span></span> <span data-ttu-id="a1d28-119">La gestion des exceptions est donc presque toujours nécessaire quand vous utilisez des fichiers.</span><span class="sxs-lookup"><span data-stu-id="a1d28-119">Exception handling is therefore nearly always necessary when with working with files.</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="a1d28-120">Sécurité .NET Framework</span><span class="sxs-lookup"><span data-stu-id="a1d28-120">.NET Framework Security</span></span>  
 <span data-ttu-id="a1d28-121">Si vous l’exécutez dans un contexte de confiance partielle, le code peut lever une exception en raison de privilèges insuffisants.</span><span class="sxs-lookup"><span data-stu-id="a1d28-121">If you are running in a partial-trust context, the code might throw an exception due to insufficient privileges.</span></span> <span data-ttu-id="a1d28-122">Pour plus d’informations, consultez [Notions fondamentales de la sécurité d’accès du code](https://msdn.microsoft.com/library/33tceax8).</span><span class="sxs-lookup"><span data-stu-id="a1d28-122">For more information, see [Code Access Security Basics](https://msdn.microsoft.com/library/33tceax8).</span></span>  
  
 <span data-ttu-id="a1d28-123">Cet exemple crée un fichier.</span><span class="sxs-lookup"><span data-stu-id="a1d28-123">This example creates a new file.</span></span> <span data-ttu-id="a1d28-124">Si une application doit créer un fichier, elle doit disposer de l’autorisation de création sur le dossier.</span><span class="sxs-lookup"><span data-stu-id="a1d28-124">If an application needs to create a file, that application needs Create permission for the folder.</span></span> <span data-ttu-id="a1d28-125">Les autorisations sont définies à l’aide des listes de contrôle d’accès.</span><span class="sxs-lookup"><span data-stu-id="a1d28-125">Permissions are set using access control lists.</span></span> <span data-ttu-id="a1d28-126">Si le fichier existe déjà, l’application a uniquement besoin de l’autorisation d’écriture, ce qui représente une autorisation inférieure.</span><span class="sxs-lookup"><span data-stu-id="a1d28-126">If the file already exists, the application needs only Write permission, a lesser privilege.</span></span> <span data-ttu-id="a1d28-127">Quand cela est possible, il est plus sûr de créer le fichier pendant le déploiement et de n’accorder les privilèges de lecture que sur un seul fichier, plutôt que d’accorder des privilèges de création sur un dossier.</span><span class="sxs-lookup"><span data-stu-id="a1d28-127">Where possible, it is more secure to create the file during deployment, and only grant Read privileges to a single file, rather than to grant Create privileges for a folder.</span></span> <span data-ttu-id="a1d28-128">Par ailleurs, il est plus sûr d’écrire les données dans des dossiers utilisateur que dans le dossier racine ou le dossier **Program Files**.</span><span class="sxs-lookup"><span data-stu-id="a1d28-128">Also, it is more secure to write data to user folders than to the root folder or the **Program Files** folder.</span></span> <span data-ttu-id="a1d28-129">Pour plus d’informations, consultez [Vue d’ensemble de la technologie ACL](http://msdn.microsoft.com/en-us/06fbf66d-6f02-4378-b863-b2f12e349045).</span><span class="sxs-lookup"><span data-stu-id="a1d28-129">For more information, see [ACL Technology Overview](http://msdn.microsoft.com/en-us/06fbf66d-6f02-4378-b863-b2f12e349045).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a1d28-130">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="a1d28-130">See Also</span></span>  
 <xref:System.IO.Path.Combine%2A?displayProperty=fullName>   
 <xref:Microsoft.VisualBasic.Devices.Computer>   
 <xref:Microsoft.VisualBasic.FileIO.FileSystem>   
 <xref:Microsoft.VisualBasic.FileIO.FileSystem.WriteAllText%2A>   
 <xref:Microsoft.VisualBasic.FileIO.SpecialDirectories>

