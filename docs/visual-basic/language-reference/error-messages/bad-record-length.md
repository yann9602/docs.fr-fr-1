---
title: Longueur d'enregistrement incorrecte
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords: vbrID59
ms.assetid: 0926a3a4-177b-4452-9b33-d8a01e24cc21
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 747d62cb41ef841b4486e0c7108c37a86929683e
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="bad-record-length"></a><span data-ttu-id="894de-102">Longueur d'enregistrement incorrecte</span><span class="sxs-lookup"><span data-stu-id="894de-102">Bad record length</span></span>
<span data-ttu-id="894de-103">Cette erreur peut avoir plusieurs causes, dont les suivantes :</span><span class="sxs-lookup"><span data-stu-id="894de-103">Among the possible causes of this error are:</span></span>  
  
-   <span data-ttu-id="894de-104">La longueur d’une variable d’enregistrement spécifiée dans un `FileGet`, `FileGetObject`, `FilePut` ou `FilePutObject` instruction diffère de la longueur spécifiée dans correspondant `FileOpen` instruction.</span><span class="sxs-lookup"><span data-stu-id="894de-104">The length of a record variable specified in a `FileGet`, `FileGetObject`, `FilePut` or `FilePutObject` statement differs from the length specified in the corresponding `FileOpen` statement.</span></span>  
  
-   <span data-ttu-id="894de-105">La variable dans un `FilePut` ou `FilePutObject` instruction est ou inclut une chaîne de longueur variable.</span><span class="sxs-lookup"><span data-stu-id="894de-105">The variable in a `FilePut` or `FilePutObject` statement is or includes a variable-length string.</span></span>  
  
-   <span data-ttu-id="894de-106">La variable dans un `FilePut` ou `FilePutObject` est ou inclut un `Variant` type.</span><span class="sxs-lookup"><span data-stu-id="894de-106">The variable in a `FilePut` or `FilePutObject` is or includes a `Variant` type.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="894de-107">Pour corriger cette erreur</span><span class="sxs-lookup"><span data-stu-id="894de-107">To correct this error</span></span>  
  
1.  <span data-ttu-id="894de-108">Assurez-vous que la somme des tailles des variables à longueur fixe dans le type défini par l’utilisateur de définition de type de la variable d’enregistrement est identique à la valeur indiquée dans le `FileOpen` l’instruction `Len` clause.</span><span class="sxs-lookup"><span data-stu-id="894de-108">Make sure the sum of the sizes of fixed-length variables in the user-defined type defining the record variable's type is the same as the value stated in the `FileOpen` statement's `Len` clause.</span></span>  
  
2.  <span data-ttu-id="894de-109">Si la variable dans un `FilePut` ou `FilePutObject` instruction est ou inclut une chaîne de longueur variable, vérifiez que la chaîne de longueur variable est au moins 2 caractères plus courtes que la longueur d’enregistrement spécifiée dans le `Len` clause de la `FileOpen` instruction.</span><span class="sxs-lookup"><span data-stu-id="894de-109">If the variable in a `FilePut` or `FilePutObject` statement is or includes a variable-length string, make sure the variable-length string is at least 2 characters shorter than the record length specified in the `Len` clause of the `FileOpen` statement.</span></span>  
  
3.  <span data-ttu-id="894de-110">Si la variable dans un `FilePut` ou `FilePutObject` est ou inclut un `Variant` Assurez-vous que la chaîne de longueur variable est au moins de 4 octets plus court que la longueur d’enregistrement spécifiée dans le `Len` clause de la `FileOpen` instruction.</span><span class="sxs-lookup"><span data-stu-id="894de-110">If the variable in a `FilePut` or `FilePutObject` is or includes a `Variant` make sure the variable-length string is at least 4 bytes shorter than the record length specified in the `Len` clause of the `FileOpen` statement.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="894de-111">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="894de-111">See Also</span></span>  
 <xref:Microsoft.VisualBasic.FileSystem.FileGet%2A>  
 <xref:Microsoft.VisualBasic.FileSystem.FileGetObject%2A>  
 <xref:Microsoft.VisualBasic.FileSystem.FilePut%2A>  
 <xref:Microsoft.VisualBasic.FileSystem.FilePutObject%2A>
