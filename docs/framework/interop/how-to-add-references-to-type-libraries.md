---
title: "Comment : ajouter des références aux bibliothèques de types"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- importing type library
- interop assemblies, generating
- type libraries
- COM interop, importing type library
ms.assetid: f5cfa6ba-cc25-4017-82cd-ba7391859113
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 4e80c4bf5142a9bbbd2b7f75d67553db73f0ff22
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-add-references-to-type-libraries"></a><span data-ttu-id="21590-102">Comment : ajouter des références aux bibliothèques de types</span><span class="sxs-lookup"><span data-stu-id="21590-102">How to: Add References to Type Libraries</span></span>
<span data-ttu-id="21590-103">Quand vous ajoutez une référence à une bibliothèque de types, Visual Studio génère un assembly d'interopérabilité contenant des métadonnées.</span><span class="sxs-lookup"><span data-stu-id="21590-103">Visual Studio generates an interop assembly containing metadata when you add a reference to a type library.</span></span> <span data-ttu-id="21590-104">Si un assembly PIA (Primary Interop Assembly) est disponible, Visual Studio utilise l'assembly existant avant de générer un nouvel assembly d'interopérabilité.</span><span class="sxs-lookup"><span data-stu-id="21590-104">If a primary interop assembly is available, Visual Studio uses the existing assembly before generating a new interop assembly.</span></span>  
  
### <a name="to-add-a-reference-to-a-type-library-in-visual-studio"></a><span data-ttu-id="21590-105">Pour ajouter une référence dans une bibliothèque de types Visual Studio</span><span class="sxs-lookup"><span data-stu-id="21590-105">To add a reference to a type library in Visual Studio</span></span>  
  
1.  <span data-ttu-id="21590-106">Installez le fichier COM DLL ou EXE sur votre ordinateur, à moins que le fichier Setup.exe de Windows n'exécute l'installation à votre place.</span><span class="sxs-lookup"><span data-stu-id="21590-106">Install the COM DLL or EXE file on your computer, unless a Windows Setup.exe file performs the installation for you.</span></span>  
  
2.  <span data-ttu-id="21590-107">Choisissez **Projet**, **Ajouter une référence**.</span><span class="sxs-lookup"><span data-stu-id="21590-107">Choose **Project**, **Add Reference**.</span></span>  
  
3.  <span data-ttu-id="21590-108">Dans le Gestionnaire de références, choisissez **COM**.</span><span class="sxs-lookup"><span data-stu-id="21590-108">In the Reference Manager, choose **COM**.</span></span>  
  
4.  <span data-ttu-id="21590-109">Sélectionnez la bibliothèque de types dans la liste, ou naviguez jusqu'au fichier .tlb.</span><span class="sxs-lookup"><span data-stu-id="21590-109">Select the type library from the list, or browse for the .tlb file.</span></span>  
  
5.  <span data-ttu-id="21590-110">Cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="21590-110">Choose **OK**.</span></span>  
  
6.  <span data-ttu-id="21590-111">Dans l’Explorateur de solutions, ouvrez le menu contextuel pour afficher la référence que vous venez d’ajouter, puis choisissez **Propriétés**.</span><span class="sxs-lookup"><span data-stu-id="21590-111">In Solution Explorer, open the shortcut menu for the reference you just added, and then choose **Properties**.</span></span>  
  
7.  <span data-ttu-id="21590-112">Dans la fenêtre **Propriétés**, vérifiez que la propriété **Incorporer les types interop** a la valeur **True**.</span><span class="sxs-lookup"><span data-stu-id="21590-112">In the **Properties** window, make sure that the **Embed Interop Types** property is set to **True**.</span></span> <span data-ttu-id="21590-113">Visual Studio incorpore alors les informations de type pour les types COM dans vos fichiers exécutables, en éliminant le besoin de déployer des assemblys PIA (Primary Interop Assembly) avec votre application.</span><span class="sxs-lookup"><span data-stu-id="21590-113">This causes Visual Studio to embed type information for COM types in your executables, eliminating the need to deploy primary interop assemblies with your app.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="21590-114">Les options de menu et de boîte de dialogue peuvent varier en fonction de la version de Visual Studio utilisée.</span><span class="sxs-lookup"><span data-stu-id="21590-114">The menu and dialog box options may vary depending on the version of Visual Studio you're using.</span></span>  
  
