---
title: /delaysign | Documents Microsoft
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
- delaysign compiler option [Visual Basic]
- /delaysign compiler option [Visual Basic]
- -delaysign compiler option [Visual Basic]
ms.assetid: c76e61a4-1884-4252-9fb2-377f99caa690
caps.latest.revision: 19
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
ms.openlocfilehash: bcc819e08ca7731d91dc77dc831060bcf00a4425
ms.contentlocale: fr-fr
ms.lasthandoff: 04/12/2017

---
# <a name="delaysign"></a><span data-ttu-id="af337-102">/delaysign</span><span class="sxs-lookup"><span data-stu-id="af337-102">/delaysign</span></span>
<span data-ttu-id="af337-103">Spécifie si l'assembly sera complètement ou partiellement signé.</span><span class="sxs-lookup"><span data-stu-id="af337-103">Specifies whether the assembly will be fully or partially signed.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="af337-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="af337-104">Syntax</span></span>  
  
```  
/delaysign[+ | -]  
```  
  
## <a name="arguments"></a><span data-ttu-id="af337-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="af337-105">Arguments</span></span>  
 <span data-ttu-id="af337-106">`+` &#124; `-`</span><span class="sxs-lookup"><span data-stu-id="af337-106">`+` &#124; `-`</span></span>  
 <span data-ttu-id="af337-107">Facultatif.</span><span class="sxs-lookup"><span data-stu-id="af337-107">Optional.</span></span> <span data-ttu-id="af337-108">Utilisez `/delaysign-` si vous souhaitez obtenir un assembly complètement signé.</span><span class="sxs-lookup"><span data-stu-id="af337-108">Use `/delaysign-` if you want a fully signed assembly.</span></span> <span data-ttu-id="af337-109">Utilisez `/delaysign+` si vous souhaitez placer la clé publique dans l’assembly et réserve l’espace pour le hachage signé.</span><span class="sxs-lookup"><span data-stu-id="af337-109">Use `/delaysign+` if you want to place the public key in the assembly and reserve space for the signed hash.</span></span> <span data-ttu-id="af337-110">La valeur par défaut est `/delaysign-`.</span><span class="sxs-lookup"><span data-stu-id="af337-110">The default is `/delaysign-`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="af337-111">Remarques</span><span class="sxs-lookup"><span data-stu-id="af337-111">Remarks</span></span>  
 <span data-ttu-id="af337-112">Le `/delaysign` option est sans effet sauf si utilisée avec [/keyfile](../../../visual-basic/reference/command-line-compiler/keyfile.md) ou [/keycontainer](../../../visual-basic/reference/command-line-compiler/keycontainer.md).</span><span class="sxs-lookup"><span data-stu-id="af337-112">The `/delaysign` option has no effect unless used with [/keyfile](../../../visual-basic/reference/command-line-compiler/keyfile.md) or [/keycontainer](../../../visual-basic/reference/command-line-compiler/keycontainer.md).</span></span>  
  
 <span data-ttu-id="af337-113">Lorsque vous demandez un assembly totalement signé, le compilateur hache le fichier qui contient le manifeste (métadonnées de l’assembly) et signe ce hachage avec la clé privée.</span><span class="sxs-lookup"><span data-stu-id="af337-113">When you request a fully signed assembly, the compiler hashes the file that contains the manifest (assembly metadata) and signs that hash with the private key.</span></span> <span data-ttu-id="af337-114">La signature numérique obtenue est stockée dans le fichier qui contient le manifeste.</span><span class="sxs-lookup"><span data-stu-id="af337-114">The resulting digital signature is stored in the file that contains the manifest.</span></span> <span data-ttu-id="af337-115">Lorsqu’un assembly est différée, le compilateur ne calcule pas et stocke la signature, mais réserve d’espace dans le fichier pour la signature puisse être ajoutée ultérieurement.</span><span class="sxs-lookup"><span data-stu-id="af337-115">When an assembly is delay signed, the compiler does not compute and store the signature but reserves space in the file so the signature can be added later.</span></span>  
  
 <span data-ttu-id="af337-116">Par exemple, en utilisant `/delaysign+`, un développeur d’une organisation peut distribuer des versions de test non signé d’un assembly que les testeurs peuvent enregistrer dans le global assembly cache et utiliser.</span><span class="sxs-lookup"><span data-stu-id="af337-116">For example, by using `/delaysign+`, a developer in an organization can distribute unsigned test versions of an assembly that testers can register with the global assembly cache and use.</span></span> <span data-ttu-id="af337-117">Lorsque le travail sur l’assembly est terminé, la personne responsable de la clé privée de l’organisation peut signer complètement l’assembly.</span><span class="sxs-lookup"><span data-stu-id="af337-117">When work on the assembly is completed, the person responsible for the organization's private key can fully sign the assembly.</span></span> <span data-ttu-id="af337-118">Ce compartimentage protège la clé privée de l’organisation contre toute divulgation, tout en permettant à tous les développeurs de travailler sur les assemblys.</span><span class="sxs-lookup"><span data-stu-id="af337-118">This compartmentalization protects the organization's private key from disclosure, while allowing all developers to work on the assemblies.</span></span>  
  
 <span data-ttu-id="af337-119">Consultez la page [création et utilisation d’assemblys](https://msdn.microsoft.com/library/xwb8f617) pour plus d’informations sur la signature d’un assembly.</span><span class="sxs-lookup"><span data-stu-id="af337-119">See [Creating and Using Strong-Named Assemblies](https://msdn.microsoft.com/library/xwb8f617) for more information on signing an assembly.</span></span>  
  
### <a name="to-set-delaysign-in-the-visual-studio-integrated-development-environment"></a><span data-ttu-id="af337-120">Pour définir /delaysign dans Visual Studio environnement de développement intégré</span><span class="sxs-lookup"><span data-stu-id="af337-120">To set /delaysign in the Visual Studio integrated development environment</span></span>  
  
1.  <span data-ttu-id="af337-121">Sélectionnez un projet dans l' **Explorateur de solutions**.</span><span class="sxs-lookup"><span data-stu-id="af337-121">Have a project selected in **Solution Explorer**.</span></span> <span data-ttu-id="af337-122">Sur le **projet** menu, cliquez sur **propriétés**.</span><span class="sxs-lookup"><span data-stu-id="af337-122">On the **Project** menu, click **Properties**.</span></span> <span data-ttu-id="af337-123">Pour plus d’informations, consultez [Introduction au Concepteur de projets](http://msdn.microsoft.com/en-us/898dd854-c98d-430c-ba1b-a913ce3c73d7).</span><span class="sxs-lookup"><span data-stu-id="af337-123">For more information, see [Introduction to the Project Designer](http://msdn.microsoft.com/en-us/898dd854-c98d-430c-ba1b-a913ce3c73d7).</span></span>  
  
2.  <span data-ttu-id="af337-124">Cliquez sur le **signature** onglet.</span><span class="sxs-lookup"><span data-stu-id="af337-124">Click the **Signing** tab.</span></span>  
  
3.  <span data-ttu-id="af337-125">Définissez la valeur de la **temporiser la signature uniquement** boîte.</span><span class="sxs-lookup"><span data-stu-id="af337-125">Set the value in the **Delay sign only** box.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="af337-126">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="af337-126">See Also</span></span>  
 <span data-ttu-id="af337-127">[Compilateur de ligne de commande de Visual Basic](../../../visual-basic/reference/command-line-compiler/index.md) </span><span class="sxs-lookup"><span data-stu-id="af337-127">[Visual Basic Command-Line Compiler](../../../visual-basic/reference/command-line-compiler/index.md) </span></span>  
<span data-ttu-id="af337-128"> [/ keyfile](../../../visual-basic/reference/command-line-compiler/keyfile.md) </span><span class="sxs-lookup"><span data-stu-id="af337-128"> [/keyfile](../../../visual-basic/reference/command-line-compiler/keyfile.md) </span></span>  
<span data-ttu-id="af337-129"> [/ keycontainer](../../../visual-basic/reference/command-line-compiler/keycontainer.md) </span><span class="sxs-lookup"><span data-stu-id="af337-129"> [/keycontainer](../../../visual-basic/reference/command-line-compiler/keycontainer.md) </span></span>  
<span data-ttu-id="af337-130"> [Exemples de lignes de commande de compilation](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)</span><span class="sxs-lookup"><span data-stu-id="af337-130"> [Sample Compilation Command Lines](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)</span></span>
