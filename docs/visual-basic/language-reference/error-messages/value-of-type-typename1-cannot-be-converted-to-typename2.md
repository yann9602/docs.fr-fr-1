---
title: "Valeur de type &quot;&lt;NomType1&gt;« ne peut pas être converti en »&lt;NomType2&gt;&quot; | Documents Microsoft"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vbc30955
- bc30955
dev_langs:
- VB
helpviewer_keywords:
- BC30955
ms.assetid: 966b61eb-441e-48b0-bedf-ca95384ecb8b
caps.latest.revision: 12
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
ms.openlocfilehash: 2fbe1550515d2b15a3e349392fc8d78812787ae4
ms.contentlocale: fr-fr
ms.lasthandoff: 04/12/2017

---
# <a name="value-of-type-39lttypename1gt39-cannot-be-converted-to-39lttypename2gt39"></a><span data-ttu-id="49f2f-102">Valeur de type '&lt;NomType1&gt;« ne peut pas être converti en »&lt;NomType2&gt;»</span><span class="sxs-lookup"><span data-stu-id="49f2f-102">Value of type &#39;&lt;typename1&gt;&#39; cannot be converted to &#39;&lt;typename2&gt;&#39;</span></span>
<span data-ttu-id="49f2f-103">Valeur de type '\<NomType1 >' ne peut pas être convertie en '\<NomType2 > ».</span><span class="sxs-lookup"><span data-stu-id="49f2f-103">Value of type '\<typename1>' cannot be converted to '\<typename2>'.</span></span> <span data-ttu-id="49f2f-104">Incompatibilité de type peut être dû à la combinaison d’une référence de fichier avec une référence de projet à l’assembly '\<assemblyname > ».</span><span class="sxs-lookup"><span data-stu-id="49f2f-104">Type mismatch could be due to the mixing of a file reference with a project reference to assembly '\<assemblyname>'.</span></span> <span data-ttu-id="49f2f-105">Essayez de remplacer la référence du fichier à '\<filepath >' projet '\<projectname1 >' avec une référence de projet à '\<projectname2 > ».</span><span class="sxs-lookup"><span data-stu-id="49f2f-105">Try replacing the file reference to '\<filepath>' in project '\<projectname1>' with a project reference to '\<projectname2>'.</span></span>  
  
 <span data-ttu-id="49f2f-106">Dans une situation où un projet crée une référence de projet et une référence de fichier, le compilateur ne peut pas garantir qu’un type peut être converti vers un autre.</span><span class="sxs-lookup"><span data-stu-id="49f2f-106">In a situation where a project makes both a project reference and a file reference, the compiler cannot guarantee that one type can be converted to another.</span></span>  
  
 <span data-ttu-id="49f2f-107">Le pseudo-code suivant illustre une situation qui peut générer cette erreur.</span><span class="sxs-lookup"><span data-stu-id="49f2f-107">The following pseudo-code illustrates a situation that can generate this error.</span></span>  
  
 `' ================ Visual Basic project P1 ================`  
  
 `'        P1 makes a PROJECT REFERENCE to project P2`  
  
 `'        and a FILE REFERENCE to project P3.`  
  
 `Public commonObject As P3.commonClass`  
  
 `commonObject = P2.getCommonClass()`  
  
 `' ================ Visual Basic project P2 ================`  
  
 `'        P2 makes a PROJECT REFERENCE to project P3`  
  
 `Public Function getCommonClass() As P3.commonClass`  
  
 `Return New P3.commonClass`  
  
 `End Function`  
  
 `' ================ Visual Basic project P3 ================`  
  
 `Public Class commonClass`  
  
 `End Class`  
  
 <span data-ttu-id="49f2f-108">Projet `P1` établit une référence de projet indirecte via le projet `P2` au projet `P3`, ainsi qu’une référence de fichier directe pour `P3`.</span><span class="sxs-lookup"><span data-stu-id="49f2f-108">Project `P1` makes an indirect project reference through project `P2` to project `P3`, and also a direct file reference to `P3`.</span></span> <span data-ttu-id="49f2f-109">La déclaration de `commonObject` utilise la référence de fichier pour `P3`, tandis que l’appel à `P2.getCommonClass` utilise la référence de projet `P3`.</span><span class="sxs-lookup"><span data-stu-id="49f2f-109">The declaration of `commonObject` uses the file reference to `P3`, while the call to `P2.getCommonClass` uses the project reference to `P3`.</span></span>  
  
 <span data-ttu-id="49f2f-110">Le problème dans ce cas est que la référence de fichier Spécifie un chemin d’accès et le nom du fichier de sortie de `P3` (en général, p3.dll), alors que les références de projet identifient le projet source (`P3`) par le nom du projet.</span><span class="sxs-lookup"><span data-stu-id="49f2f-110">The problem in this situation is that the file reference specifies a file path and name for the output file of `P3` (typically p3.dll), while the project references identify the source project (`P3`) by project name.</span></span> <span data-ttu-id="49f2f-111">Pour cette raison, le compilateur ne peut pas garantir que le type `P3.commonClass` proviennent du même code source, les deux références différentes.</span><span class="sxs-lookup"><span data-stu-id="49f2f-111">Because of this, the compiler cannot guarantee that the type `P3.commonClass` comes from the same source code through the two different references.</span></span>  
  
 <span data-ttu-id="49f2f-112">Cette situation se produit généralement lorsque les références de projet et les références de fichiers sont mélangées.</span><span class="sxs-lookup"><span data-stu-id="49f2f-112">This situation typically occurs when project references and file references are mixed.</span></span> <span data-ttu-id="49f2f-113">Dans l’illustration précédente, le problème se produirait pas si `P1` crée une référence de projet directe pour `P3` au lieu d’une référence de fichier.</span><span class="sxs-lookup"><span data-stu-id="49f2f-113">In the preceding illustration, the problem would not occur if `P1` made a direct project reference to `P3` instead of a file reference.</span></span>  
  
 <span data-ttu-id="49f2f-114">**ID d’erreur :** BC30955</span><span class="sxs-lookup"><span data-stu-id="49f2f-114">**Error ID:** BC30955</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="49f2f-115">Pour corriger cette erreur</span><span class="sxs-lookup"><span data-stu-id="49f2f-115">To correct this error</span></span>  
  
