---
title: /subsystemversion (Visual Basic) | Documents Microsoft
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- /subsystemversion compiler option [Visual Basic]
- -subsystemversion compiler option [Visual Basic]
- subsystemversion compiler option [Visual Basic]
ms.assetid: 08be22b2-f447-4cd3-8203-120b1b920b54
caps.latest.revision: 9
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
ms.openlocfilehash: efeade3fcde18f02b3a760adc50d3555df6c9ed7
ms.contentlocale: fr-fr
ms.lasthandoff: 04/12/2017

---
# <a name="subsystemversion-visual-basic"></a><span data-ttu-id="dbc19-102">/subsystemversion (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="dbc19-102">/subsystemversion (Visual Basic)</span></span>
<span data-ttu-id="dbc19-103">Spécifie la version minimale du sous-système sur lequel le fichier exécutable généré peut s’exécuter, en déterminant les versions de Windows sur lequel le fichier exécutable peut s’exécuter.</span><span class="sxs-lookup"><span data-stu-id="dbc19-103">Specifies the minimum version of the subsystem on which the generated executable file can run, thereby determining the versions of Windows on which the executable file can run.</span></span> <span data-ttu-id="dbc19-104">En règle générale, cette option garantit que le fichier exécutable peut tirer parti des fonctionnalités de sécurité qui ne sont pas disponibles avec les versions antérieures de Windows.</span><span class="sxs-lookup"><span data-stu-id="dbc19-104">Most commonly, this option ensures that the executable file can leverage particular security features that aren’t available with older versions of Windows.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="dbc19-105">Pour spécifier le sous-système lui-même, utilisez la [/target](../../../csharp/language-reference/compiler-options/target-compiler-option.md) option du compilateur.</span><span class="sxs-lookup"><span data-stu-id="dbc19-105">To specify the subsystem itself, use the [/target](../../../csharp/language-reference/compiler-options/target-compiler-option.md) compiler option.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dbc19-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="dbc19-106">Syntax</span></span>  
  
```vb  
/subsystemversion:major.minor  
```  
  
#### <a name="parameters"></a><span data-ttu-id="dbc19-107">Paramètres</span><span class="sxs-lookup"><span data-stu-id="dbc19-107">Parameters</span></span>  
 `major.minor`  
 <span data-ttu-id="dbc19-108">La version minimale requise du sous-système, comme cela est exprimé dans une notation par points pour les versions majeures et mineures.</span><span class="sxs-lookup"><span data-stu-id="dbc19-108">The minimum required version of the subsystem, as expressed in a dot notation for major and minor versions.</span></span> <span data-ttu-id="dbc19-109">Par exemple, vous pouvez spécifier qu’une application ne peut pas s’exécuter sur un système d’exploitation qui est antérieure à Windows 7 si vous définissez la valeur de cette option sur 6.01, comme décrit dans le tableau plus loin dans cette rubrique.</span><span class="sxs-lookup"><span data-stu-id="dbc19-109">For example, you can specify that an application can't run on an operating system that's older than Windows 7 if you set the value of this option to 6.01, as the table later in this topic describes.</span></span> <span data-ttu-id="dbc19-110">Vous devez spécifier les valeurs de `major` et `minor` en tant qu’entiers.</span><span class="sxs-lookup"><span data-stu-id="dbc19-110">You must specify the values for `major` and `minor` as integers.</span></span>  
  
 <span data-ttu-id="dbc19-111">Zéros de début le `minor` version ne modifiez pas la version, mais que faire de zéros de fin.</span><span class="sxs-lookup"><span data-stu-id="dbc19-111">Leading zeroes in the `minor` version don't change the version, but trailing zeroes do.</span></span> <span data-ttu-id="dbc19-112">Par exemple, 6.1 et 6.01 font référence à la même version, mais 6.10 fait référence à une version différente.</span><span class="sxs-lookup"><span data-stu-id="dbc19-112">For example, 6.1 and 6.01 refer to the same version, but 6.10 refers to a different version.</span></span> <span data-ttu-id="dbc19-113">Nous vous recommandons d’exprimer la version secondaire à deux chiffres pour éviter toute confusion.</span><span class="sxs-lookup"><span data-stu-id="dbc19-113">We recommend expressing the minor version as two digits to avoid confusion.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="dbc19-114">Notes</span><span class="sxs-lookup"><span data-stu-id="dbc19-114">Remarks</span></span>  
 <span data-ttu-id="dbc19-115">Le tableau suivant répertorie les versions de sous-système commun de Windows.</span><span class="sxs-lookup"><span data-stu-id="dbc19-115">The following table lists common subsystem versions of Windows.</span></span>  
  
