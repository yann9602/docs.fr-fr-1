---
title: /delaysign
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- delaysign compiler option [Visual Basic]
- /delaysign compiler option [Visual Basic]
- -delaysign compiler option [Visual Basic]
ms.assetid: c76e61a4-1884-4252-9fb2-377f99caa690
caps.latest.revision: "19"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 6c42e351808281d90eafdb6e61a3f1736ef15c9d
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="delaysign"></a><span data-ttu-id="5e7df-102">/delaysign</span><span class="sxs-lookup"><span data-stu-id="5e7df-102">/delaysign</span></span>
<span data-ttu-id="5e7df-103">Spécifie si l'assembly sera complètement ou partiellement signé.</span><span class="sxs-lookup"><span data-stu-id="5e7df-103">Specifies whether the assembly will be fully or partially signed.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5e7df-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="5e7df-104">Syntax</span></span>  
  
```  
/delaysign[+ | -]  
```  
  
## <a name="arguments"></a><span data-ttu-id="5e7df-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="5e7df-105">Arguments</span></span>  
 <span data-ttu-id="5e7df-106">`+` &#124; `-`</span><span class="sxs-lookup"><span data-stu-id="5e7df-106">`+` &#124; `-`</span></span>  
 <span data-ttu-id="5e7df-107">Facultatif.</span><span class="sxs-lookup"><span data-stu-id="5e7df-107">Optional.</span></span> <span data-ttu-id="5e7df-108">Utilisez `/delaysign-` si vous souhaitez obtenir un assembly complètement signé.</span><span class="sxs-lookup"><span data-stu-id="5e7df-108">Use `/delaysign-` if you want a fully signed assembly.</span></span> <span data-ttu-id="5e7df-109">Utilisez `/delaysign+` si vous souhaitez placer la clé publique dans l’espace d’assembly et réservez pour le hachage signé.</span><span class="sxs-lookup"><span data-stu-id="5e7df-109">Use `/delaysign+` if you want to place the public key in the assembly and reserve space for the signed hash.</span></span> <span data-ttu-id="5e7df-110">La valeur par défaut est `/delaysign-`.</span><span class="sxs-lookup"><span data-stu-id="5e7df-110">The default is `/delaysign-`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="5e7df-111">Remarques</span><span class="sxs-lookup"><span data-stu-id="5e7df-111">Remarks</span></span>  
 <span data-ttu-id="5e7df-112">Le `/delaysign` option est sans effet sauf si utilisée avec [/keyfile](../../../visual-basic/reference/command-line-compiler/keyfile.md) ou [/keycontainer](../../../visual-basic/reference/command-line-compiler/keycontainer.md).</span><span class="sxs-lookup"><span data-stu-id="5e7df-112">The `/delaysign` option has no effect unless used with [/keyfile](../../../visual-basic/reference/command-line-compiler/keyfile.md) or [/keycontainer](../../../visual-basic/reference/command-line-compiler/keycontainer.md).</span></span>  
  
 <span data-ttu-id="5e7df-113">Quand vous demandez un assembly totalement signé, le compilateur hache le fichier qui contient le manifeste (métadonnées de l’assembly) et signe ce hachage avec la clé privée.</span><span class="sxs-lookup"><span data-stu-id="5e7df-113">When you request a fully signed assembly, the compiler hashes the file that contains the manifest (assembly metadata) and signs that hash with the private key.</span></span> <span data-ttu-id="5e7df-114">La signature numérique obtenue est stockée dans le fichier qui contient le manifeste.</span><span class="sxs-lookup"><span data-stu-id="5e7df-114">The resulting digital signature is stored in the file that contains the manifest.</span></span> <span data-ttu-id="5e7df-115">Lorsqu’un assembly est à signature différée, le compilateur ne calcule pas et stocke l’espace de la signature, mais les réserves de ressources dans le fichier afin de pouvoir ajouter ultérieurement la signature.</span><span class="sxs-lookup"><span data-stu-id="5e7df-115">When an assembly is delay signed, the compiler does not compute and store the signature but reserves space in the file so the signature can be added later.</span></span>  
  
 <span data-ttu-id="5e7df-116">Par exemple, à l’aide de `/delaysign+`, un développeur d’une organisation peut distribuer des versions de test non signé d’un assembly qui les testeurs peuvent enregistrer dans le global assembly cache et utiliser.</span><span class="sxs-lookup"><span data-stu-id="5e7df-116">For example, by using `/delaysign+`, a developer in an organization can distribute unsigned test versions of an assembly that testers can register with the global assembly cache and use.</span></span> <span data-ttu-id="5e7df-117">Lorsque le travail sur l’assembly est terminé, la personne responsable de la clé privée de l’organisation peut signer complètement l’assembly.</span><span class="sxs-lookup"><span data-stu-id="5e7df-117">When work on the assembly is completed, the person responsible for the organization's private key can fully sign the assembly.</span></span> <span data-ttu-id="5e7df-118">Ce compartimentage protège la clé privée de l’organisation à partir de la publication, tout en permettant à tous les développeurs de travailler sur les assemblys.</span><span class="sxs-lookup"><span data-stu-id="5e7df-118">This compartmentalization protects the organization's private key from disclosure, while allowing all developers to work on the assemblies.</span></span>  
  
 <span data-ttu-id="5e7df-119">Consultez [création et assemblys avec nom fort](https://msdn.microsoft.com/library/xwb8f617) pour plus d’informations sur la signature d’un assembly.</span><span class="sxs-lookup"><span data-stu-id="5e7df-119">See [Creating and Using Strong-Named Assemblies](https://msdn.microsoft.com/library/xwb8f617) for more information on signing an assembly.</span></span>  
  
### <a name="to-set-delaysign-in-the-visual-studio-integrated-development-environment"></a><span data-ttu-id="5e7df-120">Pour définir /delaysign dans Visual Studio environnement de développement intégré</span><span class="sxs-lookup"><span data-stu-id="5e7df-120">To set /delaysign in the Visual Studio integrated development environment</span></span>  
  
1.  <span data-ttu-id="5e7df-121">Sélectionnez un projet dans l' **Explorateur de solutions**.</span><span class="sxs-lookup"><span data-stu-id="5e7df-121">Have a project selected in **Solution Explorer**.</span></span> <span data-ttu-id="5e7df-122">Dans le menu **Projet**, cliquez sur **Propriétés**.</span><span class="sxs-lookup"><span data-stu-id="5e7df-122">On the **Project** menu, click **Properties**.</span></span> <span data-ttu-id="5e7df-123">Pour plus d’informations, consultez [Introduction au Concepteur de projets](http://msdn.microsoft.com/en-us/898dd854-c98d-430c-ba1b-a913ce3c73d7).</span><span class="sxs-lookup"><span data-stu-id="5e7df-123">For more information, see [Introduction to the Project Designer](http://msdn.microsoft.com/en-us/898dd854-c98d-430c-ba1b-a913ce3c73d7).</span></span>  
  
2.  <span data-ttu-id="5e7df-124">Cliquez sur l’onglet **Signature**.</span><span class="sxs-lookup"><span data-stu-id="5e7df-124">Click the **Signing** tab.</span></span>  
  
3.  <span data-ttu-id="5e7df-125">Définissez la valeur de la **temporiser la signature uniquement** boîte.</span><span class="sxs-lookup"><span data-stu-id="5e7df-125">Set the value in the **Delay sign only** box.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5e7df-126">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="5e7df-126">See Also</span></span>  
 [<span data-ttu-id="5e7df-127">Compilateur de ligne de commande de Visual Basic</span><span class="sxs-lookup"><span data-stu-id="5e7df-127">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)  
 [<span data-ttu-id="5e7df-128">/keyfile</span><span class="sxs-lookup"><span data-stu-id="5e7df-128">/keyfile</span></span>](../../../visual-basic/reference/command-line-compiler/keyfile.md)  
 [<span data-ttu-id="5e7df-129">/keycontainer</span><span class="sxs-lookup"><span data-stu-id="5e7df-129">/keycontainer</span></span>](../../../visual-basic/reference/command-line-compiler/keycontainer.md)  
 [<span data-ttu-id="5e7df-130">Exemples de lignes de commande de compilation</span><span class="sxs-lookup"><span data-stu-id="5e7df-130">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