-   <span data-ttu-id="49f2f-116">Modifiez la référence de fichier pour une référence de projet.</span><span class="sxs-lookup"><span data-stu-id="49f2f-116">Change the file reference to a project reference.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="49f2f-117">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="49f2f-117">See Also</span></span>  
 <span data-ttu-id="49f2f-118">[Conversions de type dans Visual Basic](../../../visual-basic/programming-guide/language-features/data-types/type-conversions.md) </span><span class="sxs-lookup"><span data-stu-id="49f2f-118">[Type Conversions in Visual Basic](../../../visual-basic/programming-guide/language-features/data-types/type-conversions.md) </span></span>  
<span data-ttu-id="49f2f-119"> [Gestion des références dans un projet](https://docs.microsoft.com/visualstudio/ide/managing-references-in-a-project) </span><span class="sxs-lookup"><span data-stu-id="49f2f-119"> [Managing references in a project](https://docs.microsoft.com/visualstudio/ide/managing-references-in-a-project) </span></span>  
<span data-ttu-id="49f2f-120"> [NIB Comment : ajouter ou supprimer des références à l’aide de la boîte de dialogue Ajouter une référence](http://msdn.microsoft.com/en-us/3bd75d61-f00c-47c0-86a2-dd1f20e231c9)</span><span class="sxs-lookup"><span data-stu-id="49f2f-120"> [NIB How to: Add or Remove References By Using the Add Reference Dialog Box](http://msdn.microsoft.com/en-us/3bd75d61-f00c-47c0-86a2-dd1f20e231c9)</span></span>
