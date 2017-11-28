---
title: "Guide pratique pour copier, supprimer et déplacer des fichiers et dossiers (Guide de programmation C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords: I/O [C#]
ms.assetid: 62e52cd7-9597-4e4a-acf9-1315f5cdbf05
caps.latest.revision: "13"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 56383873674998fc0d6417a2abf4fa72e498f08f
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-copy-delete-and-move-files-and-folders-c-programming-guide"></a><span data-ttu-id="89c8c-102">Guide pratique pour copier, supprimer et déplacer des fichiers et dossiers (Guide de programmation C#)</span><span class="sxs-lookup"><span data-stu-id="89c8c-102">How to: Copy, Delete, and Move Files and Folders (C# Programming Guide)</span></span>
<span data-ttu-id="89c8c-103">Les exemples suivants montrent comment copier, déplacer et supprimer des fichiers et dossiers de manière synchrone à l’aide des classes <xref:System.IO.File?displayProperty=nameWithType>, <xref:System.IO.Directory?displayProperty=nameWithType>, <xref:System.IO.FileInfo?displayProperty=nameWithType> et <xref:System.IO.DirectoryInfo?displayProperty=nameWithType> à partir de l’espace de noms <xref:System.IO?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="89c8c-103">The following examples show how to copy, move, and delete files and folders in a synchronous manner by using the <xref:System.IO.File?displayProperty=nameWithType>, <xref:System.IO.Directory?displayProperty=nameWithType>, <xref:System.IO.FileInfo?displayProperty=nameWithType>, and <xref:System.IO.DirectoryInfo?displayProperty=nameWithType> classes from the <xref:System.IO?displayProperty=nameWithType> namespace.</span></span> <span data-ttu-id="89c8c-104">Ces exemples ne fournissent pas de barre de progression ou autre interface utilisateur.</span><span class="sxs-lookup"><span data-stu-id="89c8c-104">These examples do not provide a progress bar or any other user interface.</span></span> <span data-ttu-id="89c8c-105">Si vous souhaitez fournir une boîte de dialogue de progression standard, consultez [Guide pratique pour fournir une boîte de dialogue de progression pour les opérations sur les fichiers](how-to-provide-a-progress-dialog-box-for-file-operations.md).</span><span class="sxs-lookup"><span data-stu-id="89c8c-105">If you want to provide a standard progress dialog box, see [How to: Provide a Progress Dialog Box for File Operations](how-to-provide-a-progress-dialog-box-for-file-operations.md).</span></span>  
  
 <span data-ttu-id="89c8c-106">Utilisez <xref:System.IO.FileSystemWatcher?displayProperty=nameWithType> pour fournir des événements qui vous permettent de calculer la progression quand vous travaillez sur plusieurs fichiers.</span><span class="sxs-lookup"><span data-stu-id="89c8c-106">Use <xref:System.IO.FileSystemWatcher?displayProperty=nameWithType> to provide events that will enable you to calculate the progress when operating on multiple files.</span></span> <span data-ttu-id="89c8c-107">Une autre approche consiste à utiliser l’appel de code non managé pour appeler les méthodes pertinentes relatives aux fichiers dans le shell Windows.</span><span class="sxs-lookup"><span data-stu-id="89c8c-107">Another approach is to use platform invoke to call the relevant file-related methods in the Windows Shell.</span></span> <span data-ttu-id="89c8c-108">Pour plus d’informations sur la façon d’effectuer ces opérations sur les fichiers de façon asynchrone, consultez [E/S de fichiers asynchrones](https://msdn.microsoft.com/library/kztecsys).</span><span class="sxs-lookup"><span data-stu-id="89c8c-108">For information about how to perform these file operations asynchronously, see [Asynchronous File I/O](https://msdn.microsoft.com/library/kztecsys).</span></span>  
  
## <a name="example"></a><span data-ttu-id="89c8c-109">Exemple</span><span class="sxs-lookup"><span data-stu-id="89c8c-109">Example</span></span>  
 <span data-ttu-id="89c8c-110">L’exemple suivant montre comment copier des fichiers et des répertoires.</span><span class="sxs-lookup"><span data-stu-id="89c8c-110">The following example shows how to copy files and directories.</span></span>  
  
 [!code-csharp[csFilesandFolders#7](../../../csharp/programming-guide/file-system/codesnippet/CSharp/how-to-copy-delete-and-move-files-and-folders_1.cs)]  
  
## <a name="example"></a><span data-ttu-id="89c8c-111">Exemple</span><span class="sxs-lookup"><span data-stu-id="89c8c-111">Example</span></span>  
 <span data-ttu-id="89c8c-112">L’exemple suivant montre comment déplacer des fichiers et des répertoires.</span><span class="sxs-lookup"><span data-stu-id="89c8c-112">The following example shows how to move files and directories.</span></span>  
  
 [!code-csharp[csFilesandFolders#8](../../../csharp/programming-guide/file-system/codesnippet/CSharp/how-to-copy-delete-and-move-files-and-folders_2.cs)]  
  
## <a name="example"></a><span data-ttu-id="89c8c-113">Exemple</span><span class="sxs-lookup"><span data-stu-id="89c8c-113">Example</span></span>  
 <span data-ttu-id="89c8c-114">L’exemple suivant montre comment supprimer des fichiers et des répertoires.</span><span class="sxs-lookup"><span data-stu-id="89c8c-114">The following example shows how to delete files and directories.</span></span>  
  
 [!code-csharp[csFilesandFolders#9](../../../csharp/programming-guide/file-system/codesnippet/CSharp/how-to-copy-delete-and-move-files-and-folders_3.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="89c8c-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="89c8c-115">See Also</span></span>  
 <xref:System.IO?displayProperty=nameWithType>  
 [<span data-ttu-id="89c8c-116">Guide de programmation C#</span><span class="sxs-lookup"><span data-stu-id="89c8c-116">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="89c8c-117">Système de fichiers et Registre (Guide de programmation C#)</span><span class="sxs-lookup"><span data-stu-id="89c8c-117">File System and the Registry (C# Programming Guide)</span></span>](index.md)  
 [<span data-ttu-id="89c8c-118">Comment : fournir une boîte de dialogue de progression pour les opérations sur les fichiers</span><span class="sxs-lookup"><span data-stu-id="89c8c-118">How to: Provide a Progress Dialog Box for File Operations</span></span>](how-to-provide-a-progress-dialog-box-for-file-operations.md)  
 [<span data-ttu-id="89c8c-119">Fichier et flux de données E/S</span><span class="sxs-lookup"><span data-stu-id="89c8c-119">File and Stream I/O</span></span>](https://msdn.microsoft.com/library/k3352a4t)  
 [<span data-ttu-id="89c8c-120">Tâches d’E/S courantes</span><span class="sxs-lookup"><span data-stu-id="89c8c-120">Common I/O Tasks</span></span>](https://msdn.microsoft.com/library/ms404278)
