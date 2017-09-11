---
title: "Guide pratique pour copier, supprimer et déplacer des fichiers et dossiers (Guide de programmation C#)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
helpviewer_keywords:
- I/O [C#]
ms.assetid: 62e52cd7-9597-4e4a-acf9-1315f5cdbf05
caps.latest.revision: 13
author: BillWagner
ms.author: wiwagn
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
ms.openlocfilehash: a4cfec46e0af0056a0de20a1ed83a370cd010055
ms.contentlocale: fr-fr
ms.lasthandoff: 07/28/2017

---
# <a name="how-to-copy-delete-and-move-files-and-folders-c-programming-guide"></a><span data-ttu-id="4e9f0-102">Guide pratique pour copier, supprimer et déplacer des fichiers et dossiers (Guide de programmation C#)</span><span class="sxs-lookup"><span data-stu-id="4e9f0-102">How to: Copy, Delete, and Move Files and Folders (C# Programming Guide)</span></span>
<span data-ttu-id="4e9f0-103">Les exemples suivants montrent comment copier, déplacer et supprimer des fichiers et dossiers de manière synchrone à l’aide des classes <xref:System.IO.File?displayProperty=fullName>, <xref:System.IO.Directory?displayProperty=fullName>, <xref:System.IO.FileInfo?displayProperty=fullName> et <xref:System.IO.DirectoryInfo?displayProperty=fullName> à partir de l’espace de noms <xref:System.IO?displayProperty=fullName>.</span><span class="sxs-lookup"><span data-stu-id="4e9f0-103">The following examples show how to copy, move, and delete files and folders in a synchronous manner by using the <xref:System.IO.File?displayProperty=fullName>, <xref:System.IO.Directory?displayProperty=fullName>, <xref:System.IO.FileInfo?displayProperty=fullName>, and <xref:System.IO.DirectoryInfo?displayProperty=fullName> classes from the <xref:System.IO?displayProperty=fullName> namespace.</span></span> <span data-ttu-id="4e9f0-104">Ces exemples ne fournissent pas de barre de progression ou autre interface utilisateur.</span><span class="sxs-lookup"><span data-stu-id="4e9f0-104">These examples do not provide a progress bar or any other user interface.</span></span> <span data-ttu-id="4e9f0-105">Si vous souhaitez fournir une boîte de dialogue de progression standard, consultez [Guide pratique pour fournir une boîte de dialogue de progression pour les opérations sur les fichiers](how-to-provide-a-progress-dialog-box-for-file-operations.md).</span><span class="sxs-lookup"><span data-stu-id="4e9f0-105">If you want to provide a standard progress dialog box, see [How to: Provide a Progress Dialog Box for File Operations](how-to-provide-a-progress-dialog-box-for-file-operations.md).</span></span>  
  
 <span data-ttu-id="4e9f0-106">Utilisez <xref:System.IO.FileSystemWatcher?displayProperty=fullName> pour fournir des événements qui vous permettent de calculer la progression quand vous travaillez sur plusieurs fichiers.</span><span class="sxs-lookup"><span data-stu-id="4e9f0-106">Use <xref:System.IO.FileSystemWatcher?displayProperty=fullName> to provide events that will enable you to calculate the progress when operating on multiple files.</span></span> <span data-ttu-id="4e9f0-107">Une autre approche consiste à utiliser l’appel de code non managé pour appeler les méthodes pertinentes relatives aux fichiers dans le shell Windows.</span><span class="sxs-lookup"><span data-stu-id="4e9f0-107">Another approach is to use platform invoke to call the relevant file-related methods in the Windows Shell.</span></span> <span data-ttu-id="4e9f0-108">Pour plus d’informations sur la façon d’effectuer ces opérations sur les fichiers de façon asynchrone, consultez [E/S de fichiers asynchrones](https://msdn.microsoft.com/library/kztecsys).</span><span class="sxs-lookup"><span data-stu-id="4e9f0-108">For information about how to perform these file operations asynchronously, see [Asynchronous File I/O](https://msdn.microsoft.com/library/kztecsys).</span></span>  
  
## <a name="example"></a><span data-ttu-id="4e9f0-109">Exemple</span><span class="sxs-lookup"><span data-stu-id="4e9f0-109">Example</span></span>  
 <span data-ttu-id="4e9f0-110">L’exemple suivant montre comment copier des fichiers et des répertoires.</span><span class="sxs-lookup"><span data-stu-id="4e9f0-110">The following example shows how to copy files and directories.</span></span>  
  
 <span data-ttu-id="4e9f0-111">[!code-cs[csFilesandFolders#7](../../../csharp/programming-guide/file-system/codesnippet/CSharp/how-to-copy-delete-and-move-files-and-folders_1.cs)]</span><span class="sxs-lookup"><span data-stu-id="4e9f0-111">[!code-cs[csFilesandFolders#7](../../../csharp/programming-guide/file-system/codesnippet/CSharp/how-to-copy-delete-and-move-files-and-folders_1.cs)]</span></span>  
  
## <a name="example"></a><span data-ttu-id="4e9f0-112">Exemple</span><span class="sxs-lookup"><span data-stu-id="4e9f0-112">Example</span></span>  
 <span data-ttu-id="4e9f0-113">L’exemple suivant montre comment déplacer des fichiers et des répertoires.</span><span class="sxs-lookup"><span data-stu-id="4e9f0-113">The following example shows how to move files and directories.</span></span>  
  
 <span data-ttu-id="4e9f0-114">[!code-cs[csFilesandFolders#8](../../../csharp/programming-guide/file-system/codesnippet/CSharp/how-to-copy-delete-and-move-files-and-folders_2.cs)]</span><span class="sxs-lookup"><span data-stu-id="4e9f0-114">[!code-cs[csFilesandFolders#8](../../../csharp/programming-guide/file-system/codesnippet/CSharp/how-to-copy-delete-and-move-files-and-folders_2.cs)]</span></span>  
  
## <a name="example"></a><span data-ttu-id="4e9f0-115">Exemple</span><span class="sxs-lookup"><span data-stu-id="4e9f0-115">Example</span></span>  
 <span data-ttu-id="4e9f0-116">L’exemple suivant montre comment supprimer des fichiers et des répertoires.</span><span class="sxs-lookup"><span data-stu-id="4e9f0-116">The following example shows how to delete files and directories.</span></span>  
  
 <span data-ttu-id="4e9f0-117">[!code-cs[csFilesandFolders#9](../../../csharp/programming-guide/file-system/codesnippet/CSharp/how-to-copy-delete-and-move-files-and-folders_3.cs)]</span><span class="sxs-lookup"><span data-stu-id="4e9f0-117">[!code-cs[csFilesandFolders#9](../../../csharp/programming-guide/file-system/codesnippet/CSharp/how-to-copy-delete-and-move-files-and-folders_3.cs)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4e9f0-118">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="4e9f0-118">See Also</span></span>  
 <span data-ttu-id="4e9f0-119"><xref:System.IO?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="4e9f0-119"><xref:System.IO?displayProperty=fullName></span></span>   
 <span data-ttu-id="4e9f0-120">[Guide de programmation C#](../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="4e9f0-120">[C# Programming Guide](../../../csharp/programming-guide/index.md) </span></span>  
 <span data-ttu-id="4e9f0-121">[Système de fichiers et Registre (Guide de programmation C#)](index.md) </span><span class="sxs-lookup"><span data-stu-id="4e9f0-121">[File System and the Registry (C# Programming Guide)](index.md) </span></span>  
 <span data-ttu-id="4e9f0-122">[Guide pratique pour fournir une boîte de dialogue de progression pour les opérations sur les fichiers](how-to-provide-a-progress-dialog-box-for-file-operations.md) </span><span class="sxs-lookup"><span data-stu-id="4e9f0-122">[How to: Provide a Progress Dialog Box for File Operations](how-to-provide-a-progress-dialog-box-for-file-operations.md) </span></span>  
 <span data-ttu-id="4e9f0-123">[E/S de fichier et de flux](https://msdn.microsoft.com/library/k3352a4t) </span><span class="sxs-lookup"><span data-stu-id="4e9f0-123">[File and Stream I/O](https://msdn.microsoft.com/library/k3352a4t) </span></span>  
 [<span data-ttu-id="4e9f0-124">Tâches d’E/S courantes</span><span class="sxs-lookup"><span data-stu-id="4e9f0-124">Common I/O Tasks</span></span>](https://msdn.microsoft.com/library/ms404278)

