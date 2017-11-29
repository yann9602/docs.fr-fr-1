---
title: Erreur de chargement de la DLL (Visual Basic)
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords: vbrID48
ms.assetid: 4226cd1f-028c-477d-88a5-cb57f7e0cdc8
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: cc557dcc6709178b6519adb56f31debcbd1d1c39
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="error-in-loading-dll-visual-basic"></a><span data-ttu-id="0597a-102">Erreur de chargement de la DLL (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="0597a-102">Error in loading DLL (Visual Basic)</span></span>
<span data-ttu-id="0597a-103">Une bibliothèque de liens dynamiques (DLL) est une bibliothèque spécifiée dans la `Lib` clause d’un `Declare` instruction.</span><span class="sxs-lookup"><span data-stu-id="0597a-103">A dynamic-link library (DLL) is a library specified in the `Lib` clause of a `Declare` statement.</span></span> <span data-ttu-id="0597a-104">Les causes possibles de cette erreur sont les suivantes :</span><span class="sxs-lookup"><span data-stu-id="0597a-104">Possible causes for this error include:</span></span>  
  
-   <span data-ttu-id="0597a-105">Le fichier n’est pas exécutable DLL.</span><span class="sxs-lookup"><span data-stu-id="0597a-105">The file is not DLL executable.</span></span>  
  
-   <span data-ttu-id="0597a-106">Le fichier n’est pas une DLL Microsoft Windows.</span><span class="sxs-lookup"><span data-stu-id="0597a-106">The file is not a Microsoft Windows DLL.</span></span>  
  
-   <span data-ttu-id="0597a-107">La DLL fait référence à une autre DLL qui n’est pas présente.</span><span class="sxs-lookup"><span data-stu-id="0597a-107">The DLL references another DLL that is not present.</span></span>  
  
-   <span data-ttu-id="0597a-108">Le fichier DLL ou la DLL référencée n’est pas un répertoire spécifié dans le chemin d’accès.</span><span class="sxs-lookup"><span data-stu-id="0597a-108">The DLL or referenced DLL is not in a directory specified in the path.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="0597a-109">Pour corriger cette erreur</span><span class="sxs-lookup"><span data-stu-id="0597a-109">To correct this error</span></span>  
  
-   <span data-ttu-id="0597a-110">Si le fichier est un fichier texte source et par conséquent pas un exécutable DLL, il doit être compilé et lié à un formulaire exécutable DLL.</span><span class="sxs-lookup"><span data-stu-id="0597a-110">If the file is a source-text file and therefore not DLL executable, it must be compiled and linked to a DLL-executable form.</span></span>  
  
-   <span data-ttu-id="0597a-111">Si le fichier n’est pas une DLL Microsoft Windows, obtenir l’équivalent Microsoft Windows.</span><span class="sxs-lookup"><span data-stu-id="0597a-111">If the file is not a Microsoft Windows DLL, obtain the Microsoft Windows equivalent.</span></span>  
  
-   <span data-ttu-id="0597a-112">Si la DLL fait référence à une autre DLL qui n’est pas présente, obtenir la DLL référencée et le rendre disponible.</span><span class="sxs-lookup"><span data-stu-id="0597a-112">If the DLL references another DLL that is not present, obtain the referenced DLL and make it available.</span></span>  
  
-   <span data-ttu-id="0597a-113">Si le fichier DLL ou la DLL référencée n’est pas un répertoire spécifié par le chemin d’accès, déplacez la DLL vers un répertoire référencé.</span><span class="sxs-lookup"><span data-stu-id="0597a-113">If the DLL or referenced DLL is not in a directory specified by the path, move the DLL to a referenced directory.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0597a-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="0597a-114">See Also</span></span>  
 [<span data-ttu-id="0597a-115">Declare (instruction)</span><span class="sxs-lookup"><span data-stu-id="0597a-115">Declare Statement</span></span>](../../../visual-basic/language-reference/statements/declare-statement.md)
