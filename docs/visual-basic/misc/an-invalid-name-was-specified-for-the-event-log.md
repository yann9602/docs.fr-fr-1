---
title: "Un nom de fichier non valide a été spécifié pour le journal des événements"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-visual-basic
ms.topic: article
ms.assetid: b1b158bd-f13f-4371-a8af-31c0e86ae6be
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 76e4082710a6786ec5e743ce606e849637c26512
ms.sourcegitcommit: 34ec7753acf76f90a0fa845235ef06663dc9e36e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/21/2017
---
# <a name="an-invalid-name-was-specified-for-the-event-log"></a><span data-ttu-id="e0601-102">Un nom de fichier non valide a été spécifié pour le journal des événements</span><span class="sxs-lookup"><span data-stu-id="e0601-102">An invalid name was specified for the event log</span></span>
<span data-ttu-id="e0601-103">Un nom de fichier non valide a été spécifié pour le journal des événements.</span><span class="sxs-lookup"><span data-stu-id="e0601-103">An invalid name was specified for the event log.</span></span> <span data-ttu-id="e0601-104">Cette erreur est généralement due à des caractères non valides dans le nom, à un nom de fichier vide ou à un nom de fichier trop long.</span><span class="sxs-lookup"><span data-stu-id="e0601-104">Usually this is a result of invalid characters in the name, a blank file name, or a file name that is too long.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="e0601-105">Pour corriger cette erreur</span><span class="sxs-lookup"><span data-stu-id="e0601-105">To correct this error</span></span>  
  
-   <span data-ttu-id="e0601-106">Si le nom spécifié fait plus de huit caractères, vérifiez qu’il n’existe aucun conflit avec les noms des autres journaux des événements.</span><span class="sxs-lookup"><span data-stu-id="e0601-106">If the specified name is more than eight characters, make sure there is no conflict with the names of other event logs.</span></span> <span data-ttu-id="e0601-107">Seuls les huit premiers caractères sont évalués pour déterminer si le nom est unique.</span><span class="sxs-lookup"><span data-stu-id="e0601-107">Only the first eight characters are evaluated when determining if the name is unique.</span></span>  
  
-   <span data-ttu-id="e0601-108">Si vous fournissez un chemin, vérifiez qu’il est correctement analysé.</span><span class="sxs-lookup"><span data-stu-id="e0601-108">If supplying a path, make sure it is parsed correctly.</span></span>  
  
-   <span data-ttu-id="e0601-109">Vérifiez que le nom ne contient aucun caractère non valide.</span><span class="sxs-lookup"><span data-stu-id="e0601-109">Check that there are no invalid characters in the name.</span></span> <span data-ttu-id="e0601-110">Les caractères `<`, `>`, `:`, `"`, `/`, `\`et `|`ne peuvent pas être utilisés dans un nom de fichier.</span><span class="sxs-lookup"><span data-stu-id="e0601-110">Characters that cannot be used in a file name include `<`, `>`, `:`, `"`, `/`, `\`, and `|`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e0601-111">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e0601-111">See Also</span></span>  
 [<span data-ttu-id="e0601-112">Guide pratique pour analyser des chemins</span><span class="sxs-lookup"><span data-stu-id="e0601-112">How to: Parse File Paths</span></span>](../../visual-basic/developing-apps/programming/drives-directories-files/how-to-parse-file-paths.md)  
 [<span data-ttu-id="e0601-113">Guide pratique : renommer un fichier</span><span class="sxs-lookup"><span data-stu-id="e0601-113">How to: Rename a File</span></span>](../../visual-basic/developing-apps/programming/drives-directories-files/how-to-rename-a-file.md)  
 
