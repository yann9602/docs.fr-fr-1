---
title: /out (Visual Basic) | Documents Microsoft
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
- /out compiler option [Visual Basic]
- -out compiler option [Visual Basic]
- out compiler option [Visual Basic]
ms.assetid: 9f148c15-0909-4cb8-a2db-777f8a8b45ae
caps.latest.revision: 17
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
ms.openlocfilehash: 489a9015718a581c793cd1217ba073625929daf3
ms.contentlocale: fr-fr
ms.lasthandoff: 04/12/2017

---
# <a name="out-visual-basic"></a><span data-ttu-id="99b86-102">/out (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="99b86-102">/out (Visual Basic)</span></span>
<span data-ttu-id="99b86-103">Spécifie le nom du fichier de sortie.</span><span class="sxs-lookup"><span data-stu-id="99b86-103">Specifies the name of the output file.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="99b86-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="99b86-104">Syntax</span></span>  
  
```  
/out:filename  
```  
  
## <a name="arguments"></a><span data-ttu-id="99b86-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="99b86-105">Arguments</span></span>  
  
|<span data-ttu-id="99b86-106">Terme</span><span class="sxs-lookup"><span data-stu-id="99b86-106">Term</span></span>|<span data-ttu-id="99b86-107">Définition</span><span class="sxs-lookup"><span data-stu-id="99b86-107">Definition</span></span>|  
|---|---|  
|`filename`|<span data-ttu-id="99b86-108">Obligatoire.</span><span class="sxs-lookup"><span data-stu-id="99b86-108">Required.</span></span> <span data-ttu-id="99b86-109">Le nom du fichier de sortie, que le compilateur crée.</span><span class="sxs-lookup"><span data-stu-id="99b86-109">The name of the output file the compiler creates.</span></span> <span data-ttu-id="99b86-110">Si le nom de fichier contient un espace, placez le nom entre guillemets (« »).</span><span class="sxs-lookup"><span data-stu-id="99b86-110">If the file name contains a space, enclose the name in quotation marks (" ").</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="99b86-111">Remarques</span><span class="sxs-lookup"><span data-stu-id="99b86-111">Remarks</span></span>  
 <span data-ttu-id="99b86-112">Spécifiez le nom complet et l’extension du fichier à créer.</span><span class="sxs-lookup"><span data-stu-id="99b86-112">Specify the full name and extension of the file to create.</span></span> <span data-ttu-id="99b86-113">Si vous ne le faites pas, le fichier .exe tire son nom du fichier de code source contenant le `Sub Main` procédure et le fichier .dll tire son nom du premier fichier de code source.</span><span class="sxs-lookup"><span data-stu-id="99b86-113">If you do not, the .exe file takes its name from the source-code file containing the `Sub Main` procedure, and the .dll file takes its name from the first source-code file.</span></span>  
  
 <span data-ttu-id="99b86-114">Si vous spécifiez un nom de fichier sans l’extension .exe ou .dll, le compilateur ajoute automatiquement l’extension pour vous, selon la valeur spécifiée pour la `/target` option du compilateur.</span><span class="sxs-lookup"><span data-stu-id="99b86-114">If you specify a file name without an .exe or .dll extension, the compiler automatically adds the extension for you, depending on the value specified for the `/target` compiler option.</span></span>  
  
|<span data-ttu-id="99b86-115">Pour définir /out dans l’environnement de développement intégré Visual Studio</span><span class="sxs-lookup"><span data-stu-id="99b86-115">To set /out in the Visual Studio integrated development environment</span></span>|  
|---|  
|<span data-ttu-id="99b86-116">1.  Sélectionnez un projet dans l' **Explorateur de solutions**.</span><span class="sxs-lookup"><span data-stu-id="99b86-116">1.  Have a project selected in **Solution Explorer**.</span></span> <span data-ttu-id="99b86-117">Sur le **projet** menu, cliquez sur **propriétés**.</span><span class="sxs-lookup"><span data-stu-id="99b86-117">On the **Project** menu, click **Properties**.</span></span> <span data-ttu-id="99b86-118">Pour plus d’informations, consultez [Introduction au Concepteur de projets](http://msdn.microsoft.com/en-us/898dd854-c98d-430c-ba1b-a913ce3c73d7).</span><span class="sxs-lookup"><span data-stu-id="99b86-118">For more information, see [Introduction to the Project Designer](http://msdn.microsoft.com/en-us/898dd854-c98d-430c-ba1b-a913ce3c73d7).</span></span><br /><span data-ttu-id="99b86-119">2.  Cliquez sur l’onglet **Application** .</span><span class="sxs-lookup"><span data-stu-id="99b86-119">2.  Click the **Application** tab.</span></span><br /><span data-ttu-id="99b86-120">3.  Modifiez la valeur dans la **nom de l’Assembly** boîte.</span><span class="sxs-lookup"><span data-stu-id="99b86-120">3.  Modify the value in the **Assembly Name** box.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="99b86-121">Exemple</span><span class="sxs-lookup"><span data-stu-id="99b86-121">Example</span></span>  
 <span data-ttu-id="99b86-122">Le code suivant compile `T2.vb` et crée le fichier de sortie `T2.exe`.</span><span class="sxs-lookup"><span data-stu-id="99b86-122">The following code compiles `T2.vb` and creates output file `T2.exe`.</span></span>  
  
```  
vbc t2.vb /out:t3.exe  
```  
  
## <a name="see-also"></a><span data-ttu-id="99b86-123">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="99b86-123">See Also</span></span>  
 <span data-ttu-id="99b86-124">[Compilateur de ligne de commande de Visual Basic](../../../visual-basic/reference/command-line-compiler/index.md) </span><span class="sxs-lookup"><span data-stu-id="99b86-124">[Visual Basic Command-Line Compiler](../../../visual-basic/reference/command-line-compiler/index.md) </span></span>  
<span data-ttu-id="99b86-125"> [/target (Visual Basic)](../../../visual-basic/reference/command-line-compiler/target.md) </span><span class="sxs-lookup"><span data-stu-id="99b86-125"> [/target (Visual Basic)](../../../visual-basic/reference/command-line-compiler/target.md) </span></span>  
<span data-ttu-id="99b86-126"> [Exemples de lignes de commande de compilation](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)</span><span class="sxs-lookup"><span data-stu-id="99b86-126"> [Sample Compilation Command Lines](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)</span></span>