|<span data-ttu-id="dbc19-116">Version Windows</span><span class="sxs-lookup"><span data-stu-id="dbc19-116">Windows version</span></span>|<span data-ttu-id="dbc19-117">Version du sous-système</span><span class="sxs-lookup"><span data-stu-id="dbc19-117">Subsystem version</span></span>|  
|---------------------|-----------------------|  
|<span data-ttu-id="dbc19-118">Windows 2000</span><span class="sxs-lookup"><span data-stu-id="dbc19-118">Windows 2000</span></span>|<span data-ttu-id="dbc19-119">5.00</span><span class="sxs-lookup"><span data-stu-id="dbc19-119">5.00</span></span>|  
|<span data-ttu-id="dbc19-120">Windows XP</span><span class="sxs-lookup"><span data-stu-id="dbc19-120">Windows XP</span></span>|<span data-ttu-id="dbc19-121">5.01</span><span class="sxs-lookup"><span data-stu-id="dbc19-121">5.01</span></span>|  
|<span data-ttu-id="dbc19-122">Windows Server 2003</span><span class="sxs-lookup"><span data-stu-id="dbc19-122">Windows Server 2003</span></span>|<span data-ttu-id="dbc19-123">5.02</span><span class="sxs-lookup"><span data-stu-id="dbc19-123">5.02</span></span>|  
|<span data-ttu-id="dbc19-124">Windows Vista</span><span class="sxs-lookup"><span data-stu-id="dbc19-124">Windows Vista</span></span>|<span data-ttu-id="dbc19-125">6.00</span><span class="sxs-lookup"><span data-stu-id="dbc19-125">6.00</span></span>|  
|<span data-ttu-id="dbc19-126">Windows 7</span><span class="sxs-lookup"><span data-stu-id="dbc19-126">Windows 7</span></span>|<span data-ttu-id="dbc19-127">6.01</span><span class="sxs-lookup"><span data-stu-id="dbc19-127">6.01</span></span>|  
|<span data-ttu-id="dbc19-128">Windows Server 2008</span><span class="sxs-lookup"><span data-stu-id="dbc19-128">Windows Server 2008</span></span>|<span data-ttu-id="dbc19-129">6.01</span><span class="sxs-lookup"><span data-stu-id="dbc19-129">6.01</span></span>|  
|[!INCLUDE[win8](../../../csharp/language-reference/compiler-options/includes/win8_md.md)]|<span data-ttu-id="dbc19-130">6.02</span><span class="sxs-lookup"><span data-stu-id="dbc19-130">6.02</span></span>|  
  
## <a name="default-values"></a><span data-ttu-id="dbc19-131">Valeurs par défaut</span><span class="sxs-lookup"><span data-stu-id="dbc19-131">Default values</span></span>  
 <span data-ttu-id="dbc19-132">La valeur par défaut de la **/subsystemversion** option du compilateur dépend des conditions dans la liste suivante :</span><span class="sxs-lookup"><span data-stu-id="dbc19-132">The default value of the **/subsystemversion** compiler option depends on the conditions in the following list:</span></span>  
  
