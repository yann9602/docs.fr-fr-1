---
title: "Accès au fichier avec Visual Basic"
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
- file access
- files, input and output
- file access, Visual Basic
- files, I/O
- file I/O classes
- data [Visual Basic], accessing from files
- files, accessing
- file access, using components
- My.Computer.FileSystem object, accessing files
- I/O [Visual Basic]
- sequential access
ms.assetid: 231533bf-d049-4345-befa-3fb78fe6517d
caps.latest.revision: 17
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
ms.openlocfilehash: 71e941bf33c3b1051c22c8170b327df9fae7d4b9
ms.contentlocale: fr-fr
ms.lasthandoff: 07/28/2017

---
# <a name="file-access-with-visual-basic"></a><span data-ttu-id="4a5de-102">Accès au fichier avec Visual Basic</span><span class="sxs-lookup"><span data-stu-id="4a5de-102">File Access with Visual Basic</span></span>
<span data-ttu-id="4a5de-103">L’objet `My.Computer.FileSystem` fournit des outils pour l’utilisation des fichiers et des dossiers.</span><span class="sxs-lookup"><span data-stu-id="4a5de-103">The `My.Computer.FileSystem` object provides tools for working with files and folders.</span></span> <span data-ttu-id="4a5de-104">Ses propriétés, méthodes et événements permettent de créer, copier, déplacer, examiner et supprimer des fichiers et des dossiers.</span><span class="sxs-lookup"><span data-stu-id="4a5de-104">Its properties, methods, and events allow you to create, copy, move, investigate, and delete files and folders.</span></span> <span data-ttu-id="4a5de-105">`My.Computer.FileSystem` offre de meilleures performances que les fonctions héritées (`FileOpen`, `FileClose`, `Input`, `InputString`, `LineInput`, etc.) qui sont fournies par [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] pour une compatibilité descendante.</span><span class="sxs-lookup"><span data-stu-id="4a5de-105">`My.Computer.FileSystem` provides better performance than the legacy functions (`FileOpen`, `FileClose`, `Input`, `InputString`, `LineInput`, etc.) that are provided by [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] for backward compatibility.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="4a5de-106">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="4a5de-106">In This Section</span></span>  
 [<span data-ttu-id="4a5de-107">Lecture à partir de fichiers</span><span class="sxs-lookup"><span data-stu-id="4a5de-107">Reading from Files</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/reading-from-files.md)  
 <span data-ttu-id="4a5de-108">Répertorie les rubriques qui traitent de l’utilisation de l’objet `My.Computer.FileSystem` pour lire des fichiers.</span><span class="sxs-lookup"><span data-stu-id="4a5de-108">Lists topics dealing with using the `My.Computer.FileSystem` object to read from files</span></span>  
  
 [<span data-ttu-id="4a5de-109">Écriture dans des fichiers</span><span class="sxs-lookup"><span data-stu-id="4a5de-109">Writing to Files</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/writing-to-files.md)  
 <span data-ttu-id="4a5de-110">Répertorie les rubriques qui traitent de l’utilisation de l’objet `My.Computer.FileSystem` pour écrire dans des fichiers</span><span class="sxs-lookup"><span data-stu-id="4a5de-110">Lists topics dealing with using the `My.Computer.FileSystem` object to write to files</span></span>  
  
 [<span data-ttu-id="4a5de-111">Création, suppression et déplacement de fichiers et de répertoires</span><span class="sxs-lookup"><span data-stu-id="4a5de-111">Creating, Deleting, and Moving Files and Directories</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/creating-deleting-and-moving-files-and-directories.md)  
 <span data-ttu-id="4a5de-112">Répertorie les rubriques qui traitent de l’utilisation de l’objet `My.Computer.FileSystem` pour la création, la copie, la suppression et le déplacement de fichiers et de dossiers.</span><span class="sxs-lookup"><span data-stu-id="4a5de-112">Lists topics dealing with using the `My.Computer.FileSystem` object to creating, copying, deleting and moving files and folders.</span></span>  
  
 [<span data-ttu-id="4a5de-113">Analyse des fichiers texte avec l’objet TextFieldParser</span><span class="sxs-lookup"><span data-stu-id="4a5de-113">Parsing Text Files with the TextFieldParser Object</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/parsing-text-files-with-the-textfieldparser-object.md)  
 <span data-ttu-id="4a5de-114">Explique comment utiliser `TextFieldReader` pour analyser des fichiers texte tels que les journaux.</span><span class="sxs-lookup"><span data-stu-id="4a5de-114">Discusses how to use the `TextFieldReader` to parse text files such as logs.</span></span>  
  
 [<span data-ttu-id="4a5de-115">Codages de fichiers</span><span class="sxs-lookup"><span data-stu-id="4a5de-115">File Encodings</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/file-encodings.md)  
 <span data-ttu-id="4a5de-116">Décrit les encodages de fichiers et leur utilisation.</span><span class="sxs-lookup"><span data-stu-id="4a5de-116">Describes file encodings and their use.</span></span>  
  
 [<span data-ttu-id="4a5de-117">Procédure pas à pas : manipulation de fichiers et de répertoires en Visual Basic</span><span class="sxs-lookup"><span data-stu-id="4a5de-117">Walkthrough: Manipulating Files and Directories in Visual Basic</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/walkthrough-manipulating-files-and-directories.md)  
 <span data-ttu-id="4a5de-118">Montre comment créer un utilitaire qui fournit des informations sur les fichiers et les dossiers.</span><span class="sxs-lookup"><span data-stu-id="4a5de-118">Demonstrates how to create a utility that reports information about files and folders.</span></span>  
  
 [<span data-ttu-id="4a5de-119">Dépannage : lecture et écriture dans des fichiers texte</span><span class="sxs-lookup"><span data-stu-id="4a5de-119">Troubleshooting: Reading from and Writing to Text Files</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/troubleshooting-reading-from-and-writing-to-text-files.md)  
 <span data-ttu-id="4a5de-120">Répertorie les problèmes courants rencontrés lors des opérations de lecture et d’écriture dans des fichiers texte, et suggère des solutions pour chaque problème.</span><span class="sxs-lookup"><span data-stu-id="4a5de-120">Lists common problems encountered when reading and writing to text files, and suggests remedies for each.</span></span>

