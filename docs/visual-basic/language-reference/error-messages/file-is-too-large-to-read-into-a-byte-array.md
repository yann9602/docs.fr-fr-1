---
title: "Le fichier est trop volumineux pour être lu dans un tableau d'octets"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
ms.assetid: 686630a6-a439-46c7-8d7b-34613ae4c5d8
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 2bbdb5a4dcaa22ca84428ef28c8838a6d9a0ee1b
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="file-is-too-large-to-read-into-a-byte-array"></a><span data-ttu-id="db1e6-102">Le fichier est trop volumineux pour être lu dans un tableau d'octets</span><span class="sxs-lookup"><span data-stu-id="db1e6-102">File is too large to read into a byte array</span></span>
<span data-ttu-id="db1e6-103">La taille du fichier que vous tentez de lire dans un tableau d’octets dépasse 4 Go.</span><span class="sxs-lookup"><span data-stu-id="db1e6-103">The size of the file you are attempting to read into a byte array exceeds 4 GB.</span></span> <span data-ttu-id="db1e6-104">Le `My.Computer.FileSystem.ReadAllBytes` méthode ne peut pas lire un fichier qui dépasse cette taille.</span><span class="sxs-lookup"><span data-stu-id="db1e6-104">The `My.Computer.FileSystem.ReadAllBytes` method cannot read a file that exceeds this size.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="db1e6-105">Pour corriger cette erreur</span><span class="sxs-lookup"><span data-stu-id="db1e6-105">To correct this error</span></span>  
  
-   <span data-ttu-id="db1e6-106">Utilisez un <xref:System.IO.StreamReader> pour lire le fichier.</span><span class="sxs-lookup"><span data-stu-id="db1e6-106">Use a <xref:System.IO.StreamReader> to read the file.</span></span> <span data-ttu-id="db1e6-107">Pour plus d’informations, consultez [principes de base de .NET Framework fichier e/s et le système de fichiers (Visual Basic)](../../../visual-basic/developing-apps/programming/drives-directories-files/basics-of-net-framework-file-io-and-the-file-system.md).</span><span class="sxs-lookup"><span data-stu-id="db1e6-107">For more information, see [Basics of .NET Framework File I/O and the File System (Visual Basic)](../../../visual-basic/developing-apps/programming/drives-directories-files/basics-of-net-framework-file-io-and-the-file-system.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="db1e6-108">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="db1e6-108">See Also</span></span>  
 <xref:Microsoft.VisualBasic.FileIO.FileSystem.ReadAllBytes%2A>  
 <xref:System.IO.StreamReader>  
 [<span data-ttu-id="db1e6-109">Accès au fichier avec Visual Basic</span><span class="sxs-lookup"><span data-stu-id="db1e6-109">File Access with Visual Basic</span></span>](../../../visual-basic/developing-apps/programming/drives-directories-files/file-access.md)  
 [<span data-ttu-id="db1e6-110">Guide pratique : lire le texte des fichiers avec un StreamReader</span><span class="sxs-lookup"><span data-stu-id="db1e6-110">How to: Read Text from Files with a StreamReader</span></span>](../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-read-text-from-files-with-a-streamreader.md)
