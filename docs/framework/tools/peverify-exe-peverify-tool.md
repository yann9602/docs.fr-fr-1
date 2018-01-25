---
title: Peverify.exe (outil PEVerify)
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- portable executable files, PEVerify
- verifying MSIL and metadata
- PEVerify tool
- type safety requirements
- MSIL
- PEverify.exe
- PE files, PEVerify
ms.assetid: f4f46f9e-8d08-4e66-a94b-0c69c9b0bbfa
caps.latest.revision: "18"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 5acb6da7c68f899daa4144e897e9ec31fcfa868a
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/19/2018
---
# <a name="peverifyexe-peverify-tool"></a><span data-ttu-id="c1f29-102">Peverify.exe (outil PEVerify)</span><span class="sxs-lookup"><span data-stu-id="c1f29-102">Peverify.exe (PEVerify Tool)</span></span>
<span data-ttu-id="c1f29-103">L’outil PEVerify Tool permet aux développeurs générant du langage MSIL (Microsoft Intermediate Language) (tels que des développeurs de moteurs de script, writers de compilateur, etc.) de déterminer si leur code MSIL et les métadonnées qui y sont associées répondent aux exigences de sécurité de type.</span><span class="sxs-lookup"><span data-stu-id="c1f29-103">The PEVerify tool helps developers who generate Microsoft intermediate language (MSIL) (such as compiler writers, script engine developers, and so on) to determine whether their MSIL code and associated metadata meet type safety requirements.</span></span> <span data-ttu-id="c1f29-104">Certains compilateurs génèrent du code de type sécurisé vérifié uniquement si vous évitez d'utiliser certaines constructions de langage.</span><span class="sxs-lookup"><span data-stu-id="c1f29-104">Some compilers generate verifiably type-safe code only if you avoid using certain language constructs.</span></span> <span data-ttu-id="c1f29-105">Si, en tant que développeur, vous utilisez ce type de compilateur, vous pouvez souhaiter vérifier que vous n'avez pas compromis la sécurité de type de votre code.</span><span class="sxs-lookup"><span data-stu-id="c1f29-105">If, as a developer, you are using such a compiler, you may want to verify that you have not compromised the type safety of your code.</span></span> <span data-ttu-id="c1f29-106">Vous pouvez dans ce cas exécuter l'outil PEVerify Tool sur vos fichiers pour vérifier le langage MSIL et les métadonnées.</span><span class="sxs-lookup"><span data-stu-id="c1f29-106">In this situation, you can run the PEVerify tool on your files to check the MSIL and metadata.</span></span>  
  
 <span data-ttu-id="c1f29-107">Cet outil est installé automatiquement avec Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="c1f29-107">This tool is automatically installed with Visual Studio.</span></span> <span data-ttu-id="c1f29-108">Pour exécuter l'outil, utilisez l'invite de commandes développeur (ou l'invite de commandes Visual Studio dans Windows 7).</span><span class="sxs-lookup"><span data-stu-id="c1f29-108">To run the tool, use the Developer Command Prompt (or the Visual Studio Command Prompt in Windows 7).</span></span> <span data-ttu-id="c1f29-109">Pour plus d'informations, consultez [Invites de commandes](../../../docs/framework/tools/developer-command-prompt-for-vs.md).</span><span class="sxs-lookup"><span data-stu-id="c1f29-109">For more information, see [Command Prompts](../../../docs/framework/tools/developer-command-prompt-for-vs.md).</span></span>  
  
 <span data-ttu-id="c1f29-110">À l'invite de commandes, tapez le texte suivant :</span><span class="sxs-lookup"><span data-stu-id="c1f29-110">At the command prompt, type the following:</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c1f29-111">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c1f29-111">Syntax</span></span>  
  
```  
peverify filename [options]  
```  
  
#### <a name="parameters"></a><span data-ttu-id="c1f29-112">Paramètres</span><span class="sxs-lookup"><span data-stu-id="c1f29-112">Parameters</span></span>  
  
|<span data-ttu-id="c1f29-113">Argument</span><span class="sxs-lookup"><span data-stu-id="c1f29-113">Argument</span></span>|<span data-ttu-id="c1f29-114">Description</span><span class="sxs-lookup"><span data-stu-id="c1f29-114">Description</span></span>|  
|--------------|-----------------|  
|<span data-ttu-id="c1f29-115">*filename*</span><span class="sxs-lookup"><span data-stu-id="c1f29-115">*filename*</span></span>|<span data-ttu-id="c1f29-116">Fichier exécutable portable dont le langage MSIL et les métadonnées sont à vérifier.</span><span class="sxs-lookup"><span data-stu-id="c1f29-116">The portable executable (PE) file for which to check the MSIL and metadata.</span></span>|  
  
|<span data-ttu-id="c1f29-117">Option</span><span class="sxs-lookup"><span data-stu-id="c1f29-117">Option</span></span>|<span data-ttu-id="c1f29-118">Description</span><span class="sxs-lookup"><span data-stu-id="c1f29-118">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="c1f29-119">**/break=** *maxErrorCount*</span><span class="sxs-lookup"><span data-stu-id="c1f29-119">**/break=** *maxErrorCount*</span></span>|<span data-ttu-id="c1f29-120">Abandonne la vérification si le nombre d’erreurs atteint *maxErrorCount* erreurs.</span><span class="sxs-lookup"><span data-stu-id="c1f29-120">Aborts verification after *maxErrorCount* errors.</span></span><br /><br /> <span data-ttu-id="c1f29-121">Ce paramètre n'est pas pris en charge dans les versions 2.0 et ultérieures du .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="c1f29-121">This parameter is not supported in .NET Framework version 2.0 or later.</span></span>|  
|<span data-ttu-id="c1f29-122">**/clock**</span><span class="sxs-lookup"><span data-stu-id="c1f29-122">**/clock**</span></span>|<span data-ttu-id="c1f29-123">Calcule et indique la durée des vérifications suivantes, en millisecondes :</span><span class="sxs-lookup"><span data-stu-id="c1f29-123">Measures and reports the following verification times in milliseconds:</span></span><br /><br /> <span data-ttu-id="c1f29-124">**MD Val. cycle**</span><span class="sxs-lookup"><span data-stu-id="c1f29-124">**MD Val. cycle**</span></span><br /> <span data-ttu-id="c1f29-125">Cycle de validation des métadonnées</span><span class="sxs-lookup"><span data-stu-id="c1f29-125">Metadata validation cycle</span></span><br /><br /> <span data-ttu-id="c1f29-126">**MD Val. pure**</span><span class="sxs-lookup"><span data-stu-id="c1f29-126">**MD Val. pure**</span></span><br /> <span data-ttu-id="c1f29-127">Validation simple des métadonnées</span><span class="sxs-lookup"><span data-stu-id="c1f29-127">Metadata validation pure</span></span><br /><br /> <span data-ttu-id="c1f29-128">**IL Ver. cycle**</span><span class="sxs-lookup"><span data-stu-id="c1f29-128">**IL Ver. cycle**</span></span><br /> <span data-ttu-id="c1f29-129">Cycle de vérification MSIL</span><span class="sxs-lookup"><span data-stu-id="c1f29-129">Microsoft intermediate language (MSIL) verification cycle</span></span><br /><br /> <span data-ttu-id="c1f29-130">**IL Ver pure**</span><span class="sxs-lookup"><span data-stu-id="c1f29-130">**IL Ver pure**</span></span><br /> <span data-ttu-id="c1f29-131">Vérification MSIL simple</span><span class="sxs-lookup"><span data-stu-id="c1f29-131">MSIL verification pure</span></span><br /><br /> <span data-ttu-id="c1f29-132">Les temps **MD Val. cycle** et **IL Ver. cycle** incluent le temps qu’il faut pour effectuer les procédures de démarrage et d’arrêt nécessaires.</span><span class="sxs-lookup"><span data-stu-id="c1f29-132">The **MD Val. cycle** and **IL Ver. cycle** times include the time required to perform necessary startup and shutdown procedures.</span></span> <span data-ttu-id="c1f29-133">Les temps **MD Val. pure** et **IL Ver pure** reflètent le temps qu’il faut pour effectuer la validation ou la vérification uniquement.</span><span class="sxs-lookup"><span data-stu-id="c1f29-133">The **MD Val. pure** and **IL Ver pure** times reflect the time required to perform the validation or verification only.</span></span>|  
|<span data-ttu-id="c1f29-134">**/help**</span><span class="sxs-lookup"><span data-stu-id="c1f29-134">**/help**</span></span>|<span data-ttu-id="c1f29-135">Affiche la syntaxe et les options de commande de l'outil.</span><span class="sxs-lookup"><span data-stu-id="c1f29-135">Displays command syntax and options for the tool.</span></span>|  
|<span data-ttu-id="c1f29-136">**/hresult**</span><span class="sxs-lookup"><span data-stu-id="c1f29-136">**/hresult**</span></span>|<span data-ttu-id="c1f29-137">Affiche les codes d'erreur au format hexadécimal.</span><span class="sxs-lookup"><span data-stu-id="c1f29-137">Displays error codes in hexadecimal format.</span></span>|  
|<span data-ttu-id="c1f29-138">**/ignore=** *hex.code* [, *hex.code*]</span><span class="sxs-lookup"><span data-stu-id="c1f29-138">**/ignore=** *hex.code* [, *hex.code*]</span></span>|<span data-ttu-id="c1f29-139">Ignore les codes d'erreur spécifiés.</span><span class="sxs-lookup"><span data-stu-id="c1f29-139">Ignores the specified error codes.</span></span>|  
|<span data-ttu-id="c1f29-140">**/ignore=@** *responseFile*</span><span class="sxs-lookup"><span data-stu-id="c1f29-140">**/ignore=@** *responseFile*</span></span>|<span data-ttu-id="c1f29-141">Ignore les codes d'erreur répertoriés dans le fichier réponse spécifié.</span><span class="sxs-lookup"><span data-stu-id="c1f29-141">Ignores the error codes listed in the specified response file.</span></span>|  
|<span data-ttu-id="c1f29-142">**/il**</span><span class="sxs-lookup"><span data-stu-id="c1f29-142">**/il**</span></span>|<span data-ttu-id="c1f29-143">Procède aux contrôles de vérification de la sécurité de type MSIL pour les méthodes implémentées dans l’assembly spécifié par *filename*.</span><span class="sxs-lookup"><span data-stu-id="c1f29-143">Performs MSIL type safety verification checks for methods implemented in the assembly specified by *filename*.</span></span> <span data-ttu-id="c1f29-144">L’outil retourne les descriptions détaillées de chaque problème rencontré, sauf si vous spécifiez l’option **/quiet**.</span><span class="sxs-lookup"><span data-stu-id="c1f29-144">The tool returns detailed descriptions for each problem found unless you specify the **/quiet** option.</span></span>|  
|<span data-ttu-id="c1f29-145">**/md**</span><span class="sxs-lookup"><span data-stu-id="c1f29-145">**/md**</span></span>|<span data-ttu-id="c1f29-146">Procède aux contrôles de validation des métadonnées sur l’assembly spécifié par *filename*.</span><span class="sxs-lookup"><span data-stu-id="c1f29-146">Performs metadata validation checks on the assembly specified by *filename*.</span></span> <span data-ttu-id="c1f29-147">Parcourt l’intégralité de la structure des métadonnées figurant dans le fichier et fait état de tous les problèmes de validation rencontrés.</span><span class="sxs-lookup"><span data-stu-id="c1f29-147">This walks the full metadata structure within the file and reports all validation problems encountered.</span></span>|  
|<span data-ttu-id="c1f29-148">**/nologo**</span><span class="sxs-lookup"><span data-stu-id="c1f29-148">**/nologo**</span></span>|<span data-ttu-id="c1f29-149">Supprime l'affichage de version de produit et d'informations de copyright.</span><span class="sxs-lookup"><span data-stu-id="c1f29-149">Suppresses the display of product version and copyright information.</span></span>|  
|<span data-ttu-id="c1f29-150">**/nosymbols**</span><span class="sxs-lookup"><span data-stu-id="c1f29-150">**/nosymbols**</span></span>|<span data-ttu-id="c1f29-151">Dans le .NET Framework version 2.0, il supprime les numéros de ligne pour la compatibilité descendante.</span><span class="sxs-lookup"><span data-stu-id="c1f29-151">In the .NET Framework version 2.0, suppresses line numbers for backward compatibility.</span></span>|  
|<span data-ttu-id="c1f29-152">**/quiet**</span><span class="sxs-lookup"><span data-stu-id="c1f29-152">**/quiet**</span></span>|<span data-ttu-id="c1f29-153">Spécifie le mode silencieux ; supprime la sortie des états sur les problèmes de vérification.</span><span class="sxs-lookup"><span data-stu-id="c1f29-153">Specifies quiet mode; suppresses output of the verification problem reports.</span></span> <span data-ttu-id="c1f29-154">Peverify.exe continue à indiquer si le fichier est de type sécurisé, mais ne fait pas état d'informations sur les problèmes empêchant la vérification de la sécurité de type.</span><span class="sxs-lookup"><span data-stu-id="c1f29-154">Peverify.exe still reports whether the file is type safe, but does not report information on problems preventing type safety verification.</span></span>|  
|`/transparent`|<span data-ttu-id="c1f29-155">Vérifiez uniquement les méthodes transparentes.</span><span class="sxs-lookup"><span data-stu-id="c1f29-155">Verify only the transparent methods.</span></span>|  
|<span data-ttu-id="c1f29-156">**/unique**</span><span class="sxs-lookup"><span data-stu-id="c1f29-156">**/unique**</span></span>|<span data-ttu-id="c1f29-157">Ignore les codes d'erreur récurrents.</span><span class="sxs-lookup"><span data-stu-id="c1f29-157">Ignores repeating error codes.</span></span>|  
|<span data-ttu-id="c1f29-158">**/verbose**</span><span class="sxs-lookup"><span data-stu-id="c1f29-158">**/verbose**</span></span>|<span data-ttu-id="c1f29-159">Dans le .NET Framework version 2.0, il affiche des informations supplémentaires dans les messages de vérification MSIL.</span><span class="sxs-lookup"><span data-stu-id="c1f29-159">In the .NET Framework version 2.0, displays additional information in MSIL verification messages.</span></span>|  
|<span data-ttu-id="c1f29-160">**/?**</span><span class="sxs-lookup"><span data-stu-id="c1f29-160">**/?**</span></span>|<span data-ttu-id="c1f29-161">Affiche la syntaxe et les options de commande de l'outil.</span><span class="sxs-lookup"><span data-stu-id="c1f29-161">Displays command syntax and options for the tool.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c1f29-162">Notes</span><span class="sxs-lookup"><span data-stu-id="c1f29-162">Remarks</span></span>  
 <span data-ttu-id="c1f29-163">Le Common Language Runtime repose sur l'exécution de type sécurisé du code de l'application pour permettre de mettre en œuvre des mécanismes de sécurité et d'isolation.</span><span class="sxs-lookup"><span data-stu-id="c1f29-163">The common language runtime relies on the type-safe execution of application code to help enforce security and isolation mechanisms.</span></span> <span data-ttu-id="c1f29-164">Le code qui n’est pas de [type sécurisé vérifié](http://msdn.microsoft.com/library/095cd1f6-d8db-4c0e-bce2-83ccb34dd5dc) ne peut normalement pas être exécuté, même si vous pouvez définir une stratégie de sécurité permettant l’exécution d’un code de confiance, mais non vérifiable.</span><span class="sxs-lookup"><span data-stu-id="c1f29-164">Normally, code that is not [verifiably type safe](http://msdn.microsoft.com/library/095cd1f6-d8db-4c0e-bce2-83ccb34dd5dc) cannot run, although you can set security policy to allow the execution of trusted but unverifiable code.</span></span>  
  
 <span data-ttu-id="c1f29-165">Si ni l’option **/md** ni l’option **/il** ne sont spécifiées, Peverify.exe effectue ces deux types de contrôles.</span><span class="sxs-lookup"><span data-stu-id="c1f29-165">If neither the **/md** nor **/il** options are specified, Peverify.exe performs both types of checks.</span></span> <span data-ttu-id="c1f29-166">Peverify.exe procède en premier lieu aux contrôles **/md**.</span><span class="sxs-lookup"><span data-stu-id="c1f29-166">Peverify.exe performs **/md** checks first.</span></span> <span data-ttu-id="c1f29-167">En l’absence d’erreurs, il effectue ensuite les contrôles **/il**.</span><span class="sxs-lookup"><span data-stu-id="c1f29-167">If there are no errors, **/il** checks are made.</span></span> <span data-ttu-id="c1f29-168">Si vous spécifiez à la fois les contrôles **/md** et **/il**, les contrôles **/il** sont effectués, y compris en cas d’erreurs dans les métadonnées.</span><span class="sxs-lookup"><span data-stu-id="c1f29-168">If you specify both **/md** and **/il**, **/il** checks are made even if there are errors in the metadata.</span></span> <span data-ttu-id="c1f29-169">En l’absence d’erreurs dans les métadonnées, **peverify** *filename* équivaut alors à **peverify** *filename* **/md** **/il**.</span><span class="sxs-lookup"><span data-stu-id="c1f29-169">Thus, if there are no metadata errors, **peverify** *filename* is equivalent to **peverify** *filename* **/md** **/il**.</span></span>  
  
 <span data-ttu-id="c1f29-170">Peverify.exe effectue des contrôles de vérification MSIL complets en fonction de l'analyse des flux de données et d'une liste de plusieurs centaines de règles sur la validité des métadonnées.</span><span class="sxs-lookup"><span data-stu-id="c1f29-170">Peverify.exe performs comprehensive MSIL verification checks based on dataflow analysis plus a list of several hundred rules on valid metadata.</span></span> <span data-ttu-id="c1f29-171">Pour plus d'informations sur les contrôles effectués par Peverify.exe, consultez « Metadata Validation Specification » et « MSIL Instruction Set Specification » dans le dossier « Tool Developer's Guide » du [!INCLUDE[winsdklong](../../../includes/winsdklong-md.md)].</span><span class="sxs-lookup"><span data-stu-id="c1f29-171">For detailed information on the checks Peverify.exe performs, see the "Metadata Validation Specification" and the "MSIL Instruction Set Specification" in the Tools Developers Guide folder in the [!INCLUDE[winsdklong](../../../includes/winsdklong-md.md)].</span></span>  
  
 <span data-ttu-id="c1f29-172">Notez que le .NET Framework version 2.0 ou ultérieure prend en charge les valeurs de retour `byref` vérifiables spécifiées à l'aide des instructions MSIL suivantes : `dup`, `ldsflda`, `ldflda`, `ldelema`, `call` et `unbox`.</span><span class="sxs-lookup"><span data-stu-id="c1f29-172">Note that the .NET Framework version 2.0 or later supports verifiable `byref` returns specified using the following MSIL instructions: `dup`, `ldsflda`, `ldflda`, `ldelema`, `call` and `unbox`.</span></span>  
  
## <a name="examples"></a><span data-ttu-id="c1f29-173">Exemples</span><span class="sxs-lookup"><span data-stu-id="c1f29-173">Examples</span></span>  
 <span data-ttu-id="c1f29-174">La commande suivante procède aux contrôles de validation des métadonnées et aux contrôles de vérification de la sécurité de type MSIL pour les méthodes implémentées dans l'assembly `myAssembly.exe`.</span><span class="sxs-lookup"><span data-stu-id="c1f29-174">The following command performs metadata validation checks and MSIL type safety verification checks for methods implemented in the assembly `myAssembly.exe`.</span></span>  
  
```  
peverify myAssembly.exe /md /il  
```  
  
 <span data-ttu-id="c1f29-175">Une fois les contrôles ci‑dessus terminés, Peverify.exe affiche le message suivant.</span><span class="sxs-lookup"><span data-stu-id="c1f29-175">Upon successful completion of the above request, Peverify.exe displays the following message.</span></span>  
  
```  
All classes and methods in myAssembly.exe Verified  
```  
  
 <span data-ttu-id="c1f29-176">La commande suivante procède aux contrôles de validation des métadonnées et aux contrôles de vérification de la sécurité de type MSIL pour les méthodes implémentées dans l'assembly `myAssembly.exe`.</span><span class="sxs-lookup"><span data-stu-id="c1f29-176">The following command performs metadata validation checks and MSIL type safety verification checks for methods implemented in the assembly `myAssembly.exe`.</span></span> <span data-ttu-id="c1f29-177">L'outil affiche le temps requis pour effectuer ces vérifications.</span><span class="sxs-lookup"><span data-stu-id="c1f29-177">The tool displays the time required to perform these checks.</span></span>  
  
```  
peverify myAssembly.exe /md /il /clock  
```  
  
 <span data-ttu-id="c1f29-178">Une fois les contrôles ci‑dessus terminés, Peverify.exe affiche le message suivant.</span><span class="sxs-lookup"><span data-stu-id="c1f29-178">Upon successful completion of the above request, Peverify.exe displays the following message.</span></span>  
  
```  
All classes and methods in myAssembly.exe Verified  
Timing: Total run     320 msec  
        MD Val.cycle  40 msec  
        MD Val.pure   10 msec  
        IL Ver.cycle  270 msec  
        IL Ver.pure   230 msec  
```  
  
 <span data-ttu-id="c1f29-179">La commande suivante procède aux contrôles de validation des métadonnées et aux contrôles de vérification de la sécurité de type MSIL pour les méthodes implémentées dans l'assembly `myAssembly.exe`.</span><span class="sxs-lookup"><span data-stu-id="c1f29-179">The following command performs metadata validation checks and MSIL type safety verification checks for methods implemented in the assembly `myAssembly.exe`.</span></span> <span data-ttu-id="c1f29-180">Toutefois, Peverify.exe s'arrête lorsqu'il atteint le nombre d'erreurs maximal de 100.</span><span class="sxs-lookup"><span data-stu-id="c1f29-180">Peverify.exe stops, however, when it reaches the maximum error count of 100.</span></span> <span data-ttu-id="c1f29-181">L'outil ignore également les codes d'erreur spécifiés.</span><span class="sxs-lookup"><span data-stu-id="c1f29-181">The tool also ignores the specified error codes.</span></span>  
  
```  
peverify myAssembly.exe /break=100 /ignore=0x12345678,0xABCD1234  
```  
  
 <span data-ttu-id="c1f29-182">La commande suivante aboutit au même résultat que dans l'exemple précédent, mais elle spécifie les codes d'erreur à ignorer dans le fichier réponse `ignoreErrors.rsp`.</span><span class="sxs-lookup"><span data-stu-id="c1f29-182">The following command produces the same result as the above previous example, but specifies the error codes to ignore in the response file `ignoreErrors.rsp`.</span></span>  
  
```  
peverify myAssembly.exe /break=100 /ignore@ignoreErrors.rsp  
```  
  
 <span data-ttu-id="c1f29-183">Le fichier réponse peut comporter une liste de codes d'erreur avec la virgule comme séparateur.</span><span class="sxs-lookup"><span data-stu-id="c1f29-183">The response file can contain a comma-separated list of error codes.</span></span>  
  
```  
0x12345678, 0xABCD1234  
```  
  
 <span data-ttu-id="c1f29-184">Le fichier réponse peut également être mis en forme avec un code d'erreur par ligne.</span><span class="sxs-lookup"><span data-stu-id="c1f29-184">Alternatively, the response file can be formatted with one error code per line.</span></span>  
  
```  
0x12345678  
0xABCD1234  
```  
  
## <a name="see-also"></a><span data-ttu-id="c1f29-185">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="c1f29-185">See Also</span></span>  
 [<span data-ttu-id="c1f29-186">Outils</span><span class="sxs-lookup"><span data-stu-id="c1f29-186">Tools</span></span>](../../../docs/framework/tools/index.md)  
 [<span data-ttu-id="c1f29-187">NIB : Écriture de code de type sécurisé vérifié</span><span class="sxs-lookup"><span data-stu-id="c1f29-187">NIB: Writing Verifiably Type-Safe Code</span></span>](http://msdn.microsoft.com/library/d18f10ef-3b48-4f47-8726-96714021547b)  
 [<span data-ttu-id="c1f29-188">Cohérence des types et sécurité</span><span class="sxs-lookup"><span data-stu-id="c1f29-188">Type Safety and Security</span></span>](http://msdn.microsoft.com/library/095cd1f6-d8db-4c0e-bce2-83ccb34dd5dc)  
 [<span data-ttu-id="c1f29-189">Invites de commandes</span><span class="sxs-lookup"><span data-stu-id="c1f29-189">Command Prompts</span></span>](../../../docs/framework/tools/developer-command-prompt-for-vs.md)
