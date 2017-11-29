---
title: Mode de fichier incorrect
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords: vbrID54
ms.assetid: 74891e96-884b-4c8d-872d-cd11ae272372
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: a540135727eb97f4df5027e2ded7271e21bb4648
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="bad-file-mode"></a><span data-ttu-id="2b20f-102">Mode de fichier incorrect</span><span class="sxs-lookup"><span data-stu-id="2b20f-102">Bad file mode</span></span>
<span data-ttu-id="2b20f-103">Les instructions utilisées pour la manipulation du contenu du fichier doivent être adaptées au mode dans lequel le fichier a été ouvert.</span><span class="sxs-lookup"><span data-stu-id="2b20f-103">Statements used in manipulating file contents must be appropriate to the mode in which the file was opened.</span></span> <span data-ttu-id="2b20f-104">Plusieurs causes sont possibles :</span><span class="sxs-lookup"><span data-stu-id="2b20f-104">Possible causes include:</span></span>  
  
-   <span data-ttu-id="2b20f-105">A `FilePutObject` ou `FileGetObject` instruction spécifie un fichier séquentiel.</span><span class="sxs-lookup"><span data-stu-id="2b20f-105">A `FilePutObject` or `FileGetObject` statement specifies a sequential file.</span></span>  
  
-   <span data-ttu-id="2b20f-106">A `Print` instruction spécifie un fichier ouvert pour un mode d’accès autre que `Output` ou `Append`.</span><span class="sxs-lookup"><span data-stu-id="2b20f-106">A `Print` statement specifies a file opened for an access mode other than `Output` or `Append`.</span></span>  
  
-   <span data-ttu-id="2b20f-107">Un `Input` instruction spécifie un fichier ouvert pour un mode d’accès autre que`Input`</span><span class="sxs-lookup"><span data-stu-id="2b20f-107">An `Input` statement specifies a file opened for an access mode other than `Input`</span></span>  
  
-   <span data-ttu-id="2b20f-108">Toute tentative d’écriture dans un fichier en lecture seule.</span><span class="sxs-lookup"><span data-stu-id="2b20f-108">An attempt to write to a read-only file.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="2b20f-109">Pour corriger cette erreur</span><span class="sxs-lookup"><span data-stu-id="2b20f-109">To correct this error</span></span>  
  
-   <span data-ttu-id="2b20f-110">Assurez-vous que `FilePutObject` et `FileGetObject` font uniquement référence à des fichiers ouverts pour `Random` ou `Binary` accès.</span><span class="sxs-lookup"><span data-stu-id="2b20f-110">Make sure `FilePutObject` and `FileGetObject` are only referring to files open for `Random` or `Binary` access.</span></span>  
  
-   <span data-ttu-id="2b20f-111">Assurez-vous que `Print` spécifie un fichier ouvert pour un `Output` ou `Append` mode d’accès.</span><span class="sxs-lookup"><span data-stu-id="2b20f-111">Make sure `Print` specifies a file opened for either `Output` or `Append` access mode.</span></span> <span data-ttu-id="2b20f-112">Si ce n’est pas le cas, utilisez une instruction différente pour placer des données dans le fichier ou rouvrez le fichier dans un mode approprié.</span><span class="sxs-lookup"><span data-stu-id="2b20f-112">If not, use a different statement to place data in the file, or reopen the file in an appropriate mode.</span></span>  
  
-   <span data-ttu-id="2b20f-113">Assurez-vous que `Input` spécifie un fichier ouvert pour `Input`.</span><span class="sxs-lookup"><span data-stu-id="2b20f-113">Make sure `Input` specifies a file opened for `Input`.</span></span> <span data-ttu-id="2b20f-114">Si ce n’est pas le cas, utilisez une instruction différente pour placer des données dans le fichier ou rouvrez le fichier dans un mode approprié.</span><span class="sxs-lookup"><span data-stu-id="2b20f-114">If not, use a different statement to place data in the file or reopen the file in an appropriate mode.</span></span>  
  
-   <span data-ttu-id="2b20f-115">Si vous écrivez dans un fichier en lecture seule, de modifier l’état de lecture/écriture du fichier ou n’essayez pas d’écrire dedans.</span><span class="sxs-lookup"><span data-stu-id="2b20f-115">If you are writing to a read-only file, change the read/write status of the file or do not try to write to it.</span></span>  
  
-   <span data-ttu-id="2b20f-116">Utilisez les fonctionnalités disponibles dans l’objet `My.Computer.FileSystem` .</span><span class="sxs-lookup"><span data-stu-id="2b20f-116">Use the functionality available in the `My.Computer.FileSystem` object.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2b20f-117">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="2b20f-117">See Also</span></span>  
 <xref:Microsoft.VisualBasic.FileSystem>  
 [<span data-ttu-id="2b20f-118">Dépannage : lecture et écriture dans des fichiers texte</span><span class="sxs-lookup"><span data-stu-id="2b20f-118">Troubleshooting: Reading from and Writing to Text Files</span></span>](../../../visual-basic/developing-apps/programming/drives-directories-files/troubleshooting-reading-from-and-writing-to-text-files.md)
