---
title: -errorreport (Options du compilateur C#)
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords: /errorreport
helpviewer_keywords:
- -errorreport compiler option [C#]
- errorreport compiler option [C#]
- /errorreport compiler option [C#]
ms.assetid: bd0e7493-b79d-4369-9c3f-ba26ebdfbedf
caps.latest.revision: "35"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 6d2fcb3f0bf4491de23b70c8beebf7ae495b2aa0
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/19/2018
---
# <a name="-errorreport-c-compiler-options"></a><span data-ttu-id="7be0a-102">-errorreport (Options du compilateur C#)</span><span class="sxs-lookup"><span data-stu-id="7be0a-102">-errorreport (C# Compiler Options)</span></span>
<span data-ttu-id="7be0a-103">Cette option fournit un moyen pratique de signaler une erreur interne du compilateur C# à Microsoft.</span><span class="sxs-lookup"><span data-stu-id="7be0a-103">This option provides a convenient way to report a C# internal compiler error to Microsoft.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="7be0a-104">Sur Windows Vista et Windows Server 2008, les paramètres de rapport d’erreurs que vous spécifiez pour Visual Studio ne remplacent pas les paramètres définis par l’intermédiaire de Rapport d’erreurs Windows.</span><span class="sxs-lookup"><span data-stu-id="7be0a-104">On Windows Vista and Windows Server 2008, the error reporting settings that you make for Visual Studio do not override the settings made through Windows Error Reporting (WER).</span></span> <span data-ttu-id="7be0a-105">Les paramètres de Rapport d’erreurs Windows ont toujours priorité sur les paramètres de signalement d’erreurs de Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="7be0a-105">WER settings always take precedence over Visual Studio error reporting settings.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7be0a-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="7be0a-106">Syntax</span></span>  
  
```console  
-errorreport:{ none | prompt | queue | send }  
```  
  
## <a name="arguments"></a><span data-ttu-id="7be0a-107">Arguments</span><span class="sxs-lookup"><span data-stu-id="7be0a-107">Arguments</span></span>  
 <span data-ttu-id="7be0a-108">**none**</span><span class="sxs-lookup"><span data-stu-id="7be0a-108">**none**</span></span>  
 <span data-ttu-id="7be0a-109">Les rapports sur les erreurs internes du compilateur ne seront pas collectés ni envoyés à Microsoft.</span><span class="sxs-lookup"><span data-stu-id="7be0a-109">Reports about internal compiler errors will not be collected or sent to Microsoft.</span></span>  
  
 <span data-ttu-id="7be0a-110">**prompt**</span><span class="sxs-lookup"><span data-stu-id="7be0a-110">**prompt**</span></span>  
 <span data-ttu-id="7be0a-111">Vous invite à envoyer un rapport dès qu'une erreur interne du compilateur se produit.</span><span class="sxs-lookup"><span data-stu-id="7be0a-111">Prompts you to send a report when you receive an internal compiler error.</span></span> <span data-ttu-id="7be0a-112">**prompt** est la valeur par défaut quand vous compilez une application dans l’environnement de développement.</span><span class="sxs-lookup"><span data-stu-id="7be0a-112">**prompt** is the default when you compile an application in the development environment.</span></span>  
  
 <span data-ttu-id="7be0a-113">**queue**</span><span class="sxs-lookup"><span data-stu-id="7be0a-113">**queue**</span></span>  
 <span data-ttu-id="7be0a-114">Met le rapport d’erreurs en file d’attente.</span><span class="sxs-lookup"><span data-stu-id="7be0a-114">Queues the error report.</span></span> <span data-ttu-id="7be0a-115">Quand vous ouvrez une session avec des informations d’identification administratives, vous pouvez signaler toute défaillance qui s’est produite depuis votre dernière connexion.</span><span class="sxs-lookup"><span data-stu-id="7be0a-115">When you log on with administrative credentials, you can report any failures since the last time that you were logged on.</span></span> <span data-ttu-id="7be0a-116">Vous ne serez pas invité à envoyer des rapports d’échecs plus d’une fois tous les trois jours.</span><span class="sxs-lookup"><span data-stu-id="7be0a-116">You will not be prompted to send reports for failures more than once every three days.</span></span> <span data-ttu-id="7be0a-117">**queue** est la valeur par défaut quand vous compilez une application à partir de la ligne de commande.</span><span class="sxs-lookup"><span data-stu-id="7be0a-117">**queue** is the default when you compile an application at the command line.</span></span>  
  
 <span data-ttu-id="7be0a-118">**send**</span><span class="sxs-lookup"><span data-stu-id="7be0a-118">**send**</span></span>  
 <span data-ttu-id="7be0a-119">Envoie automatiquement des rapports d’erreurs internes du compilateur à Microsoft.</span><span class="sxs-lookup"><span data-stu-id="7be0a-119">Automatically sends reports of internal compiler errors to Microsoft.</span></span> <span data-ttu-id="7be0a-120">Pour activer cette option, vous devez tout d’abord accepter la politique de collecte de données de Microsoft.</span><span class="sxs-lookup"><span data-stu-id="7be0a-120">To enable this option, you must first agree to the Microsoft data collection policy.</span></span> <span data-ttu-id="7be0a-121">La première fois que vous spécifiez **-errorreport:send** sur un ordinateur, un message du compilateur vous dirige vers un site web qui affiche la politique de collecte de données de Microsoft.</span><span class="sxs-lookup"><span data-stu-id="7be0a-121">The first time that you specify **-errorreport:send** on a computer, a compiler message will refer you to a Web site that contains the Microsoft data collection policy.</span></span>  
    
## <a name="remarks"></a><span data-ttu-id="7be0a-122">Notes</span><span class="sxs-lookup"><span data-stu-id="7be0a-122">Remarks</span></span>  
 <span data-ttu-id="7be0a-123">Une erreur interne du compilateur se produit quand le compilateur ne peut pas traiter un fichier de code source.</span><span class="sxs-lookup"><span data-stu-id="7be0a-123">An internal compiler error (ICE) results when the compiler cannot process a source code file.</span></span> <span data-ttu-id="7be0a-124">Quand une telle erreur se produit, le compilateur ne génère pas de fichier de sortie ni de diagnostic utile que vous pouvez utiliser pour corriger votre code.</span><span class="sxs-lookup"><span data-stu-id="7be0a-124">When an ICE occurs, the compiler does not produce an output file or any useful diagnostic that you can use to fix your code.</span></span>  
  
 <span data-ttu-id="7be0a-125">Dans les versions précédentes, quand vous receviez une erreur interne du compilateur, vous étiez invité à contacter le Support technique Microsoft pour signaler le problème.</span><span class="sxs-lookup"><span data-stu-id="7be0a-125">In previous releases, when you received an ICE, you were encouraged to contact Microsoft Product Support Services to report the problem.</span></span> <span data-ttu-id="7be0a-126">En utilisant **-errorreport**, vous pouvez fournir des informations sur l’erreur interne du compilateur à l’équipe Visual C#.</span><span class="sxs-lookup"><span data-stu-id="7be0a-126">By using **-errorreport**, you can provide ICE information to the Visual C# team.</span></span> <span data-ttu-id="7be0a-127">Vos rapports d’erreurs peuvent aider à améliorer les versions ultérieures du compilateur.</span><span class="sxs-lookup"><span data-stu-id="7be0a-127">Your error reports can help improve future compiler releases.</span></span>  
  
 <span data-ttu-id="7be0a-128">La capacité d’un utilisateur à envoyer des rapports dépend des autorisations de stratégie ordinateur et utilisateur.</span><span class="sxs-lookup"><span data-stu-id="7be0a-128">A user's ability to send reports depends on computer and user policy permissions.</span></span>  
  
 <span data-ttu-id="7be0a-129">Pour plus d’informations sur le débogueur d’erreur, consultez [Description de l’outil Dr Watson pour Windows (Drwtsn32.exe)](https://support.microsoft.com/help/308538/description-of-the-dr--watson-for-windows-drwtsn32-exe-tool).</span><span class="sxs-lookup"><span data-stu-id="7be0a-129">For more information about error debugger, see [Description of the Dr. Watson for Windows (Drwtsn32.exe) Tool](https://support.microsoft.com/help/308538/description-of-the-dr--watson-for-windows-drwtsn32-exe-tool).</span></span>  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a><span data-ttu-id="7be0a-130">Pour définir cette option du compilateur dans l'environnement de développement Visual Studio</span><span class="sxs-lookup"><span data-stu-id="7be0a-130">To set this compiler option in the Visual Studio development environment</span></span>  
  
1.  <span data-ttu-id="7be0a-131">Ouvrez la page **Propriétés** du projet.</span><span class="sxs-lookup"><span data-stu-id="7be0a-131">Open the project's **Properties** page.</span></span> <span data-ttu-id="7be0a-132">Pour plus d’informations, consultez [Générer, page du Concepteur de projets (C#)](/visualstudio/ide/reference/build-page-project-designer-csharp).</span><span class="sxs-lookup"><span data-stu-id="7be0a-132">For more information, see [Build Page, Project Designer (C#)](/visualstudio/ide/reference/build-page-project-designer-csharp).</span></span>  
  
2.  <span data-ttu-id="7be0a-133">Cliquez sur la page de propriétés **Générer**.</span><span class="sxs-lookup"><span data-stu-id="7be0a-133">Click the **Build** property page.</span></span>  
  
3.  <span data-ttu-id="7be0a-134">Cliquez sur le bouton **Avancées** .</span><span class="sxs-lookup"><span data-stu-id="7be0a-134">Click the **Advanced** button.</span></span>  
  
4.  <span data-ttu-id="7be0a-135">Modifiez la propriété **Rapport d’erreurs du compilateur interne**.</span><span class="sxs-lookup"><span data-stu-id="7be0a-135">Modify the **Internal Compiler Error Reporting** property.</span></span>  
  
 <span data-ttu-id="7be0a-136">Pour plus d'informations sur la façon de définir cette option du compilateur par programme, consultez <xref:VSLangProj80.CSharpProjectConfigurationProperties3.ErrorReport%2A>.</span><span class="sxs-lookup"><span data-stu-id="7be0a-136">For information about how to set this compiler option programmatically, see <xref:VSLangProj80.CSharpProjectConfigurationProperties3.ErrorReport%2A>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7be0a-137">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="7be0a-137">See Also</span></span>  
 [<span data-ttu-id="7be0a-138">Options du compilateur C#</span><span class="sxs-lookup"><span data-stu-id="7be0a-138">C# Compiler Options</span></span>](../../../csharp/language-reference/compiler-options/index.md)
