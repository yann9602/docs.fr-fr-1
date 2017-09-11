---
title: /filealign | Documents Microsoft
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
- sections compiler option [Visual Basic]
- alignment compiler option [Visual Basic]
- -filealign compiler option [Visual Basic]
- section alignment
- /filealign compiler option [Visual Basic]
- filealign compiler option [Visual Basic]
ms.assetid: cc61ec3d-ad38-4b28-9659-099d73cad099
caps.latest.revision: 14
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
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: 5e0cd0a2a7e4c88df1087faee963f541c325b272
ms.contentlocale: fr-fr
ms.lasthandoff: 04/12/2017

---
# <a name="filealign"></a><span data-ttu-id="315d8-102">/filealign</span><span class="sxs-lookup"><span data-stu-id="315d8-102">/filealign</span></span>
<span data-ttu-id="315d8-103">Spécifie où les sections du fichier de sortie doivent être alignées.</span><span class="sxs-lookup"><span data-stu-id="315d8-103">Specifies where to align the sections of the output file.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="315d8-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="315d8-104">Syntax</span></span>  
  
```  
/filealign:number  
```  
  
## <a name="arguments"></a><span data-ttu-id="315d8-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="315d8-105">Arguments</span></span>  
 `number`  
 <span data-ttu-id="315d8-106">Obligatoire.</span><span class="sxs-lookup"><span data-stu-id="315d8-106">Required.</span></span> <span data-ttu-id="315d8-107">Une valeur qui spécifie l’alignement des sections dans le fichier de sortie.</span><span class="sxs-lookup"><span data-stu-id="315d8-107">A value that specifies the alignment of sections in the output file.</span></span> <span data-ttu-id="315d8-108">Les valeurs valides sont 512, 1024, 2048, 4096 et 8192.</span><span class="sxs-lookup"><span data-stu-id="315d8-108">Valid values are 512, 1024, 2048, 4096, and 8192.</span></span> <span data-ttu-id="315d8-109">Ces valeurs sont exprimées en octets.</span><span class="sxs-lookup"><span data-stu-id="315d8-109">These values are in bytes.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="315d8-110">Remarques</span><span class="sxs-lookup"><span data-stu-id="315d8-110">Remarks</span></span>  
 <span data-ttu-id="315d8-111">Vous pouvez utiliser la `/filealign` option pour spécifier l’alignement des sections dans votre fichier de sortie.</span><span class="sxs-lookup"><span data-stu-id="315d8-111">You can use the `/filealign` option to specify the alignment of sections in your output file.</span></span> <span data-ttu-id="315d8-112">Les sections sont les blocs de mémoire contiguë dans un fichier exécutable Portable (PE) qui contient du code ou des données.</span><span class="sxs-lookup"><span data-stu-id="315d8-112">Sections are blocks of contiguous memory in a Portable Executable (PE) file that contains either code or data.</span></span> <span data-ttu-id="315d8-113">La `/filealign` option vous permet de compiler votre application avec un alignement non standard ; la plupart des développeurs n’avez pas besoin d’utiliser cette option.</span><span class="sxs-lookup"><span data-stu-id="315d8-113">The `/filealign` option lets you compile your application with a nonstandard alignment; most developers do not need to use this option.</span></span>  
  
 <span data-ttu-id="315d8-114">Chaque section est alignée sur une limite qui est un multiple de la `/filealign` valeur.</span><span class="sxs-lookup"><span data-stu-id="315d8-114">Each section is aligned on a boundary that is a multiple of the `/filealign` value.</span></span> <span data-ttu-id="315d8-115">Il n’existe aucune valeur par défaut fixe.</span><span class="sxs-lookup"><span data-stu-id="315d8-115">There is no fixed default.</span></span> <span data-ttu-id="315d8-116">Si `/filealign` n’est pas spécifié, le compilateur sélectionne la valeur par défaut au moment de la compilation.</span><span class="sxs-lookup"><span data-stu-id="315d8-116">If `/filealign` is not specified, the compiler picks a default at compile time.</span></span>  
  
 <span data-ttu-id="315d8-117">En spécifiant la taille de la section, vous pouvez modifier la taille du fichier de sortie.</span><span class="sxs-lookup"><span data-stu-id="315d8-117">By specifying the section size, you can change the size of the output file.</span></span> <span data-ttu-id="315d8-118">Modification de la taille de la section peut être utile pour les programmes qui seront exécuteront sur les périphériques de petite taille.</span><span class="sxs-lookup"><span data-stu-id="315d8-118">Modifying section size may be useful for programs that will run on smaller devices.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="315d8-119">La `/filealign` option n’est pas disponible dans l’environnement de développement Visual Studio ; il est disponible uniquement lors de la compilation à partir de la ligne de commande.</span><span class="sxs-lookup"><span data-stu-id="315d8-119">The `/filealign` option is not available from within the Visual Studio development environment; it is available only when compiling from the command line.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="315d8-120">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="315d8-120">See Also</span></span>  
 [<span data-ttu-id="315d8-121">Compilateur de ligne de commande de Visual Basic</span><span class="sxs-lookup"><span data-stu-id="315d8-121">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)
