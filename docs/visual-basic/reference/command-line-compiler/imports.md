---
title: /Imports (Visual Basic) | Documents Microsoft
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
- /imports compiler option [Visual Basic]
- imports compiler option [Visual Basic]
- -imports compiler option [Visual Basic]
ms.assetid: 9a93fb53-c080-497b-bf9b-441022dbbc39
caps.latest.revision: 15
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
ms.openlocfilehash: e994e94dcc3cd00f868b6ae90e4c019eb5b9e2eb
ms.contentlocale: fr-fr
ms.lasthandoff: 04/12/2017

---
# <a name="imports-visual-basic"></a><span data-ttu-id="9f84a-102">/imports (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="9f84a-102">/imports (Visual Basic)</span></span>
<span data-ttu-id="9f84a-103">Importe des espaces de noms à partir d’un assembly spécifié.</span><span class="sxs-lookup"><span data-stu-id="9f84a-103">Imports namespaces from a specified assembly.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9f84a-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="9f84a-104">Syntax</span></span>  
  
```  
/imports:namespaceList  
```  
  
## <a name="arguments"></a><span data-ttu-id="9f84a-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="9f84a-105">Arguments</span></span>  
  
|<span data-ttu-id="9f84a-106">Terme</span><span class="sxs-lookup"><span data-stu-id="9f84a-106">Term</span></span>|<span data-ttu-id="9f84a-107">Définition</span><span class="sxs-lookup"><span data-stu-id="9f84a-107">Definition</span></span>|  
|---|---|  
|`namespaceList`|<span data-ttu-id="9f84a-108">Obligatoire.</span><span class="sxs-lookup"><span data-stu-id="9f84a-108">Required.</span></span> <span data-ttu-id="9f84a-109">Liste délimitée par des virgules des espaces de noms à importer.</span><span class="sxs-lookup"><span data-stu-id="9f84a-109">Comma-delimited list of namespaces to be imported.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="9f84a-110">Remarques</span><span class="sxs-lookup"><span data-stu-id="9f84a-110">Remarks</span></span>  
 <span data-ttu-id="9f84a-111">La `/imports` option importe un espace de noms défini dans l’ensemble des fichiers source ou à partir de tout assembly référencé actuel.</span><span class="sxs-lookup"><span data-stu-id="9f84a-111">The `/imports` option imports any namespace defined within the current set of source files or from any referenced assembly.</span></span>  
  
 <span data-ttu-id="9f84a-112">Les membres d’un espace de noms spécifiés avec `/imports` sont disponibles pour tous les fichiers de code source dans la compilation.</span><span class="sxs-lookup"><span data-stu-id="9f84a-112">The members in a namespace specified with `/imports` are available to all source-code files in the compilation.</span></span> <span data-ttu-id="9f84a-113">Utilisez le [Imports, instruction (.NET Namespace et Type)](../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md) à utiliser un espace de noms dans un fichier de code source unique.</span><span class="sxs-lookup"><span data-stu-id="9f84a-113">Use the [Imports Statement (.NET Namespace and Type)](../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md) to use a namespace in a single source-code file.</span></span>  
  
|<span data-ttu-id="9f84a-114">Pour définir /Imports dans l’environnement de développement intégré Visual Studio</span><span class="sxs-lookup"><span data-stu-id="9f84a-114">To set /imports in the Visual Studio integrated development environment</span></span>|  
|---|  
|<span data-ttu-id="9f84a-115">1.  Sélectionnez un projet dans l' **Explorateur de solutions**.</span><span class="sxs-lookup"><span data-stu-id="9f84a-115">1.  Have a project selected in **Solution Explorer**.</span></span> <span data-ttu-id="9f84a-116">Sur le **projet** menu, cliquez sur **propriétés**.</span><span class="sxs-lookup"><span data-stu-id="9f84a-116">On the **Project** menu, click **Properties**.</span></span> <span data-ttu-id="9f84a-117">Pour plus d’informations, consultez [Introduction au Concepteur de projets](http://msdn.microsoft.com/en-us/898dd854-c98d-430c-ba1b-a913ce3c73d7).</span><span class="sxs-lookup"><span data-stu-id="9f84a-117">For more information, see [Introduction to the Project Designer](http://msdn.microsoft.com/en-us/898dd854-c98d-430c-ba1b-a913ce3c73d7).</span></span><br /><span data-ttu-id="9f84a-118">2.  Cliquez sur le **références** onglet.</span><span class="sxs-lookup"><span data-stu-id="9f84a-118">2.  Click the **References** tab.</span></span><br /><span data-ttu-id="9f84a-119">3.  Entrez le nom de l’espace de noms dans la zone en regard de la **ajouter une importation utilisateur** bouton.</span><span class="sxs-lookup"><span data-stu-id="9f84a-119">3.  Enter the namespace name in the box beside the **Add User Import** button.</span></span><br /><span data-ttu-id="9f84a-120">4.  Cliquez sur le **ajouter une importation utilisateur** bouton.</span><span class="sxs-lookup"><span data-stu-id="9f84a-120">4.  Click the **Add User Import** button.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="9f84a-121">Exemple</span><span class="sxs-lookup"><span data-stu-id="9f84a-121">Example</span></span>  
 <span data-ttu-id="9f84a-122">Le code suivant compile si `/imports:system` est spécifié.</span><span class="sxs-lookup"><span data-stu-id="9f84a-122">The following code compiles when `/imports:system` is specified.</span></span>  
  
 <span data-ttu-id="9f84a-123">[!code-vb[VbVbalrCompiler n °&21;](../../../visual-basic/reference/command-line-compiler/codesnippet/VisualBasic/imports_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="9f84a-123">[!code-vb[VbVbalrCompiler#21](../../../visual-basic/reference/command-line-compiler/codesnippet/VisualBasic/imports_1.vb)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9f84a-124">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="9f84a-124">See Also</span></span>  
 <span data-ttu-id="9f84a-125">[Compilateur de ligne de commande de Visual Basic](../../../visual-basic/reference/command-line-compiler/index.md) </span><span class="sxs-lookup"><span data-stu-id="9f84a-125">[Visual Basic Command-Line Compiler](../../../visual-basic/reference/command-line-compiler/index.md) </span></span>  
<span data-ttu-id="9f84a-126"> [Références et l’instruction Imports](../../../visual-basic/programming-guide/program-structure/references-and-the-imports-statement.md) </span><span class="sxs-lookup"><span data-stu-id="9f84a-126"> [References and the Imports Statement](../../../visual-basic/programming-guide/program-structure/references-and-the-imports-statement.md) </span></span>  
<span data-ttu-id="9f84a-127"> [Exemples de lignes de commande de compilation](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)</span><span class="sxs-lookup"><span data-stu-id="9f84a-127"> [Sample Compilation Command Lines](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)</span></span>
