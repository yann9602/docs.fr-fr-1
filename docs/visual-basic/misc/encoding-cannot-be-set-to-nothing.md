---
title: Le codage ne peut pas avoir la valeur Nothing
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-visual-basic
ms.topic: article
ms.assetid: 59f7c731-8291-4a85-bf51-c225e48cdc84
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 42baef6e0634849004290dce3db32e47f103282d
ms.sourcegitcommit: 34ec7753acf76f90a0fa845235ef06663dc9e36e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/21/2017
---
# <a name="encoding-cannot-be-set-to-nothing"></a><span data-ttu-id="4dc28-102">Le codage ne peut pas avoir la valeur Nothing</span><span class="sxs-lookup"><span data-stu-id="4dc28-102">Encoding cannot be set to Nothing</span></span>
<span data-ttu-id="4dc28-103">Une tentative de lecture ou d’écriture dans un fichier a échoué, car le paramètre `encoding` a la valeur `Nothing` , mais requiert une valeur valide.</span><span class="sxs-lookup"><span data-stu-id="4dc28-103">An attempt to read from or write to a file has failed because the parameter `encoding` has been set to `Nothing` but requires a valid value.</span></span>  
  
 <span data-ttu-id="4dc28-104"><xref:System.Text.Encoding> est utilisé pour déterminer le codage à utiliser lors de l’écriture dans un fichier.</span><span class="sxs-lookup"><span data-stu-id="4dc28-104"><xref:System.Text.Encoding> is used to determine what encoding to use when writing to a file.</span></span> <span data-ttu-id="4dc28-105">La valeur par défaut est UTF-8.</span><span class="sxs-lookup"><span data-stu-id="4dc28-105">The default is UTF-8.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="4dc28-106">Pour corriger cette erreur</span><span class="sxs-lookup"><span data-stu-id="4dc28-106">To correct this error</span></span>  
  
-   <span data-ttu-id="4dc28-107">Fournissez une valeur valide pour le paramètre `encoding` .</span><span class="sxs-lookup"><span data-stu-id="4dc28-107">Supply a valid value for the `encoding` parameter.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4dc28-108">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="4dc28-108">See Also</span></span>  
 [<span data-ttu-id="4dc28-109">Codages de fichiers</span><span class="sxs-lookup"><span data-stu-id="4dc28-109">File Encodings</span></span>](../../visual-basic/developing-apps/programming/drives-directories-files/file-encodings.md)  
 [<span data-ttu-id="4dc28-110">Lecture à partir de fichiers</span><span class="sxs-lookup"><span data-stu-id="4dc28-110">Reading from Files</span></span>](../../visual-basic/developing-apps/programming/drives-directories-files/reading-from-files.md)  
 [<span data-ttu-id="4dc28-111">Écriture dans des fichiers</span><span class="sxs-lookup"><span data-stu-id="4dc28-111">Writing to Files</span></span>](../../visual-basic/developing-apps/programming/drives-directories-files/writing-to-files.md)  
 [<span data-ttu-id="4dc28-112">My.Computer.FileSystem.ReadAllText</span><span class="sxs-lookup"><span data-stu-id="4dc28-112">My.Computer.FileSystem.ReadAllText</span></span>](xref:Microsoft.VisualBasic.FileIO.FileSystem.ReadAllText%2A)  
 [<span data-ttu-id="4dc28-113">My.Computer.FileSystem.WriteAllText</span><span class="sxs-lookup"><span data-stu-id="4dc28-113">My.Computer.FileSystem.WriteAllText</span></span>](xref:Microsoft.VisualBasic.FileIO.FileSystem.WriteAllText%2A)
