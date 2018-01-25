---
title: "-bugreport (Options du compilateur C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords: /bugreport
helpviewer_keywords:
- /bugreport compiler option [C#]
- -bugreport compiler option [C#]
- bugreport compiler option [C#]
ms.assetid: f39665e3-4f6f-4357-88a2-3274c7bec0c1
caps.latest.revision: "20"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: d2a6c27454cc8f95b9662d6ae688471849c5cee0
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/19/2018
---
# <a name="-bugreport-c-compiler-options"></a><span data-ttu-id="04939-102">-bugreport (Options du compilateur C#)</span><span class="sxs-lookup"><span data-stu-id="04939-102">-bugreport (C# Compiler Options)</span></span>
<span data-ttu-id="04939-103">Spécifie que les informations de débogage doivent être placées dans un fichier pour une future analyse.</span><span class="sxs-lookup"><span data-stu-id="04939-103">Specifies that debug information should be placed in a file for later analysis.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="04939-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="04939-104">Syntax</span></span>  
  
```console  
-bugreport:file  
```  
  
## <a name="arguments"></a><span data-ttu-id="04939-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="04939-105">Arguments</span></span>  
 `file`  
 <span data-ttu-id="04939-106">Nom du fichier qui doit contenir votre rapport de bogues.</span><span class="sxs-lookup"><span data-stu-id="04939-106">The name of the file that you want to contain your bug report.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="04939-107">Notes</span><span class="sxs-lookup"><span data-stu-id="04939-107">Remarks</span></span>  
 <span data-ttu-id="04939-108">L’option **-bugreport** spécifie que les informations suivantes doivent être placées dans `file` :</span><span class="sxs-lookup"><span data-stu-id="04939-108">The **-bugreport** option specifies that the following information should be placed in `file`:</span></span>  
  
-   <span data-ttu-id="04939-109">Une copie de tous les fichiers de code source de la compilation.</span><span class="sxs-lookup"><span data-stu-id="04939-109">A copy of all source code files in the compilation.</span></span>  
  
-   <span data-ttu-id="04939-110">Une liste des options du compilateur utilisées dans la compilation.</span><span class="sxs-lookup"><span data-stu-id="04939-110">A listing of the compiler options used in the compilation.</span></span>  
  
-   <span data-ttu-id="04939-111">Les informations de version concernant votre compilateur, votre runtime et votre système d’exploitation.</span><span class="sxs-lookup"><span data-stu-id="04939-111">Version information about your compiler, run time, and operating system.</span></span>  
  
-   <span data-ttu-id="04939-112">Les assemblys et modules référencés, enregistrés sous la forme de chiffres hexadécimaux, sauf les assemblys qui sont fournis avec le .NET Framework et le SDK.</span><span class="sxs-lookup"><span data-stu-id="04939-112">Referenced assemblies and modules, saved as hexadecimal digits, except assemblies that ship with the .NET Framework and SDK.</span></span>  
  
-   <span data-ttu-id="04939-113">Les résultats de la compilation, le cas échéant.</span><span class="sxs-lookup"><span data-stu-id="04939-113">Compiler output, if any.</span></span>  
  
-   <span data-ttu-id="04939-114">Une description du problème, qui vous sera demandée.</span><span class="sxs-lookup"><span data-stu-id="04939-114">A description of the problem, which you will be prompted for.</span></span>  
  
-   <span data-ttu-id="04939-115">Une description de vos suggestions de résolution du problème, qui vous sera demandée.</span><span class="sxs-lookup"><span data-stu-id="04939-115">A description of how you think the problem should be fixed, which you will be prompted for.</span></span>  
  
 <span data-ttu-id="04939-116">Si cette option est utilisée avec **-errorreport:prompt** ou **-errorreport:send**, les informations figurant dans le fichier seront envoyées à Microsoft Corporation.</span><span class="sxs-lookup"><span data-stu-id="04939-116">If this option is used with **-errorreport:prompt** or **-errorreport:send**, the information in the file will be sent to Microsoft Corporation.</span></span>  
  
 <span data-ttu-id="04939-117">Étant donné qu’une copie de tous les fichiers de code source sera placée dans `file`, vous souhaiterez peut-être reproduire l’erreur de code suspecte dans le programme le plus court possible.</span><span class="sxs-lookup"><span data-stu-id="04939-117">Because a copy of all source code files will be placed in `file`, you might want to reproduce the suspected code defect in the shortest possible program.</span></span>  
  
 <span data-ttu-id="04939-118">Cette option de compilateur n’est pas disponible dans Visual Studio et ne peut pas être changée par programmation.</span><span class="sxs-lookup"><span data-stu-id="04939-118">This compiler option is unavailable in Visual Studio and cannot be changed programmatically.</span></span>  
  
 <span data-ttu-id="04939-119">Notez que le contenu du fichier généré expose le code source, ce qui pourrait entraîner une divulgation d’informations non voulue.</span><span class="sxs-lookup"><span data-stu-id="04939-119">Notice that contents of the generated file expose source code that could result in inadvertent information disclosure.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="04939-120">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="04939-120">See Also</span></span>  
 [<span data-ttu-id="04939-121">Options du compilateur C#</span><span class="sxs-lookup"><span data-stu-id="04939-121">C# Compiler Options</span></span>](../../../csharp/language-reference/compiler-options/index.md)  
 [<span data-ttu-id="04939-122">-errorreport (Options du compilateur C#)</span><span class="sxs-lookup"><span data-stu-id="04939-122">-errorreport (C# Compiler Options)</span></span>](../../../csharp/language-reference/compiler-options/errorreport-compiler-option.md)  
 [<span data-ttu-id="04939-123">Gestion des propriétés des projets et des solutions</span><span class="sxs-lookup"><span data-stu-id="04939-123">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
