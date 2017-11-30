---
title: "-baseaddress (Options du compilateur C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords: /dllbase
helpviewer_keywords:
- baseaddress compiler option [C#]
- /baseaddress compiler option [C#]
- -baseaddress compiler option [C#]
ms.assetid: ce13c965-dfe4-4433-94f5-63b476e3a608
caps.latest.revision: "18"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 7cd3269754f783ab8b26683f5215aa81825673e6
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="baseaddress-c-compiler-options"></a><span data-ttu-id="7291c-102">/baseaddress (Options du compilateur C#)</span><span class="sxs-lookup"><span data-stu-id="7291c-102">/baseaddress (C# Compiler Options)</span></span>
<span data-ttu-id="7291c-103">L’option **/baseaddress** vous permet de spécifier l’adresse de base préférée à laquelle doit être chargée une DLL.</span><span class="sxs-lookup"><span data-stu-id="7291c-103">The **/baseaddress** option lets you specify the preferred base address at which to load a DLL.</span></span> <span data-ttu-id="7291c-104">Pour plus d’informations sur quand et pourquoi utiliser cette option, consultez [blog de Larry Osterman](http://go.microsoft.com/fwlink/?LinkId=107044).</span><span class="sxs-lookup"><span data-stu-id="7291c-104">For more information about when and why to use this option, see [Larry Osterman's WebLog](http://go.microsoft.com/fwlink/?LinkId=107044).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7291c-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="7291c-105">Syntax</span></span>  
  
```console  
/baseaddress:address  
```  
  
## <a name="arguments"></a><span data-ttu-id="7291c-106">Arguments</span><span class="sxs-lookup"><span data-stu-id="7291c-106">Arguments</span></span>  
 `address`  
 <span data-ttu-id="7291c-107">Adresse de base de la DLL.</span><span class="sxs-lookup"><span data-stu-id="7291c-107">The base address for the DLL.</span></span> <span data-ttu-id="7291c-108">Cette adresse peut être spécifiée sous forme d’un nombre décimal, hexadécimal ou octal.</span><span class="sxs-lookup"><span data-stu-id="7291c-108">This address can be specified as a decimal, hexadecimal, or octal number.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="7291c-109">Remarques</span><span class="sxs-lookup"><span data-stu-id="7291c-109">Remarks</span></span>  
 <span data-ttu-id="7291c-110">L’adresse de base par défaut d’une DLL est définie par le Common Language Runtime (CLR) .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="7291c-110">The default base address for a DLL is set by the .NET Framework common language runtime.</span></span>  
  
 <span data-ttu-id="7291c-111">Sachez que le dernier chiffre de cette adresse sera arrondi.</span><span class="sxs-lookup"><span data-stu-id="7291c-111">Be aware that the lower-order word in this address will be rounded.</span></span> <span data-ttu-id="7291c-112">Par exemple, si vous spécifiez l’adresse 0x11110001, elle est arrondie à 0x11110000.</span><span class="sxs-lookup"><span data-stu-id="7291c-112">For example, if you specify 0x11110001, it will be rounded to 0x11110000.</span></span>  
  
 <span data-ttu-id="7291c-113">Pour terminer le processus de signature d’une DLL, utilisez SN.EXE avec l’option -R.</span><span class="sxs-lookup"><span data-stu-id="7291c-113">To complete the signing process for a DLL, use SN.EXE with the -R option.</span></span>  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a><span data-ttu-id="7291c-114">Pour définir cette option du compilateur dans l'environnement de développement Visual Studio</span><span class="sxs-lookup"><span data-stu-id="7291c-114">To set this compiler option in the Visual Studio development environment</span></span>  
  
1.  <span data-ttu-id="7291c-115">Ouvrez la page **Propriétés** du projet.</span><span class="sxs-lookup"><span data-stu-id="7291c-115">Open the project's **Properties** page.</span></span>  
  
2.  <span data-ttu-id="7291c-116">Cliquez sur la page de propriétés **Générer**.</span><span class="sxs-lookup"><span data-stu-id="7291c-116">Click the **Build** property page.</span></span>  
  
3.  <span data-ttu-id="7291c-117">Cliquez sur le bouton **Avancées** .</span><span class="sxs-lookup"><span data-stu-id="7291c-117">Click the **Advanced** button.</span></span>  
  
4.  <span data-ttu-id="7291c-118">Modifiez la propriété **Adresse de base de la DLL**.</span><span class="sxs-lookup"><span data-stu-id="7291c-118">Modify the **DLL Base Address** property.</span></span>  
  
     <span data-ttu-id="7291c-119">Pour définir cette option du compilateur par programmation, consultez <xref:VSLangProj80.CSharpProjectConfigurationProperties3.BaseAddress%2A>.</span><span class="sxs-lookup"><span data-stu-id="7291c-119">To set this compiler option programmatically, see <xref:VSLangProj80.CSharpProjectConfigurationProperties3.BaseAddress%2A>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7291c-120">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="7291c-120">See Also</span></span>  
 <xref:System.Diagnostics.ProcessModule.BaseAddress%2A?displayProperty=nameWithType>  
 [<span data-ttu-id="7291c-121">Options du compilateur C#</span><span class="sxs-lookup"><span data-stu-id="7291c-121">C# Compiler Options</span></span>](../../../csharp/language-reference/compiler-options/index.md)  
 [<span data-ttu-id="7291c-122">Gestion des propriétés des projets et des solutions</span><span class="sxs-lookup"><span data-stu-id="7291c-122">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