-   <span data-ttu-id="dbc19-133">La valeur par défaut est 6.02 si toutes les options du compilateur dans la liste suivante sont définie :</span><span class="sxs-lookup"><span data-stu-id="dbc19-133">The default value is 6.02 if any compiler option in the following list is set:</span></span>  
  
    -   [<span data-ttu-id="dbc19-134">/ target : appcontainerexe</span><span class="sxs-lookup"><span data-stu-id="dbc19-134">/target:appcontainerexe</span></span>](../../../visual-basic/reference/command-line-compiler/target.md)  
  
    -   [<span data-ttu-id="dbc19-135">/ target : winmdobj</span><span class="sxs-lookup"><span data-stu-id="dbc19-135">/target:winmdobj</span></span>](../../../visual-basic/reference/command-line-compiler/target.md)  
  
    -   [<span data-ttu-id="dbc19-136">/Platform:ARM</span><span class="sxs-lookup"><span data-stu-id="dbc19-136">/platform:arm</span></span>](../../../visual-basic/reference/command-line-compiler/platform.md)  
  
-   <span data-ttu-id="dbc19-137">La valeur par défaut est 6,00 si vous utilisez MSBuild, vous ciblez [!INCLUDE[net_v45](../../../csharp/language-reference/compiler-options/includes/net_v45_md.md)], et vous n’avez pas défini les options du compilateur qui ont été spécifiées plus haut dans cette liste.</span><span class="sxs-lookup"><span data-stu-id="dbc19-137">The default value is 6.00 if you're using MSBuild, you're targeting [!INCLUDE[net_v45](../../../csharp/language-reference/compiler-options/includes/net_v45_md.md)], and you haven't set any of the compiler options that were specified earlier in this list.</span></span>  
  
-   <span data-ttu-id="dbc19-138">La valeur par défaut est 4.00 si aucune des conditions précédentes est true.</span><span class="sxs-lookup"><span data-stu-id="dbc19-138">The default value is 4.00 if none of the previous conditions is true.</span></span>  
  
## <a name="setting-this-option"></a><span data-ttu-id="dbc19-139">Définition de cette option</span><span class="sxs-lookup"><span data-stu-id="dbc19-139">Setting this option</span></span>  
 <span data-ttu-id="dbc19-140">Pour définir le **/subsystemversion** option du compilateur dans Visual Studio, vous devez ouvrir le fichier .vbproj et spécifiez une valeur pour le `SubsystemVersion` propriété dans le XML de MSBuild.</span><span class="sxs-lookup"><span data-stu-id="dbc19-140">To set the **/subsystemversion** compiler option in Visual Studio, you must open the .vbproj file and specify a value for the `SubsystemVersion` property in the MSBuild XML.</span></span> <span data-ttu-id="dbc19-141">Vous ne pouvez pas définir cette option dans l’IDE de Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="dbc19-141">You can't set this option in the Visual Studio IDE.</span></span> <span data-ttu-id="dbc19-142">Pour plus d’informations, consultez « Valeurs par défaut » plus haut dans cette rubrique ou [propriétés communes des projets MSBuild](https://docs.microsoft.com/visualstudio/msbuild/common-msbuild-project-properties).</span><span class="sxs-lookup"><span data-stu-id="dbc19-142">For more information, see "Default values" earlier in this topic or [Common MSBuild Project Properties](https://docs.microsoft.com/visualstudio/msbuild/common-msbuild-project-properties).</span></span>  
  

  
## <a name="see-also"></a><span data-ttu-id="dbc19-143">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="dbc19-143">See Also</span></span>  
[<span data-ttu-id="dbc19-144">Compilateur de ligne de commande de Visual Basic</span><span class="sxs-lookup"><span data-stu-id="dbc19-144">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)

[<span data-ttu-id="dbc19-145">Propriétés MSBuild</span><span class="sxs-lookup"><span data-stu-id="dbc19-145">MSBuild Properties</span></span>](https://docs.microsoft.com/visualstudio/msbuild/msbuild-properties)

