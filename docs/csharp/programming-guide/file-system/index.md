---
title: "Système de fichiers et Registre (Guide de programmation C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords:
- file system [C#]
- registry [C#]
- files [C#]
ms.assetid: 0f2511cf-2b02-4b41-b001-b1754677c38f
caps.latest.revision: "20"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 3d1b4e3fa9b6c6da89abd242be855e9fb7c16dd6
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="file-system-and-the-registry-c-programming-guide"></a><span data-ttu-id="82ea4-102">Système de fichiers et Registre (Guide de programmation C#)</span><span class="sxs-lookup"><span data-stu-id="82ea4-102">File System and the Registry (C# Programming Guide)</span></span>
<span data-ttu-id="82ea4-103">Les rubriques suivantes montrent comment utiliser C# et .NET Framework pour effectuer différentes opérations de base sur les fichiers, les dossiers et le Registre.</span><span class="sxs-lookup"><span data-stu-id="82ea4-103">The following topics show how to use C# and the .NET Framework to perform various basic operations on files, folders, and the Registry.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="82ea4-104">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="82ea4-104">In This Section</span></span>  
  
|<span data-ttu-id="82ea4-105">**Titre**</span><span class="sxs-lookup"><span data-stu-id="82ea4-105">**Title**</span></span>|<span data-ttu-id="82ea4-106">**Description**</span><span class="sxs-lookup"><span data-stu-id="82ea4-106">**Description**</span></span>|  
|---------------|---------------------|  
|[<span data-ttu-id="82ea4-107">Comment : itérer au sein d’une arborescence de répertoires</span><span class="sxs-lookup"><span data-stu-id="82ea4-107">How to: Iterate Through a Directory Tree</span></span>](../../../csharp/programming-guide/file-system/how-to-iterate-through-a-directory-tree.md)|<span data-ttu-id="82ea4-108">Montre comment itérer manuellement au sein d’une arborescence de répertoires.</span><span class="sxs-lookup"><span data-stu-id="82ea4-108">Shows how to manually iterate through a directory tree.</span></span>|  
|[<span data-ttu-id="82ea4-109">Guide pratique : obtenir des informations sur les fichiers, dossiers et lecteurs</span><span class="sxs-lookup"><span data-stu-id="82ea4-109">How to: Get Information About Files, Folders, and Drives</span></span>](../../../csharp/programming-guide/file-system/how-to-get-information-about-files-folders-and-drives.md)|<span data-ttu-id="82ea4-110">Montre comment extraire des informations, par exemple l’heure de création et la taille, sur les fichiers, dossiers et lecteurs.</span><span class="sxs-lookup"><span data-stu-id="82ea4-110">Shows how to retrieve information such as creation times and size, about files, folders and drives.</span></span>|  
|[<span data-ttu-id="82ea4-111">Comment : créer un fichier ou un dossier</span><span class="sxs-lookup"><span data-stu-id="82ea4-111">How to: Create a File or Folder</span></span>](../../../csharp/programming-guide/file-system/how-to-create-a-file-or-folder.md)|<span data-ttu-id="82ea4-112">Montre comment créer un fichier ou un dossier.</span><span class="sxs-lookup"><span data-stu-id="82ea4-112">Shows how to create a new file or folder.</span></span>|  
|[<span data-ttu-id="82ea4-113">Guide pratique : copier, supprimer et déplacer des fichiers et dossiers (Guide de programmation C#)</span><span class="sxs-lookup"><span data-stu-id="82ea4-113">How to: Copy, Delete, and Move Files and Folders (C# Programming Guide)</span></span>](../../../csharp/programming-guide/file-system/how-to-copy-delete-and-move-files-and-folders.md)|<span data-ttu-id="82ea4-114">Montre comment copier, supprimer et déplacer des fichiers et dossiers (C#).</span><span class="sxs-lookup"><span data-stu-id="82ea4-114">Shows how to copy, delete and move files and folders.</span></span>|  
|[<span data-ttu-id="82ea4-115">Comment : fournir une boîte de dialogue de progression pour les opérations sur les fichiers</span><span class="sxs-lookup"><span data-stu-id="82ea4-115">How to: Provide a Progress Dialog Box for File Operations</span></span>](../../../csharp/programming-guide/file-system/how-to-provide-a-progress-dialog-box-for-file-operations.md)|<span data-ttu-id="82ea4-116">Montre comment afficher une boîte de dialogue de progression Windows standard pour certaines opérations de fichiers.</span><span class="sxs-lookup"><span data-stu-id="82ea4-116">Shows how to display a standard Windows progress dialog for certain file operations.</span></span>|  
|[<span data-ttu-id="82ea4-117">Comment : écrire dans un fichier texte</span><span class="sxs-lookup"><span data-stu-id="82ea4-117">How to: Write to a Text File</span></span>](../../../csharp/programming-guide/file-system/how-to-write-to-a-text-file.md)|<span data-ttu-id="82ea4-118">Montre comment écrire dans un fichier texte.</span><span class="sxs-lookup"><span data-stu-id="82ea4-118">Shows how to write to a text file.</span></span>|  
|[<span data-ttu-id="82ea4-119">Comment : lire un fichier texte</span><span class="sxs-lookup"><span data-stu-id="82ea4-119">How to: Read From a Text File</span></span>](../../../csharp/programming-guide/file-system/how-to-read-from-a-text-file.md)|<span data-ttu-id="82ea4-120">Montre comment lire un fichier texte.</span><span class="sxs-lookup"><span data-stu-id="82ea4-120">Shows how to read from a text file.</span></span>|  
|[<span data-ttu-id="82ea4-121">Guide pratique : lire un fichier texte ligne par ligne</span><span class="sxs-lookup"><span data-stu-id="82ea4-121">How to: Read a Text File One Line at a Time</span></span>](../../../csharp/programming-guide/file-system/how-to-read-a-text-file-one-line-at-a-time.md)|<span data-ttu-id="82ea4-122">Montre comment récupérer du texte dans un fichier une ligne à la fois.</span><span class="sxs-lookup"><span data-stu-id="82ea4-122">Shows how to retrieve text from a file one line at a time.</span></span>|  
|[<span data-ttu-id="82ea4-123">Guide pratique : créer une clé dans le Registre</span><span class="sxs-lookup"><span data-stu-id="82ea4-123">How to: Create a Key In the Registry</span></span>](../../../csharp/programming-guide/file-system/how-to-create-a-key-in-the-registry.md)|<span data-ttu-id="82ea4-124">Montre comment écrire une clé dans le registre du système.</span><span class="sxs-lookup"><span data-stu-id="82ea4-124">Shows how to write a key to the system registry.</span></span>|  
  
## <a name="related-sections"></a><span data-ttu-id="82ea4-125">Rubriques connexes</span><span class="sxs-lookup"><span data-stu-id="82ea4-125">Related Sections</span></span>  
 [<span data-ttu-id="82ea4-126">Fichier et flux de données E/S</span><span class="sxs-lookup"><span data-stu-id="82ea4-126">File and Stream I/O</span></span>](https://msdn.microsoft.com/library/k3352a4t)  
  
 [<span data-ttu-id="82ea4-127">Guide pratique : copier, supprimer et déplacer des fichiers et dossiers (Guide de programmation C#)</span><span class="sxs-lookup"><span data-stu-id="82ea4-127">How to: Copy, Delete, and Move Files and Folders (C# Programming Guide)</span></span>](../../../csharp/programming-guide/file-system/how-to-copy-delete-and-move-files-and-folders.md)  
  
 [<span data-ttu-id="82ea4-128">Guide de programmation C#</span><span class="sxs-lookup"><span data-stu-id="82ea4-128">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
  
 [<span data-ttu-id="82ea4-129">Fichiers, dossiers et lecteurs</span><span class="sxs-lookup"><span data-stu-id="82ea4-129">Files, Folders and Drives</span></span>](../../../csharp/programming-guide/file-system/index.md)  
  
 <xref:System.IO?displayProperty=nameWithType>
