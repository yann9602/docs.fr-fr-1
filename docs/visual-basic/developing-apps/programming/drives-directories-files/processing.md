---
title: "Manipulation de lecteurs, de répertoires et de fichiers (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- drives
- drives, processing
- Visual Basic code, file access
- files [Visual Basic], processing
- files [Visual Basic], accessing
- directories [Visual Studio], processing
ms.assetid: f1db14c8-a4fd-4d0b-8323-c7cb29d688c2
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 27a5c3c389860cdc29c4263edbff492738ffe565
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="processing-drives-directories-and-files-visual-basic"></a><span data-ttu-id="d94a8-102">Manipulation de lecteurs, de répertoires et de fichiers (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="d94a8-102">Processing Drives, Directories, and Files (Visual Basic)</span></span>
<span data-ttu-id="d94a8-103">Vous pouvez utiliser [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] pour manipuler des lecteurs, des dossiers et des fichiers avec l’objet `My.Computer.FileSystem`. Cet objet offre de meilleures performances et est plus facile à utiliser que les méthodes traditionnelles telles que les fonctions `FileOpen` et `Write` (celles-ci restent toutefois disponibles).</span><span class="sxs-lookup"><span data-stu-id="d94a8-103">You can use [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] to process drives, folders, and files with the `My.Computer.FileSystem` object, which provides better performance and is easier to use than traditional methods such as the `FileOpen` and `Write` functions (although they are still available).</span></span> <span data-ttu-id="d94a8-104">Ces méthodes sont détaillées dans les sections suivantes.</span><span class="sxs-lookup"><span data-stu-id="d94a8-104">The following sections discuss these methods in detail.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="d94a8-105">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="d94a8-105">In This Section</span></span>  
 [<span data-ttu-id="d94a8-106">Accès au fichier avec Visual Basic</span><span class="sxs-lookup"><span data-stu-id="d94a8-106">File Access with Visual Basic</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/file-access.md)  
 <span data-ttu-id="d94a8-107">Explique comment utiliser l’objet `My.Computer.FileSystem` pour manipuler des fichiers, des lecteurs et des dossiers.</span><span class="sxs-lookup"><span data-stu-id="d94a8-107">Discusses how to use the `My.Computer.FileSystem` object to work with files, drives, and folders.</span></span>  
  
 [<span data-ttu-id="d94a8-108">Concepts de base du système de fichiers et des E/S de fichier du .NET Framework (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="d94a8-108">Basics of .NET Framework File I/O and the File System (Visual Basic)</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/basics-of-net-framework-file-io-and-the-file-system.md)  
 <span data-ttu-id="d94a8-109">Fournit une vue d’ensemble des concepts d’E/S de fichier dans le .NET Framework, à savoir les flux, le stockage isolé, les événements de fichier, les attributs de fichier et l’accès aux fichiers.</span><span class="sxs-lookup"><span data-stu-id="d94a8-109">Provides an overview of file I/O concepts in the .NET Framework, including streams, isolated storage, file events, file attributes, and file access.</span></span>  
  
 [<span data-ttu-id="d94a8-110">Procédure pas à pas : manipulation de fichiers à l’aide de méthodes du .NET Framework</span><span class="sxs-lookup"><span data-stu-id="d94a8-110">Walkthrough: Manipulating Files by Using .NET Framework Methods</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/walkthrough-manipulating-files-by-using-net-framework-methods.md)  
 <span data-ttu-id="d94a8-111">Montre comment utiliser le [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] pour manipuler des fichiers et des dossiers.</span><span class="sxs-lookup"><span data-stu-id="d94a8-111">Demonstrates how to use the [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] to manipulate files and folders.</span></span>  
  
 [<span data-ttu-id="d94a8-112">Procédure pas à pas : manipulation de fichiers et de répertoires dans Visual Basic</span><span class="sxs-lookup"><span data-stu-id="d94a8-112">Walkthrough: Manipulating Files and Directories in Visual Basic</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/walkthrough-manipulating-files-and-directories.md)  
 <span data-ttu-id="d94a8-113">Montre comment utiliser l’objet `My.Computer.FileSystem` pour manipuler des fichiers et des dossiers.</span><span class="sxs-lookup"><span data-stu-id="d94a8-113">Demonstrates how to use the `My.Computer.FileSystem` object to manipulate files and folders.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="d94a8-114">Rubriques connexes</span><span class="sxs-lookup"><span data-stu-id="d94a8-114">Related Sections</span></span>  
 [<span data-ttu-id="d94a8-115">Structure de programme et conventions de codage</span><span class="sxs-lookup"><span data-stu-id="d94a8-115">Program Structure and Code Conventions</span></span>](../../../../visual-basic/programming-guide/program-structure/program-structure-and-code-conventions.md)  
 <span data-ttu-id="d94a8-116">Fournit des indications relatives à la structure physique et l’apparence des programmes.</span><span class="sxs-lookup"><span data-stu-id="d94a8-116">Provides guidelines for the physical structure and appearance of programs.</span></span>  
  
 <xref:Microsoft.VisualBasic.FileIO.FileSystem>  
 <span data-ttu-id="d94a8-117">Fournit une documentation de référence pour l’objet `My.Computer.FileSystem` et ses membres.</span><span class="sxs-lookup"><span data-stu-id="d94a8-117">Reference documentation for the `My.Computer.FileSystem` object and its members.</span></span>
