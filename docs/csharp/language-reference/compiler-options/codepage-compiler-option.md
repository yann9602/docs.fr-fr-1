---
title: "-codepage (Options du compilateur C#)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- /codepage
dev_langs:
- CSharp
helpviewer_keywords:
- /codepage compiler option [C#]
- codepage compiler option [C#]
- -codepage compiler option [C#]
ms.assetid: 75942989-b69a-4308-90a0-840c73d2c478
caps.latest.revision: 15
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
ms.openlocfilehash: b80f6fcf8891d2f0b921af01cc094f624d807aa1
ms.contentlocale: fr-fr
ms.lasthandoff: 07/28/2017

---
# <a name="codepage-c-compiler-options"></a><span data-ttu-id="8793f-102">/codepage (Options du compilateur C#)</span><span class="sxs-lookup"><span data-stu-id="8793f-102">/codepage (C# Compiler Options)</span></span>
<span data-ttu-id="8793f-103">Cette option spécifie la page de codes à utiliser pendant la compilation si la page exigée n’est pas la page de codes par défaut actuelle du système.</span><span class="sxs-lookup"><span data-stu-id="8793f-103">This option specifies which codepage to use during compilation if the required page is not the current default codepage for the system.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8793f-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="8793f-104">Syntax</span></span>  
  
```console  
/codepage:id  
```  
  
## <a name="arguments"></a><span data-ttu-id="8793f-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="8793f-105">Arguments</span></span>  
 `id`  
 <span data-ttu-id="8793f-106">Identificateur de la page de codes à utiliser pour tous les fichiers de code source de la compilation.</span><span class="sxs-lookup"><span data-stu-id="8793f-106">The id of the code page to use for all source code files in the compilation.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="8793f-107">Remarques</span><span class="sxs-lookup"><span data-stu-id="8793f-107">Remarks</span></span>  
 <span data-ttu-id="8793f-108">Si vous compilez un ou plusieurs fichiers de code source n’ayant pas été créés pour utiliser la page de codes par défaut de votre ordinateur, vous pouvez utiliser l’option **/codepage** pour spécifier la page de codes à utiliser.</span><span class="sxs-lookup"><span data-stu-id="8793f-108">If you compile one or more source code files that were not created to use the default code page on your computer, you can use the **/codepage** option to specify which code page should be used.</span></span> <span data-ttu-id="8793f-109">**/codepage** s’applique à tous les fichiers de code source inclus dans votre compilation.</span><span class="sxs-lookup"><span data-stu-id="8793f-109">**/codepage** applies to all source code files in your compilation.</span></span>  
  
 <span data-ttu-id="8793f-110">Il n’est pas nécessaire d’utiliser **/codepage** si les fichiers de code source ont été créés avec la même page de codes que celle en vigueur sur votre ordinateur ou bien avec le format de codage UNICODE ou UTF-8.</span><span class="sxs-lookup"><span data-stu-id="8793f-110">If the source code files were created with the same codepage that is in effect on your computer or if the source code files were created with UNICODE or UTF-8, you need not use **/codepage**.</span></span>  
  
 <span data-ttu-id="8793f-111">Pour plus d’informations sur la façon de savoir quelles pages de codes sont prises en charge sur votre système, consultez [GetCPInfo](http://go.microsoft.com/fwlink/?LinkId=148371).</span><span class="sxs-lookup"><span data-stu-id="8793f-111">See [GetCPInfo](http://go.microsoft.com/fwlink/?LinkId=148371) for information on how to find which code pages are supported on your system.</span></span>  
  
 <span data-ttu-id="8793f-112">Cette option de compilateur n’est pas disponible dans Visual Studio et ne peut pas être changée par programmation.</span><span class="sxs-lookup"><span data-stu-id="8793f-112">This compiler option is unavailable in Visual Studio and cannot be changed programmatically.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8793f-113">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="8793f-113">See Also</span></span>  
 <span data-ttu-id="8793f-114">[Options du compilateur C#](../../../csharp/language-reference/compiler-options/index.md) </span><span class="sxs-lookup"><span data-stu-id="8793f-114">[C# Compiler Options](../../../csharp/language-reference/compiler-options/index.md) </span></span>  
 [<span data-ttu-id="8793f-115">Gestion des propriétés des projets et des solutions</span><span class="sxs-lookup"><span data-stu-id="8793f-115">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)

