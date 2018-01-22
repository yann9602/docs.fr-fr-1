---
title: TextFieldParser ne prend pas en charge les jetons de commentaires qui contiennent un blanc
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords: vbrTextFieldParser_WhitespaceInToken
ms.assetid: 55107656-270e-4bbb-841a-478904df8e07
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 0e5f41b1f1019459d55d5806f45301f4248e65fc
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/19/2018
---
# <a name="textfieldparser-does-not-support-comment-tokens-that-contain-whitespace"></a><span data-ttu-id="ecc42-102">TextFieldParser ne prend pas en charge les jetons de commentaires qui contiennent un blanc</span><span class="sxs-lookup"><span data-stu-id="ecc42-102">TextFieldParser does not support comment tokens that contain whitespace</span></span>
<span data-ttu-id="ecc42-103">Un jeton de commentaire qui contient un espace blanc a été fourni.</span><span class="sxs-lookup"><span data-stu-id="ecc42-103">A comment token that contains white space has been supplied.</span></span> <span data-ttu-id="ecc42-104">`TextFieldParser` ne prend pas en charge les jetons de commentaires qui contiennent un espace blanc, sauf si ce dernier se trouve au début du jeton.</span><span class="sxs-lookup"><span data-stu-id="ecc42-104">The `TextFieldParser` does not support comment tokens that contain white space unless the white space occurs at the beginning of the token.</span></span> <span data-ttu-id="ecc42-105">Un espace blanc situé au début d’un jeton est ignoré.</span><span class="sxs-lookup"><span data-stu-id="ecc42-105">White space occurring at the beginning of a token is ignored.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="ecc42-106">Pour corriger cette erreur</span><span class="sxs-lookup"><span data-stu-id="ecc42-106">To correct this error</span></span>  
  
-   <span data-ttu-id="ecc42-107">Fournissez un jeton de commentaire correct.</span><span class="sxs-lookup"><span data-stu-id="ecc42-107">Supply a correct comment token.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ecc42-108">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ecc42-108">See Also</span></span>  
 [<span data-ttu-id="ecc42-109">TextFieldParser.CommentTokens Property</span><span class="sxs-lookup"><span data-stu-id="ecc42-109">TextFieldParser.CommentTokens Property</span></span>](http://msdn.microsoft.com/library/2e6b6435-4bee-4c14-a353-e8f2c82e2d61)  
 [<span data-ttu-id="ecc42-110">Analyse des fichiers texte avec l’objet TextFieldParser</span><span class="sxs-lookup"><span data-stu-id="ecc42-110">Parsing Text Files with the TextFieldParser Object</span></span>](../../visual-basic/developing-apps/programming/drives-directories-files/parsing-text-files-with-the-textfieldparser-object.md)  
 [<span data-ttu-id="ecc42-111">TextFieldParser (objet)</span><span class="sxs-lookup"><span data-stu-id="ecc42-111">TextFieldParser Object</span></span>](../../visual-basic/language-reference/objects/textfieldparser-object.md)