### <a name="to-add-a-reference-to-a-type-library-for-command-line-compilation"></a><span data-ttu-id="21590-115">Pour ajouter une référence à une bibliothèque de types pour la compilation en ligne de commande</span><span class="sxs-lookup"><span data-stu-id="21590-115">To add a reference to a type library for command-line compilation</span></span>  
  
1.  <span data-ttu-id="21590-116">Générez un assembly d’interopérabilité comme décrit dans [Guide pratique pour générer des assemblys d’interopérabilité à partir de bibliothèques de types](../../../docs/framework/interop/how-to-generate-interop-assemblies-from-type-libraries.md).</span><span class="sxs-lookup"><span data-stu-id="21590-116">Generate an interop assembly as described in [How to: Generate Interop Assemblies from Type Libraries](../../../docs/framework/interop/how-to-generate-interop-assemblies-from-type-libraries.md).</span></span>  
  
2.  <span data-ttu-id="21590-117">Utilisez l’option du compilateur [/link (Options du compilateur C#)](~/docs/csharp/language-reference/compiler-options/link-compiler-option.md) ou [/link (Visual Basic)](~/docs/visual-basic/reference/command-line-compiler/link.md) avec le nom de l’assembly d’interopérabilité afin d’incorporer les informations de type pour les types COM dans vos fichiers exécutables.</span><span class="sxs-lookup"><span data-stu-id="21590-117">Use the [/link (C# Compiler Options)](~/docs/csharp/language-reference/compiler-options/link-compiler-option.md) or [/link (Visual Basic)](~/docs/visual-basic/reference/command-line-compiler/link.md) compiler option with the interop assembly name to embed type information for COM types in your executables.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="21590-118">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="21590-118">See Also</span></span>  
 [<span data-ttu-id="21590-119">Importation d'une bibliothèque de types sous la forme d'un assembly</span><span class="sxs-lookup"><span data-stu-id="21590-119">Importing a Type Library as an Assembly</span></span>](../../../docs/framework/interop/importing-a-type-library-as-an-assembly.md)  
 [<span data-ttu-id="21590-120">Exposition de composants COM au .NET Framework</span><span class="sxs-lookup"><span data-stu-id="21590-120">Exposing COM Components to the .NET Framework</span></span>](../../../docs/framework/interop/exposing-com-components.md)  
 [<span data-ttu-id="21590-121">Procédure pas à pas : incorporation d’informations de type provenant d’assemblys Microsoft Office</span><span class="sxs-lookup"><span data-stu-id="21590-121">Walkthrough: Embedding Type Information from Microsoft Office Assemblies</span></span>](http://msdn.microsoft.com/library/85b55e05-bc5e-4665-b6ae-e1ada9299fd3)  
 [<span data-ttu-id="21590-122">Procédure pas à pas : incorporation de types provenant d’assemblys managés</span><span class="sxs-lookup"><span data-stu-id="21590-122">Walkthrough: Embedding Types from Managed Assemblies</span></span>](http://msdn.microsoft.com/library/b28ec92c-1867-4847-95c0-61adfe095e21)  
 [<span data-ttu-id="21590-123">/link (Options du compilateur C#)</span><span class="sxs-lookup"><span data-stu-id="21590-123">/link (C# Compiler Options)</span></span>](~/docs/csharp/language-reference/compiler-options/link-compiler-option.md)  
 [<span data-ttu-id="21590-124">/link (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="21590-124">/link (Visual Basic)</span></span>](~/docs/visual-basic/reference/command-line-compiler/link.md)
