---
title: "Comment : effectuer une compilation conditionnelle avec Trace et Debug"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- trace compiler options
- trace statements
- compiling source code, trace statements
- tracing [.NET Framework], enabling or disabling
- tracing [.NET Framework], compiling conditionally
- TRACE directive
- conditional compilation, tracing code
ms.assetid: 56d051c3-012c-42c1-9a58-7270edc624aa
caps.latest.revision: "11"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: ccdadc22728c28c8dea80f168a98cb985b2572a7
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-compile-conditionally-with-trace-and-debug"></a><span data-ttu-id="51811-102">Comment : effectuer une compilation conditionnelle avec Trace et Debug</span><span class="sxs-lookup"><span data-stu-id="51811-102">How to: Compile Conditionally with Trace and Debug</span></span>
<span data-ttu-id="51811-103">Quand vous déboguez une application pendant le développement, les sorties de débogage et de traçage sont dirigées vers la fenêtre de sortie dans Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="51811-103">While you are debugging an application during development, both your tracing and debugging output go to the Output window in Visual Studio.</span></span> <span data-ttu-id="51811-104">Toutefois, pour inclure les fonctionnalités de suivi dans une application déployée, vous devez compiler vos applications instrumentées en activant la directive de compilateur **TRACE**.</span><span class="sxs-lookup"><span data-stu-id="51811-104">However, to include tracing features in a deployed application, you must compile your instrumented applications with the **TRACE** compiler directive enabled.</span></span> <span data-ttu-id="51811-105">De cette façon, le code de traçage peut être compilé dans la version commerciale de votre application.</span><span class="sxs-lookup"><span data-stu-id="51811-105">This allows tracing code to be compiled into the release version of your application.</span></span> <span data-ttu-id="51811-106">Si vous n’activez pas la directive **TRACE**, tout le code de suivi est ignoré pendant la compilation et n’est pas inclus dans le code exécutable que vous déployez.</span><span class="sxs-lookup"><span data-stu-id="51811-106">If you do not enable the **TRACE** directive, all tracing code is ignored during compilation and is not included in the executable code that you will deploy.</span></span>  
  
 <span data-ttu-id="51811-107">Les méthodes de traçage et de débogage sont associées à des attributs conditionnels.</span><span class="sxs-lookup"><span data-stu-id="51811-107">Both the tracing and debugging methods have associated conditional attributes.</span></span> <span data-ttu-id="51811-108">Par exemple, si l’attribut conditionnel pour le suivi a la valeur **true**, toutes les instructions de suivi sont incluses dans un assembly (fichier .exe ou .dll compilé) ; si l’attribut conditionnel **Trace** a la valeur **false**, les instructions de suivi ne sont pas incluses.</span><span class="sxs-lookup"><span data-stu-id="51811-108">For example, if the conditional attribute for tracing is **true**, all trace statements are included within an assembly (a compiled .exe file or .dll); if the **Trace** conditional attribute is **false**, the trace statements are not included.</span></span>  
  
 <span data-ttu-id="51811-109">Vous pouvez activer l’attribut conditionnel **Trace** ou **Debug**, les deux ou aucun pour une build.</span><span class="sxs-lookup"><span data-stu-id="51811-109">You can have either the **Trace** or **Debug** conditional attribute turned on for a build, or both, or neither.</span></span> <span data-ttu-id="51811-110">Par conséquent, il existe quatre types de build : **Debug**, **Trace**, les deux ou aucun.</span><span class="sxs-lookup"><span data-stu-id="51811-110">Thus, there are four types of build: **Debug**, **Trace**, both, or neither.</span></span> <span data-ttu-id="51811-111">Certaines versions release pour un déploiement de production peuvent n’en contenir aucun, mais la plupart des builds contiennent les deux.</span><span class="sxs-lookup"><span data-stu-id="51811-111">Some release builds for production deployment might contain neither; most debugging builds contain both.</span></span>  
  
 <span data-ttu-id="51811-112">Vous pouvez spécifier les paramètres du compilateur pour votre application de plusieurs façons :</span><span class="sxs-lookup"><span data-stu-id="51811-112">You can specify the compiler settings for your application in several ways:</span></span>  
  
