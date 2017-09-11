---
title: / keycontainer | Documents Microsoft
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
- -keycontainer compiler option [Visual Basic]
- keycontainer compiler option [Visual Basic]
- /keycontainer compiler option [Visual Basic]
ms.assetid: 6a9bc861-1752-4db1-9f64-b5252f0482cc
caps.latest.revision: 16
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
ms.openlocfilehash: a783ef85e6ff2b7c6f889f809291ca8c275e709a
ms.contentlocale: fr-fr
ms.lasthandoff: 04/12/2017

---
# <a name="keycontainer"></a><span data-ttu-id="1ae06-102">/keycontainer</span><span class="sxs-lookup"><span data-stu-id="1ae06-102">/keycontainer</span></span>
<span data-ttu-id="1ae06-103">Spécifie un nom de conteneur de clé pour une paire de clés afin d'attribuer un nom fort à un assembly.</span><span class="sxs-lookup"><span data-stu-id="1ae06-103">Specifies a key container name for a key pair to give an assembly a strong name.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1ae06-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="1ae06-104">Syntax</span></span>  
  
```  
/keycontainer:container  
```  
  
## <a name="arguments"></a><span data-ttu-id="1ae06-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="1ae06-105">Arguments</span></span>  
  
|<span data-ttu-id="1ae06-106">Terme</span><span class="sxs-lookup"><span data-stu-id="1ae06-106">Term</span></span>|<span data-ttu-id="1ae06-107">Définition</span><span class="sxs-lookup"><span data-stu-id="1ae06-107">Definition</span></span>|  
|---|---|  
|`container`|<span data-ttu-id="1ae06-108">Obligatoire.</span><span class="sxs-lookup"><span data-stu-id="1ae06-108">Required.</span></span> <span data-ttu-id="1ae06-109">Fichier conteneur qui contient la clé.</span><span class="sxs-lookup"><span data-stu-id="1ae06-109">Container file that contains the key.</span></span> <span data-ttu-id="1ae06-110">Placez le nom de fichier entre guillemets (" ») si le nom contient un espace.</span><span class="sxs-lookup"><span data-stu-id="1ae06-110">Enclose the file name in quotation marks ("") if the name contains a space.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="1ae06-111">Remarques</span><span class="sxs-lookup"><span data-stu-id="1ae06-111">Remarks</span></span>  
 <span data-ttu-id="1ae06-112">Le compilateur crée le composant partageable en insérant une clé publique dans le manifeste d’assembly et en signant l’assembly final avec la clé privée.</span><span class="sxs-lookup"><span data-stu-id="1ae06-112">The compiler creates the sharable component by inserting a public key into the assembly manifest and by signing the final assembly with the private key.</span></span> <span data-ttu-id="1ae06-113">Pour générer un fichier de clé, tapez `sn -k``file` à la ligne de commande.</span><span class="sxs-lookup"><span data-stu-id="1ae06-113">To generate a key file, type `sn -k``file` at the command line.</span></span> <span data-ttu-id="1ae06-114">La `-i` option installe la paire de clés dans un conteneur.</span><span class="sxs-lookup"><span data-stu-id="1ae06-114">The `-i` option installs the key pair into a container.</span></span> <span data-ttu-id="1ae06-115">Pour plus d’informations, consultez [Sn.exe (Strong Name Tool)](https://msdn.microsoft.com/library/k5b5tt23).</span><span class="sxs-lookup"><span data-stu-id="1ae06-115">For more information, see [Sn.exe (Strong Name Tool)](https://msdn.microsoft.com/library/k5b5tt23).</span></span>  
  
 <span data-ttu-id="1ae06-116">Si vous compilez avec `/target:module`, le nom du fichier de clé est conservé dans le module et incorporé dans l’assembly qui est créé lorsque vous compilez un assembly avec [/addmodule](../../../visual-basic/reference/command-line-compiler/addmodule.md).</span><span class="sxs-lookup"><span data-stu-id="1ae06-116">If you compile with `/target:module`, the name of the key file is held in the module and incorporated into the assembly that is created when you compile an assembly with [/addmodule](../../../visual-basic/reference/command-line-compiler/addmodule.md).</span></span>  
  
 <span data-ttu-id="1ae06-117">Vous pouvez également spécifier cette option comme attribut personnalisé (<xref:System.Reflection.AssemblyKeyNameAttribute>) dans le code source de n’importe quel module Microsoft intermediate language (MSIL).</xref:System.Reflection.AssemblyKeyNameAttribute></span><span class="sxs-lookup"><span data-stu-id="1ae06-117">You can also specify this option as a custom attribute (<xref:System.Reflection.AssemblyKeyNameAttribute>) in the source code for any Microsoft intermediate language (MSIL) module.</span></span>  
  
 <span data-ttu-id="1ae06-118">Vous pouvez également passer vos informations de chiffrement au compilateur avec [/keyfile](../../../visual-basic/reference/command-line-compiler/keyfile.md).</span><span class="sxs-lookup"><span data-stu-id="1ae06-118">You can also pass your encryption information to the compiler with [/keyfile](../../../visual-basic/reference/command-line-compiler/keyfile.md).</span></span> <span data-ttu-id="1ae06-119">Utilisez [/delaysign](../../../visual-basic/reference/command-line-compiler/delaysign.md) si vous souhaitez obtenir un assembly partiellement signé.</span><span class="sxs-lookup"><span data-stu-id="1ae06-119">Use [/delaysign](../../../visual-basic/reference/command-line-compiler/delaysign.md) if you want a partially signed assembly.</span></span>  
  
 <span data-ttu-id="1ae06-120">Consultez la page [création et utilisation d’assemblys](https://msdn.microsoft.com/library/xwb8f617) pour plus d’informations sur la signature d’un assembly.</span><span class="sxs-lookup"><span data-stu-id="1ae06-120">See [Creating and Using Strong-Named Assemblies](https://msdn.microsoft.com/library/xwb8f617) for more information on signing an assembly.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="1ae06-121">La `/keycontainer` option n’est pas disponible dans l’environnement de développement Visual Studio ; il est disponible uniquement lors de la compilation à partir de la ligne de commande.</span><span class="sxs-lookup"><span data-stu-id="1ae06-121">The `/keycontainer` option is not available from within the Visual Studio development environment; it is available only when compiling from the command line.</span></span>  
  
## <a name="example"></a><span data-ttu-id="1ae06-122">Exemple</span><span class="sxs-lookup"><span data-stu-id="1ae06-122">Example</span></span>  
 <span data-ttu-id="1ae06-123">Le code suivant compile le fichier source `Input.vb` et spécifie un conteneur de clé.</span><span class="sxs-lookup"><span data-stu-id="1ae06-123">The following code compiles source file `Input.vb` and specifies a key container.</span></span>  
  
```  
vbc /keycontainer:key1 input.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="1ae06-124">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="1ae06-124">See Also</span></span>  
 <span data-ttu-id="1ae06-125">[Assemblys et le Global Assembly Cache](../../../visual-basic/programming-guide/concepts/assemblies-gac/index.md) </span><span class="sxs-lookup"><span data-stu-id="1ae06-125">[Assemblies and the Global Assembly Cache](../../../visual-basic/programming-guide/concepts/assemblies-gac/index.md) </span></span>  
<span data-ttu-id="1ae06-126"> [Compilateur de ligne de commande de Visual Basic](../../../visual-basic/reference/command-line-compiler/index.md) </span><span class="sxs-lookup"><span data-stu-id="1ae06-126"> [Visual Basic Command-Line Compiler](../../../visual-basic/reference/command-line-compiler/index.md) </span></span>  
<span data-ttu-id="1ae06-127"> [/ keyfile](../../../visual-basic/reference/command-line-compiler/keyfile.md) </span><span class="sxs-lookup"><span data-stu-id="1ae06-127"> [/keyfile](../../../visual-basic/reference/command-line-compiler/keyfile.md) </span></span>  
<span data-ttu-id="1ae06-128"> [Exemples de lignes de commande de compilation](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)</span><span class="sxs-lookup"><span data-stu-id="1ae06-128"> [Sample Compilation Command Lines](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)</span></span>
