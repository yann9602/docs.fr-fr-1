---
title: "#<a name=\"pragma-checksum-c-reference\"></a>#pragma checksum (référence C#)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- '#pragma checksum'
dev_langs:
- CSharp
helpviewer_keywords:
- '#pragma checksum [C#]'
ms.assetid: 3673e4ca-6098-4ec1-890f-8fceb2a794a2
caps.latest.revision: 11
author: BillWagner
ms.author: wiwagn
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
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: c48d99843b9ba398dfe8dc3cf0d2264aaf72be9f
ms.contentlocale: fr-fr
ms.lasthandoff: 07/28/2017

---
# <a name="pragma-checksum-c-reference"></a><span data-ttu-id="41864-102">#pragma checksum (Référence C#)</span><span class="sxs-lookup"><span data-stu-id="41864-102">#pragma checksum (C# Reference)</span></span>
<span data-ttu-id="41864-103">Génère des sommes de contrôle pour les fichiers sources afin de faciliter le débogage des pages [!INCLUDE[vstecasp](~/includes/vstecasp-md.md)].</span><span class="sxs-lookup"><span data-stu-id="41864-103">Generates checksums for source files to aid with debugging [!INCLUDE[vstecasp](~/includes/vstecasp-md.md)] pages.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="41864-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="41864-104">Syntax</span></span>  
  
```csharp
#pragma checksum "filename" "{guid}" "checksum bytes"  
```  
  
#### <a name="parameters"></a><span data-ttu-id="41864-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="41864-105">Parameters</span></span>  
 `"filename"`  
 <span data-ttu-id="41864-106">Nom du fichier dont les modifications ou les mises à jour doivent faire l’objet d’une surveillance.</span><span class="sxs-lookup"><span data-stu-id="41864-106">The name of the file that requires monitoring for changes or updates.</span></span>  
  
 `"{guid}"`  
 <span data-ttu-id="41864-107">Identificateur global unique (GUID) du fichier.</span><span class="sxs-lookup"><span data-stu-id="41864-107">The Globally Unique Identifier (GUID) for the file.</span></span>  
  
 `"checksum_bytes"`  
 <span data-ttu-id="41864-108">Chaîne de chiffres hexadécimaux représentant les octets de la somme de contrôle.</span><span class="sxs-lookup"><span data-stu-id="41864-108">The string of hexadecimal digits representing the bytes of the checksum.</span></span> <span data-ttu-id="41864-109">Doit être un nombre pair de chiffres hexadécimaux.</span><span class="sxs-lookup"><span data-stu-id="41864-109">Must be an even number of hexadecimal digits.</span></span> <span data-ttu-id="41864-110">S’il y a un nombre impair de chiffres, un avertissement est généré au moment de la compilation et la directive est ignorée.</span><span class="sxs-lookup"><span data-stu-id="41864-110">An odd number of digits results in a compile-time warning, and the directive are  ignored.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="41864-111">Notes</span><span class="sxs-lookup"><span data-stu-id="41864-111">Remarks</span></span>  
 <span data-ttu-id="41864-112">Le débogueur Visual Studio utilise une somme de contrôle pour s’assurer de toujours trouver la bonne source.</span><span class="sxs-lookup"><span data-stu-id="41864-112">The Visual Studio debugger uses a checksum to make sure  that it always finds the right source.</span></span> <span data-ttu-id="41864-113">Le compilateur calcule la somme de contrôle pour un fichier source, puis envoie la sortie vers le fichier de base de données du programme (PDB).</span><span class="sxs-lookup"><span data-stu-id="41864-113">The compiler computes the checksum for a source file, and then emits the output to the program database (PDB) file.</span></span> <span data-ttu-id="41864-114">Le débogueur utilise ensuite le fichier PDB à comparer avec la somme de contrôle qu’il calcule pour le fichier source.</span><span class="sxs-lookup"><span data-stu-id="41864-114">The debugger then uses the PDB to compare against the checksum that it computes for the source file.</span></span>  
  
 <span data-ttu-id="41864-115">Cette solution n’est pas possible pour les projets [!INCLUDE[vstecasp](~/includes/vstecasp-md.md)], car la somme de contrôle est calculée pour le fichier source généré, au lieu du fichier .aspx.</span><span class="sxs-lookup"><span data-stu-id="41864-115">This solution does not work for [!INCLUDE[vstecasp](~/includes/vstecasp-md.md)] projects, because the computed checksum is for the generated source file, rather than the .aspx file.</span></span> <span data-ttu-id="41864-116">Pour résoudre ce problème, `#pragma checksum` fournit une prise en charge de la somme de contrôle pour les pages [!INCLUDE[vstecasp](~/includes/vstecasp-md.md)].</span><span class="sxs-lookup"><span data-stu-id="41864-116">To address this problem, `#pragma checksum` provides checksum support for [!INCLUDE[vstecasp](~/includes/vstecasp-md.md)] pages.</span></span>  
  
 <span data-ttu-id="41864-117">Quand vous créez un projet [!INCLUDE[vstecasp](~/includes/vstecasp-md.md)] dans [!INCLUDE[csprcs](~/includes/csprcs-md.md)], le fichier source généré contient une somme de contrôle pour le fichier .aspx, à partir duquel la source est générée.</span><span class="sxs-lookup"><span data-stu-id="41864-117">When you create an [!INCLUDE[vstecasp](~/includes/vstecasp-md.md)] project in [!INCLUDE[csprcs](~/includes/csprcs-md.md)], the generated source file contains a checksum for the .aspx file, from which the source is generated.</span></span> <span data-ttu-id="41864-118">Le compilateur écrit ensuite ces informations dans le fichier PDB.</span><span class="sxs-lookup"><span data-stu-id="41864-118">The compiler then writes this information into the PDB file.</span></span>  
  
 <span data-ttu-id="41864-119">Si le compilateur ne rencontre aucune directive `#pragma checksum` dans le fichier, il calcule la somme de contrôle et écrit la valeur dans le fichier PDB.</span><span class="sxs-lookup"><span data-stu-id="41864-119">If the compiler encounters no `#pragma checksum` directive in the file, it computes the checksum and writes the value to the PDB file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="41864-120">Exemple</span><span class="sxs-lookup"><span data-stu-id="41864-120">Example</span></span>  
  
```csharp
class TestClass  
{  
    static int Main()  
    {  
        #pragma checksum "file.cs" "{3673e4ca-6098-4ec1-890f-8fceb2a794a2}" "{012345678AB}" // New checksum  
    }  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="41864-121">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="41864-121">See Also</span></span>  
 <span data-ttu-id="41864-122">[Informations de référence sur C#](../../../csharp/language-reference/index.md) </span><span class="sxs-lookup"><span data-stu-id="41864-122">[C# Reference](../../../csharp/language-reference/index.md) </span></span>  
 <span data-ttu-id="41864-123">[Guide de programmation C#](../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="41864-123">[C# Programming Guide](../../../csharp/programming-guide/index.md) </span></span>  
 [<span data-ttu-id="41864-124">Directives de préprocesseur C#</span><span class="sxs-lookup"><span data-stu-id="41864-124">C# Preprocessor Directives</span></span>](../../../csharp/language-reference/preprocessor-directives/index.md)