-   <span data-ttu-id="51811-113">Pages de propriétés</span><span class="sxs-lookup"><span data-stu-id="51811-113">The property pages</span></span>  
  
-   <span data-ttu-id="51811-114">Ligne de commande</span><span class="sxs-lookup"><span data-stu-id="51811-114">The command line</span></span>  
  
-   <span data-ttu-id="51811-115">**#CONST** (pour Visual Basic) et **#define** (pour C#)</span><span class="sxs-lookup"><span data-stu-id="51811-115">**#CONST** (for Visual Basic) and **#define** (for C#)</span></span>  
  
### <a name="to-change-compile-settings-from-the-property-pages-dialog-box"></a><span data-ttu-id="51811-116">Pour modifier les paramètres de compilation dans la boîte de dialogue des pages de propriétés</span><span class="sxs-lookup"><span data-stu-id="51811-116">To change compile settings from the property pages dialog box</span></span>  
  
1.  <span data-ttu-id="51811-117">Cliquez avec le bouton droit sur le nœud du projet dans l’**Explorateur de solutions**.</span><span class="sxs-lookup"><span data-stu-id="51811-117">Right-click the project node in **Solution Explorer**.</span></span>  
  
2.  <span data-ttu-id="51811-118">Choisissez **Propriétés** dans le menu contextuel.</span><span class="sxs-lookup"><span data-stu-id="51811-118">Choose **Properties** from the shortcut menu.</span></span>  
  
    -   <span data-ttu-id="51811-119">En Visual Basic, cliquez sur l’onglet **Compiler** dans le volet gauche de la page de propriétés, puis sur le bouton **Options avancées de compilation** pour afficher la boîte de dialogue **Paramètres avancés du compilateur**.</span><span class="sxs-lookup"><span data-stu-id="51811-119">In Visual Basic, click the **Compile** tab in the left pane of the property page, then click the **Advanced Compile Options** button to display the **Advanced Compiler Settings** dialog box.</span></span> <span data-ttu-id="51811-120">Cochez les cases des paramètres du compilateur que vous voulez activer.</span><span class="sxs-lookup"><span data-stu-id="51811-120">Select the check boxes for the compiler settings you want to enable.</span></span> <span data-ttu-id="51811-121">Décochez les cases des paramètres que vous voulez désactiver.</span><span class="sxs-lookup"><span data-stu-id="51811-121">Clear the check boxes for settings you want to disable.</span></span>  
  
    -   <span data-ttu-id="51811-122">En C#, cliquez sur l’onglet **Générer** dans le volet gauche de la page de propriétés, puis cochez les cases des paramètres du compilateur que vous voulez activer.</span><span class="sxs-lookup"><span data-stu-id="51811-122">In C#, click the **Build** tab in the left pane of the property page, then select the check boxes for the compiler settings you want to enable.</span></span> <span data-ttu-id="51811-123">Décochez les cases des paramètres que vous voulez désactiver.</span><span class="sxs-lookup"><span data-stu-id="51811-123">Clear the check boxes for settings you want to disable.</span></span>  
  
### <a name="to-compile-instrumented-code-using-the-command-line"></a><span data-ttu-id="51811-124">Pour compiler du code instrumenté à l'aide de la ligne de commande</span><span class="sxs-lookup"><span data-stu-id="51811-124">To compile instrumented code using the command line</span></span>  
  
