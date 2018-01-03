---
title: /imports (Visual Basic)
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- /imports compiler option [Visual Basic]
- imports compiler option [Visual Basic]
- -imports compiler option [Visual Basic]
ms.assetid: 9a93fb53-c080-497b-bf9b-441022dbbc39
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 6cdb7cff2221930113d6b49a640da0844f175f1b
ms.sourcegitcommit: 34ec7753acf76f90a0fa845235ef06663dc9e36e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/21/2017
---
# <a name="imports-visual-basic"></a><span data-ttu-id="e731f-102">/imports (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="e731f-102">/imports (Visual Basic)</span></span>
<span data-ttu-id="e731f-103">Importe des espaces de noms à partir d’un assembly spécifié.</span><span class="sxs-lookup"><span data-stu-id="e731f-103">Imports namespaces from a specified assembly.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e731f-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e731f-104">Syntax</span></span>  
  
```  
/imports:namespaceList  
```  
  
## <a name="arguments"></a><span data-ttu-id="e731f-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="e731f-105">Arguments</span></span>  
  
|<span data-ttu-id="e731f-106">Terme</span><span class="sxs-lookup"><span data-stu-id="e731f-106">Term</span></span>|<span data-ttu-id="e731f-107">Définition</span><span class="sxs-lookup"><span data-stu-id="e731f-107">Definition</span></span>|  
|---|---|  
|`namespaceList`|<span data-ttu-id="e731f-108">Obligatoire.</span><span class="sxs-lookup"><span data-stu-id="e731f-108">Required.</span></span> <span data-ttu-id="e731f-109">Liste délimitée d’espaces de noms à importer.</span><span class="sxs-lookup"><span data-stu-id="e731f-109">Comma-delimited list of namespaces to be imported.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e731f-110">Notes</span><span class="sxs-lookup"><span data-stu-id="e731f-110">Remarks</span></span>  
 <span data-ttu-id="e731f-111">Le `/imports` option importe n’importe quel espace de noms défini dans l’ensemble actuel des fichiers source ou à partir de tout assembly référencé.</span><span class="sxs-lookup"><span data-stu-id="e731f-111">The `/imports` option imports any namespace defined within the current set of source files or from any referenced assembly.</span></span>  
  
 <span data-ttu-id="e731f-112">Les membres d’un espace de noms spécifiés avec `/imports` sont disponibles pour tous les fichiers de code source dans la compilation.</span><span class="sxs-lookup"><span data-stu-id="e731f-112">The members in a namespace specified with `/imports` are available to all source-code files in the compilation.</span></span> <span data-ttu-id="e731f-113">Utilisez le [Imports, instruction (.NET Namespace et Type)](../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md) à utiliser un espace de noms dans un fichier de code source unique.</span><span class="sxs-lookup"><span data-stu-id="e731f-113">Use the [Imports Statement (.NET Namespace and Type)](../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md) to use a namespace in a single source-code file.</span></span>  
  
|<span data-ttu-id="e731f-114">Pour définir /Imports dans l’environnement de développement intégré Visual Studio</span><span class="sxs-lookup"><span data-stu-id="e731f-114">To set /imports in the Visual Studio integrated development environment</span></span>|  
|---|  
|<span data-ttu-id="e731f-115">1.  Sélectionnez un projet dans l' **Explorateur de solutions**.</span><span class="sxs-lookup"><span data-stu-id="e731f-115">1.  Have a project selected in **Solution Explorer**.</span></span> <span data-ttu-id="e731f-116">Dans le menu **Projet**, cliquez sur **Propriétés**.</span><span class="sxs-lookup"><span data-stu-id="e731f-116">On the **Project** menu, click **Properties**.</span></span> <br /><span data-ttu-id="e731f-117">2.  Cliquez sur l’onglet **Références**.</span><span class="sxs-lookup"><span data-stu-id="e731f-117">2.  Click the **References** tab.</span></span><br /><span data-ttu-id="e731f-118">3.  Entrez le nom de l’espace de noms dans la zone en regard de la **ajouter une importation utilisateur** bouton.</span><span class="sxs-lookup"><span data-stu-id="e731f-118">3.  Enter the namespace name in the box beside the **Add User Import** button.</span></span><br /><span data-ttu-id="e731f-119">4.  Cliquez sur le **ajouter une importation utilisateur** bouton.</span><span class="sxs-lookup"><span data-stu-id="e731f-119">4.  Click the **Add User Import** button.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="e731f-120">Exemple</span><span class="sxs-lookup"><span data-stu-id="e731f-120">Example</span></span>  
 <span data-ttu-id="e731f-121">Le code suivant compile si `/imports:system` est spécifié.</span><span class="sxs-lookup"><span data-stu-id="e731f-121">The following code compiles when `/imports:system` is specified.</span></span>  
  
 [!code-vb[VbVbalrCompiler#21](../../../visual-basic/reference/command-line-compiler/codesnippet/VisualBasic/imports_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="e731f-122">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e731f-122">See Also</span></span>  
 [<span data-ttu-id="e731f-123">Compilateur de ligne de commande de Visual Basic</span><span class="sxs-lookup"><span data-stu-id="e731f-123">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)  
 [<span data-ttu-id="e731f-124">Références et l’instruction Imports</span><span class="sxs-lookup"><span data-stu-id="e731f-124">References and the Imports Statement</span></span>](../../../visual-basic/programming-guide/program-structure/references-and-the-imports-statement.md)  
 [<span data-ttu-id="e731f-125">Exemples de lignes de commande de compilation</span><span class="sxs-lookup"><span data-stu-id="e731f-125">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
