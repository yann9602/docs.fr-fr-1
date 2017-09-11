---
title: -highentropyva (Options du compilateur C#)
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- /highentropyva
dev_langs:
- CSharp
helpviewer_keywords:
- /highentropyva compiler option [C#]
- -highentropyva compiler option [C#]
- highentropyva compiler option [C#]
ms.assetid: eaf409b3-384e-49dd-9417-62453658f421
caps.latest.revision: 8
author: BillWagner
ms.author: wiwagn
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
ms.openlocfilehash: 4cb21c109fc33a30da016fd6a42285a3a3da02e2
ms.contentlocale: fr-fr
ms.lasthandoff: 07/28/2017

---
# <a name="highentropyva-c-compiler-options"></a><span data-ttu-id="c481e-102">/highentropyva (Options du compilateur C#)</span><span class="sxs-lookup"><span data-stu-id="c481e-102">/highentropyva (C# Compiler Options)</span></span>
<span data-ttu-id="c481e-103">L’option du compilateur **/highentropyva** indique au noyau Windows si un fichier exécutable particulier prend en charge la randomisation du format d’espace d’adresse (ASLR) de forte entropie.</span><span class="sxs-lookup"><span data-stu-id="c481e-103">The **/highentropyva** compiler option tells the Windows kernel whether a particular executable supports high entropy Address Space Layout Randomization (ASLR).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c481e-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c481e-104">Syntax</span></span>  
  
```console  
/highentropyva[+ | -]  
```  
  
## <a name="arguments"></a><span data-ttu-id="c481e-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="c481e-105">Arguments</span></span>  
 <span data-ttu-id="c481e-106">`+` &#124; `-`</span><span class="sxs-lookup"><span data-stu-id="c481e-106">`+` &#124; `-`</span></span>  
 <span data-ttu-id="c481e-107">Cette option spécifie qu’un exécutable 64 bits ou un exécutable marqué par l’option du compilateur [/platform:anycpu](../../../csharp/language-reference/compiler-options/platform-compiler-option.md) prend en charge un espace d’adressage virtuel d’entropie élevée.</span><span class="sxs-lookup"><span data-stu-id="c481e-107">This option specifies that a 64-bit executable or an executable that is marked by the [/platform:anycpu](../../../csharp/language-reference/compiler-options/platform-compiler-option.md) compiler option supports a high entropy virtual address space.</span></span> <span data-ttu-id="c481e-108">Cette option est désactivée par défaut.</span><span class="sxs-lookup"><span data-stu-id="c481e-108">The option is disabled by default.</span></span> <span data-ttu-id="c481e-109">Utilisez **/highentropyva+** ou **/highentropyva** pour l’activer.</span><span class="sxs-lookup"><span data-stu-id="c481e-109">Use **/highentropyva+** or **/highentropyva** to enable it.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c481e-110">Remarques</span><span class="sxs-lookup"><span data-stu-id="c481e-110">Remarks</span></span>  
 <span data-ttu-id="c481e-111">L’option **/highentropyva** permet à des versions compatibles du noyau Windows d’utiliser un degré d’entropie plus élevé lors de la randomisation du format de l’espace d’adresse d’un processus.</span><span class="sxs-lookup"><span data-stu-id="c481e-111">The **/highentropyva** option enables compatible versions of the Windows kernel to use higher degrees of entropy when randomizing the address space layout of a process as part of ASLR.</span></span> <span data-ttu-id="c481e-112">En utilisant un degré d’entropie plus élevé, vous pouvez allouer un plus grand nombre d’adresses aux zones de mémoire, telles que les piles et les tas.</span><span class="sxs-lookup"><span data-stu-id="c481e-112">Using higher degrees of entropy means that a larger number of addresses can be allocated to memory regions such as stacks and heaps.</span></span> <span data-ttu-id="c481e-113">Par conséquent, il est plus difficile de deviner l’emplacement d’une zone de mémoire.</span><span class="sxs-lookup"><span data-stu-id="c481e-113">As a result, it is more difficult to guess the location of a particular memory region.</span></span>  
  
 <span data-ttu-id="c481e-114">Lorsque l’option du compilateur **/highentropyva** est spécifiée, l’exécutable cible et tous les modules dont il dépend doivent être capables de gérer les valeurs de pointeur supérieures à 4 Go lorsqu’ils sont exécutés comme un processus 64 bits.</span><span class="sxs-lookup"><span data-stu-id="c481e-114">When the **/highentropyva** compiler option is specified, the target executable and any modules that it depends on must be able to handle pointer values that are larger than 4 gigabytes (GB) when they are running as a 64-bit process.</span></span>