1.  <span data-ttu-id="51811-125">Définissez un commutateur de compilateur conditionnel sur la ligne de commande.</span><span class="sxs-lookup"><span data-stu-id="51811-125">Set a conditional compiler switch on the command line.</span></span> <span data-ttu-id="51811-126">Le compilateur devra contenir du code de traçage ou de débogage dans l'exécutable.</span><span class="sxs-lookup"><span data-stu-id="51811-126">The compiler will include trace or debug code in the executable.</span></span>  
  
     <span data-ttu-id="51811-127">Par exemple, l'instruction de compilateur suivante entrée sur la ligne de commande inclut le code de traçage dans un fichier exécutable compilé :</span><span class="sxs-lookup"><span data-stu-id="51811-127">For example, the following compiler instruction entered on the command line would include your tracing code in a compiled executable:</span></span>  
  
     <span data-ttu-id="51811-128">Pour Visual Basic : **vbc /r:System.dll /d:TRACE=TRUE /d:DEBUG=FALSE MyApplication.vb**</span><span class="sxs-lookup"><span data-stu-id="51811-128">For Visual Basic: **vbc /r:System.dll /d:TRACE=TRUE /d:DEBUG=FALSE MyApplication.vb**</span></span>  
  
     <span data-ttu-id="51811-129">Pour C# : **csc /r:System.dll /d:TRACE /d:DEBUG=FALSE MyApplication.cs**</span><span class="sxs-lookup"><span data-stu-id="51811-129">For C#: **csc /r:System.dll /d:TRACE /d:DEBUG=FALSE MyApplication.cs**</span></span>  
  
    > [!TIP]
    >  <span data-ttu-id="51811-130">Pour compiler plusieurs fichiers d’application, insérez un espace entre les noms de fichiers, par exemple **MyApplication1.vb MyApplication2.vb MyApplication3.vb** ou **MyApplication1.cs MyApplication2.cs MyApplication3.cs**.</span><span class="sxs-lookup"><span data-stu-id="51811-130">To compile more than one application file, leave a blank space between the file names, for example, **MyApplication1.vb MyApplication2.vb MyApplication3.vb** or **MyApplication1.cs MyApplication2.cs MyApplication3.cs**.</span></span>  
  
     <span data-ttu-id="51811-131">La signification des directives de compilation conditionnelle utilisées dans les exemples ci-dessus est la suivante :</span><span class="sxs-lookup"><span data-stu-id="51811-131">The meaning of the conditional-compilation directives used in the above examples is as follows:</span></span>  
  
    |<span data-ttu-id="51811-132">Directive</span><span class="sxs-lookup"><span data-stu-id="51811-132">Directive</span></span>|<span data-ttu-id="51811-133">Signification</span><span class="sxs-lookup"><span data-stu-id="51811-133">Meaning</span></span>|  
    |---------------|-------------|  
    |`vbc`|<span data-ttu-id="51811-134">compilateur Visual Basic</span><span class="sxs-lookup"><span data-stu-id="51811-134">Visual Basic compiler</span></span>|  
    |`csc`|<span data-ttu-id="51811-135">Compilateur C#</span><span class="sxs-lookup"><span data-stu-id="51811-135">C# compiler</span></span>|  
    |`/r:`|<span data-ttu-id="51811-136">Référence un assembly externe (EXE ou DLL)</span><span class="sxs-lookup"><span data-stu-id="51811-136">References an external assembly (EXE or DLL)</span></span>|  
    |`/d:`|<span data-ttu-id="51811-137">Définit un symbole de compilation conditionnelle</span><span class="sxs-lookup"><span data-stu-id="51811-137">Defines a conditional compilation symbol</span></span>|  
  
    > [!NOTE]
    >  <span data-ttu-id="51811-138">Vous devez écrire TRACE ou DEBUG en majuscules.</span><span class="sxs-lookup"><span data-stu-id="51811-138">You must spell TRACE or DEBUG with uppercase letters.</span></span> <span data-ttu-id="51811-139">Pour plus d'informations sur les commandes de compilation conditionnelle, entrez `vbc /?` (pour Visual Basic) ou `csc /?` (pour C#) à l'invite de commandes.</span><span class="sxs-lookup"><span data-stu-id="51811-139">For more information about the conditional compilation commands, enter `vbc /?` (for Visual Basic) or `csc /?` (for C#) at the command prompt.</span></span> <span data-ttu-id="51811-140">Pour plus d’informations, consultez [Génération à partir de la ligne de commande](~/docs/csharp/language-reference/compiler-options/how-to-set-environment-variables-for-the-visual-studio-command-line.md) (C#) ou [Appel du compilateur de ligne de commande](~/docs/visual-basic/reference/command-line-compiler/how-to-invoke-the-command-line-compiler.md) (Visual Basic).</span><span class="sxs-lookup"><span data-stu-id="51811-140">For more information, see [Building from the Command Line](~/docs/csharp/language-reference/compiler-options/how-to-set-environment-variables-for-the-visual-studio-command-line.md) (C#) or [Invoking the Command-Line Compiler](~/docs/visual-basic/reference/command-line-compiler/how-to-invoke-the-command-line-compiler.md) (Visual Basic).</span></span>  
  
### <a name="to-perform-conditional-compilation-using-const-or-define"></a><span data-ttu-id="51811-141">Pour effectuer une compilation conditionnelle à l'aide de #CONST ou #define</span><span class="sxs-lookup"><span data-stu-id="51811-141">To perform conditional compilation using #CONST or #define</span></span>  
  
1.  <span data-ttu-id="51811-142">Tapez l'instruction appropriée pour votre langage de programmation en haut du fichier de code source.</span><span class="sxs-lookup"><span data-stu-id="51811-142">Type the appropriate statement for your programming language at the top of the source code file.</span></span>  
  
    |<span data-ttu-id="51811-143">Langue</span><span class="sxs-lookup"><span data-stu-id="51811-143">Language</span></span>|<span data-ttu-id="51811-144">Instruction</span><span class="sxs-lookup"><span data-stu-id="51811-144">Statement</span></span>|<span data-ttu-id="51811-145">Résultat</span><span class="sxs-lookup"><span data-stu-id="51811-145">Result</span></span>|  
    |--------------|---------------|------------|  
    |<span data-ttu-id="51811-146">**Visual Basic**</span><span class="sxs-lookup"><span data-stu-id="51811-146">**Visual Basic**</span></span>|<span data-ttu-id="51811-147">**#CONST TRACE = true**</span><span class="sxs-lookup"><span data-stu-id="51811-147">**#CONST TRACE = true**</span></span>|<span data-ttu-id="51811-148">Active le traçage</span><span class="sxs-lookup"><span data-stu-id="51811-148">Enables tracing</span></span>|  
    ||<span data-ttu-id="51811-149">**#CONST TRACE = false**</span><span class="sxs-lookup"><span data-stu-id="51811-149">**#CONST TRACE = false**</span></span>|<span data-ttu-id="51811-150">Désactive le traçage</span><span class="sxs-lookup"><span data-stu-id="51811-150">Disables tracing</span></span>|  
    ||<span data-ttu-id="51811-151">**#CONST DEBUG = true**</span><span class="sxs-lookup"><span data-stu-id="51811-151">**#CONST DEBUG = true**</span></span>|<span data-ttu-id="51811-152">Active le débogage</span><span class="sxs-lookup"><span data-stu-id="51811-152">Enables debugging</span></span>|  
    ||<span data-ttu-id="51811-153">**#CONST DEBUG = false**</span><span class="sxs-lookup"><span data-stu-id="51811-153">**#CONST DEBUG = false**</span></span>|<span data-ttu-id="51811-154">Désactive le débogage</span><span class="sxs-lookup"><span data-stu-id="51811-154">Disables debugging</span></span>|  
    |<span data-ttu-id="51811-155">**C#**</span><span class="sxs-lookup"><span data-stu-id="51811-155">**C#**</span></span>|<span data-ttu-id="51811-156">**#define TRACE**</span><span class="sxs-lookup"><span data-stu-id="51811-156">**#define TRACE**</span></span>|<span data-ttu-id="51811-157">Active le traçage</span><span class="sxs-lookup"><span data-stu-id="51811-157">Enables tracing</span></span>|  
    ||<span data-ttu-id="51811-158">**#undef TRACE**</span><span class="sxs-lookup"><span data-stu-id="51811-158">**#undef TRACE**</span></span>|<span data-ttu-id="51811-159">Désactive le traçage</span><span class="sxs-lookup"><span data-stu-id="51811-159">Disables tracing</span></span>|  
    ||<span data-ttu-id="51811-160">**#define DEBUG**</span><span class="sxs-lookup"><span data-stu-id="51811-160">**#define DEBUG**</span></span>|<span data-ttu-id="51811-161">Active le débogage</span><span class="sxs-lookup"><span data-stu-id="51811-161">Enables debugging</span></span>|  
    ||<span data-ttu-id="51811-162">**#undef DEBUG**</span><span class="sxs-lookup"><span data-stu-id="51811-162">**#undef DEBUG**</span></span>|<span data-ttu-id="51811-163">Désactive le débogage</span><span class="sxs-lookup"><span data-stu-id="51811-163">Disables debugging</span></span>|  
  
### <a name="to-disable-tracing-or-debugging"></a><span data-ttu-id="51811-164">Pour désactiver le traçage ou le débogage</span><span class="sxs-lookup"><span data-stu-id="51811-164">To disable tracing or debugging</span></span>  
  
1.  <span data-ttu-id="51811-165">Supprimez la directive de compilateur de votre code source.</span><span class="sxs-lookup"><span data-stu-id="51811-165">Delete the compiler directive from your source code.</span></span>  
  
     <span data-ttu-id="51811-166">\- ou -</span><span class="sxs-lookup"><span data-stu-id="51811-166">\- or -</span></span>  
  
2.  <span data-ttu-id="51811-167">Commentez la directive de compilateur.</span><span class="sxs-lookup"><span data-stu-id="51811-167">Comment out the compiler directive.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="51811-168">Quand vous êtes prêt pour la compilation, vous pouvez choisir **Générer** dans le menu **Générer**, ou utiliser la méthode de ligne de commande, mais sans taper **d:** pour définir les symboles de compilation conditionnelle.</span><span class="sxs-lookup"><span data-stu-id="51811-168">When you are ready to compile, you can either choose **Build** from the **Build** menu, or use the command line method but without typing the **d:** to define conditional compilation symbols.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="51811-169">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="51811-169">See Also</span></span>  
 [<span data-ttu-id="51811-170">Suivi et instrumentation d’applications</span><span class="sxs-lookup"><span data-stu-id="51811-170">Tracing and Instrumenting Applications</span></span>](../../../docs/framework/debug-trace-profile/tracing-and-instrumenting-applications.md)  
 [<span data-ttu-id="51811-171">Guide pratique pour créer, initialiser et configurer des commutateurs de suivi</span><span class="sxs-lookup"><span data-stu-id="51811-171">How to: Create, Initialize and Configure Trace Switches</span></span>](../../../docs/framework/debug-trace-profile/how-to-create-initialize-and-configure-trace-switches.md)  
 [<span data-ttu-id="51811-172">Commutateurs de suivi</span><span class="sxs-lookup"><span data-stu-id="51811-172">Trace Switches</span></span>](../../../docs/framework/debug-trace-profile/trace-switches.md)  
 [<span data-ttu-id="51811-173">Écouteurs de suivi</span><span class="sxs-lookup"><span data-stu-id="51811-173">Trace Listeners</span></span>](../../../docs/framework/debug-trace-profile/trace-listeners.md)  
 [<span data-ttu-id="51811-174">Guide pratique pour ajouter des instructions de suivi au code d’application</span><span class="sxs-lookup"><span data-stu-id="51811-174">How to: Add Trace Statements to Application Code</span></span>](../../../docs/framework/debug-trace-profile/how-to-add-trace-statements-to-application-code.md)  
 [<span data-ttu-id="51811-175">Comment : définir des variables d’environnement pour la ligne de commande Visual Studio</span><span class="sxs-lookup"><span data-stu-id="51811-175">How to: Set Environment Variables for the Visual Studio Command Line</span></span>](~/docs/csharp/language-reference/compiler-options/how-to-set-environment-variables-for-the-visual-studio-command-line.md)  
 [<span data-ttu-id="51811-176">Guide pratique : appeler le compilateur de ligne de commande</span><span class="sxs-lookup"><span data-stu-id="51811-176">How to: Invoke the Command-Line Compiler</span></span>](~/docs/visual-basic/reference/command-line-compiler/how-to-invoke-the-command-line-compiler.md)
