---
title: /rootnamespace
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- /rootnamespace
- rootnamespace
helpviewer_keywords:
- /rootnamespace compiler option [Visual Basic]
- -rootnamespace compiler option [Visual Basic]
- rootnamespace compiler option [Visual Basic]
ms.assetid: e9245edf-6bef-420d-a7c7-324117752783
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: b02171b28034d676b7027e96c2c66e36be9ae604
ms.sourcegitcommit: 34ec7753acf76f90a0fa845235ef06663dc9e36e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/21/2017
---
# <a name="rootnamespace"></a><span data-ttu-id="1fc64-102">/rootnamespace</span><span class="sxs-lookup"><span data-stu-id="1fc64-102">/rootnamespace</span></span>
<span data-ttu-id="1fc64-103">Spécifie un espace de noms pour toutes les déclarations de type.</span><span class="sxs-lookup"><span data-stu-id="1fc64-103">Specifies a namespace for all type declarations.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1fc64-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="1fc64-104">Syntax</span></span>  
  
```  
/rootnamespace:namespace  
```  
  
## <a name="arguments"></a><span data-ttu-id="1fc64-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="1fc64-105">Arguments</span></span>  
  
|<span data-ttu-id="1fc64-106">Terme</span><span class="sxs-lookup"><span data-stu-id="1fc64-106">Term</span></span>|<span data-ttu-id="1fc64-107">Définition</span><span class="sxs-lookup"><span data-stu-id="1fc64-107">Definition</span></span>|  
|---|---|  
|`namespace`|<span data-ttu-id="1fc64-108">Le nom de l’espace de noms dans lequel placer toutes les déclarations de type pour le projet actuel.</span><span class="sxs-lookup"><span data-stu-id="1fc64-108">The name of the namespace in which to enclose all type declarations for the current project.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="1fc64-109">Notes</span><span class="sxs-lookup"><span data-stu-id="1fc64-109">Remarks</span></span>  
 <span data-ttu-id="1fc64-110">Si vous utilisez le fichier exécutable Visual Studio (Devenv.exe) pour compiler un projet créé dans l’environnement de développement intégré Visual Studio, utilisez `/rootnamespace` pour spécifier la valeur de la <xref:VSLangProj80.VBProjectProperties3.RootNamespace%2A> propriété.</span><span class="sxs-lookup"><span data-stu-id="1fc64-110">If you use the Visual Studio executable file (Devenv.exe) to compile a project created in the Visual Studio integrated development environment, use `/rootnamespace` to specify the value of the <xref:VSLangProj80.VBProjectProperties3.RootNamespace%2A> property.</span></span> <span data-ttu-id="1fc64-111">Consultez [commutateurs de ligne de commande Devenv](/visualstudio/ide/reference/devenv-command-line-switches) pour plus d’informations.</span><span class="sxs-lookup"><span data-stu-id="1fc64-111">See [Devenv Command Line Switches](/visualstudio/ide/reference/devenv-command-line-switches) for more information.</span></span>  
  
 <span data-ttu-id="1fc64-112">Utilisez le désassembleur MSIL du common language runtime (`Ildasm.exe`) pour afficher les noms de l’espace de noms dans votre fichier de sortie.</span><span class="sxs-lookup"><span data-stu-id="1fc64-112">Use the common language runtime MSIL Disassembler (`Ildasm.exe`) to view the namespace names in your output file.</span></span>  
  
|<span data-ttu-id="1fc64-113">Pour définir/rootnamespace dans Visual Studio environnement de développement intégré</span><span class="sxs-lookup"><span data-stu-id="1fc64-113">To set /rootnamespace in the Visual Studio integrated development environment</span></span>|  
|---|  
|<span data-ttu-id="1fc64-114">1.  Sélectionnez un projet dans l' **Explorateur de solutions**.</span><span class="sxs-lookup"><span data-stu-id="1fc64-114">1.  Have a project selected in **Solution Explorer**.</span></span> <span data-ttu-id="1fc64-115">Dans le menu **Projet**, cliquez sur **Propriétés**.</span><span class="sxs-lookup"><span data-stu-id="1fc64-115">On the **Project** menu, click **Properties**.</span></span> <br /><span data-ttu-id="1fc64-116">2.  Cliquez sur l’onglet **Application** .</span><span class="sxs-lookup"><span data-stu-id="1fc64-116">2.  Click the **Application** tab.</span></span><br /><span data-ttu-id="1fc64-117">3.  Modifiez la valeur dans la **racine Namespace** boîte.</span><span class="sxs-lookup"><span data-stu-id="1fc64-117">3.  Modify the value in the **Root Namespace** box.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="1fc64-118">Exemple</span><span class="sxs-lookup"><span data-stu-id="1fc64-118">Example</span></span>  
 <span data-ttu-id="1fc64-119">Le code suivant compile `In.vb` et englobe toutes les déclarations de type dans l’espace de noms `mynamespace`.</span><span class="sxs-lookup"><span data-stu-id="1fc64-119">The following code compiles `In.vb` and encloses all type declarations in the namespace `mynamespace`.</span></span>  
  
```  
vbc /rootnamespace:mynamespace in.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="1fc64-120">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="1fc64-120">See Also</span></span>  
 [<span data-ttu-id="1fc64-121">Compilateur de ligne de commande de Visual Basic</span><span class="sxs-lookup"><span data-stu-id="1fc64-121">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)  
 [<span data-ttu-id="1fc64-122">Ildasm.exe (désassembleur IL)</span><span class="sxs-lookup"><span data-stu-id="1fc64-122">Ildasm.exe (IL Disassembler)</span></span>](https://msdn.microsoft.com/library/f7dy01k1)  
 [<span data-ttu-id="1fc64-123">Exemples de lignes de commande de compilation</span><span class="sxs-lookup"><span data-stu-id="1fc64-123">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
